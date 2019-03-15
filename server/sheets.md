# Sheets Server

Using Google Sheets as a database.

Git repo: <https://github.com/sheetbase/sheets-server/>

## Getting started

Install: `npm install --save @sheetbase/sheets-server`

Usage:

```ts
import { sheets } from "@sheetbase/sheets-server";

const Sheets = sheets(
  /* configs */ {
    databaseId: "Abc...xyz"
  }
);

const foo = Sheets.all("foo"); // => [{}, {}, {}, ...]
```

## Configs

### databaseId

- Type: `string`

The spreadsheet id works as the database.

### keyFields

- Type: `{ [sheetName: string]: string }`
- Default: `key` field

Key fields of tables.

```ts
keyFields: {
  foo: 'slug', // use the value of the 'slug' field as the key
  bar: 'xxx' // use the value of the 'xxx' field as the key
}
```

### security

- Type: `boolean` | `Object`
- Default: `{}`

Security rules for checking against the request:

- `true` or `{}` = **private**, no read/write access anywhere
- `false` = **public**, read/write to any sheet/table
- `Object` = rule based access

```ts
security: {
  foo: { '.read': true, '.write': true }, // read/write
  bar: { '.read': true } // read only
  baz: { '.write': true } // write only
  bax: {
    $uid: {
      '.read': '!!auth && auth.uid == $uid' // only authorize user can read
    }
  }
}
```

### AuthToken

- Type: `Class`
- Default: `null`

User management token class to decode auth token.

```ts
// import and create user instance (Auth)

Sheets.setIntegration("AuthToken", Auth.Token);
```

## Sheets

CRUD interface for Sheetbase backend accessing Google Sheets.

- `setIntegration`: integrate with orther modules (Auth, ...).
- `extend`: create new Sheets instance from this instance.
- `toAdmin`: create an admin instance from this instance.
- `registerRoutes`: expose database routes.
- `ref`: create a data service for a location.
- `key`: generate an unique key.
- `all`: get all items of a sheet/table.
- `query`: query a sheet/table.
- `item`: get an item of a sheet/table.
- `add`: add an item.
- `update`: update a item of a sheet/table.
- `remove`: delete an item.

### setIntegration

Integrate Sheets module with orther modules (Auth, ...)

```ts
// import and create user instance (Auth)
// const Auth = auth({ ... });

// integrate Token class to the Sheets instacce
Sheets.setIntegration("AuthToken", Auth.Token);

// then we may use `auth ` object in security rule
// { '.read': '!!auth && auth.uid == $uid' }
```

### extend

Create new Sheets instance from this instance.

```ts
const SheetsAdmin = Sheets.extend({
  security: false // turn off security for this instance
});
```

### toAdmin

Create an admin instance from this instance.

```ts
const SheetsAdmin = Sheets.toAdmin(); // will pass all security, security = false
```

### registerRoutes

Expose database routes.

```ts
Sheets.registerRoutes({
  router: Sheetbase.Router, // Sheetbase router
  middlewares: [], // list of middlewares, [] = no middlewares
  disabledRoutes: [] // list of disabled routes, [] = no disabled
});
```

### ref

Create a data service for a location. Data service interface: <https://github.com/sheetbase/sheets-server/blob/master/src/lib/data.ts>

```ts
const fooRef = Sheets.ref("/foo");

const foo1Ref = fooRef.child("foo-1"); // create a ref to '/foo/foo-1'
foo1Ref.parent(); // create a ref to '/foo'
const rootRef = fooRef.root(); // create a ref to '/'

fooRef.key(); // generate an unique id: -Abc...xyz

fooRef.toObject(); // retrieve data as an object
fooRef.toArray(); // retrieve data as an array

foo1Ref.update({ title: "Foo 1" }); // create foo-1 if not exists
foo1Ref.update({ title: "Foo 1 new title" }); // update foo-1 title if exists
foo1Ref.update(null); // delete foo-1
```

### key

Generate a Firebase-liked unique key.

```ts
const key = Sheets.key(); // -Abc...xyz
```

### all

Get all items of a sheet/table.

```ts
const foo = Sheets.all("foo"); // [{}, {}, {}, ...]
const bar = Sheets.ref("/bar").toObject(); // { item-1: {}, item-2: {}, item-3: {}, ... }
```

### query

Query a sheet/table.

```ts
// simple query, all item from 'foo' has field1 === 'xxx'
const foo = Sheets.query("foo", { where: "field1", equal: "xxx" });
// shorthand for where/equal, pass in an object, format: { where: equal }
const foo2 = Sheets.query("foo", { field1: "xxx" });

// advanced query, all item from 'bar' has content field include 'hello'
const bar = Sheets.query("bar", item => {
  return !!item.content && item.content.indexOf("hello") > -1;
});
```

List of simple query:

- `where`: (required) an item property to perform query on
- `equal`: (optional) must exists and equal to (===)
- `exists`: (optional) exists = `true`, not exists = `false`
- `contains`: (optional) must be a string and contains the phrase (for array, user `childExists`)
- `lt|lte|gt|gte`: (optional) less/greater than or equal
- `childExists`: (optional) exists = key name or a value, not exists = add `!` before key name.
- `childEqual`: (optional) object only, exists = `key=value`, not exists = `key!=value`, child must be exists and equal to (===)

```ts
// equal
// (title === 'Foo me')
Sheets.query("foo", { where: "title", equal: "Foo me" });

// exists
// (!!content)
Sheets.query("foo", { where: "content", exists: true });
// (!content)
Sheets.query("foo", { where: "content", exists: false });

// contains
// (title.indexOf('me') > -1)
Sheets.query("foo", { where: "title", contains: "me" });

// lt, lte, gt, gte
// (age < 18)
Sheets.query("foo", { where: "age", lt: 18 });
// (age >= 18)
Sheets.query("foo", { where: "age", gte: 18 });

// childExists
// (object, !!categories['cat-1'])
Sheets.query("foo", { where: "categories", childExists: "cat-1" });
// (object, !categories['cat-1'])
Sheets.query("foo", { where: "categories", childExists: "!cat-1" });
// (array, list.indexOf('abc') > -1)
Sheets.query("foo", { where: "list", childExists: "abc" });
// (array, list.indexOf('abc') < 0)
Sheets.query("foo", { where: "list", childExists: "!abc" });

// childEqual
// (categories['cat-1'] === 'Cat 1')
Sheets.query("foo", { where: "categories", childEqual: "cat-1=Cat 1" });
// (categories['cat-1'] !== 'Cat 1')
Sheets.query("foo", { where: "categories", childEqual: "cat-1!=Cat 1" });
```

### item

Get an item of a sheet/table.

```ts
// get item by its key
const foo1 = Sheets.item("foo", "foo-1"); // { ... }

// second argument also accept the query arg (like query above)
// if only one item returned then it the item we need
// but if there is no item or more than 1 item, then it returns NULL
// so choose another unique field for query arg
const foo2 = Sheets.item("foo", { field1: "xxx" });
```

### add

Add an item.

```ts
// add 'foo-x'
// { key: 'foo-x', title: 'Foo x' }
Sheets.add("foo", "foo-x", { title: "Foo x" });

// add a 'foo' with auto key
// { key: '-Abc...xyz', title: 'A foo' }
Sheets.add("foo", null, { title: "A foo" });
```

### update

Update a item of a sheet/table.

```ts
// update foo-x title
Sheets.update("foo", "foo-x", { title: "Foo x new title" });
```

### remove

Delete an item.

```ts
// delete 'foo-x'
Sheets.remove("foo", "foo-x");
```

## Routes

To add routes to your app, see options [AddonRoutesOptions](https://github.com/sheetbase/core-server/blob/eb221ec3034d6b53abe11bc1942e1920c8f8d81f/src/lib/types.ts#L71):

```ts
Sheets.registerRoutes(options?: AddonRoutesOptions);
```

### Default disabled

Disabled routes by default, to enable set `{ disabledRoutes: [] }` in `registerRoutes()`:

```ts
[
  "post:/database", // add/update/remove an item
  "put:/database" // add an item
  "patch:/database" // update an item
  "delete:/database" // remove an item
];
```

### Endpoints

#### GET `/database`

Get `all`, `query` or `item`. Route query string:

- `path`: sheet/table name and item key
- `sheet` or `table`: sheet/table name
- `key` or `id`: item key
- `where`, `equal`, ...: query condition

Get all item from 'foo':

- `sheet=foo`
- `table=foo`
- `path=/foo`

Get an item from 'foo':

- `sheet=foo&key=foo-1`
- `table=foo&id=foo-1`
- `path=/foo/foo-1`

Query from 'foo':

- `table=foo&where=abc&equal=xyz` (same for other query)

#### POST `/database`

Add/update/delete item. Route body:

- `path`: sheet/table name and item key
- `sheet` or `table`: sheet/table name
- `key` or `id`: item key
- `data`: item data

Add an item (PUT):

- `{ sheet: 'foo', key: 'foo-x', data: { ... } }`
- `{ table: 'foo', data: { ... } }` // auto generated key

Update an item (PATCH):

- `{ sheet: 'foo', key: 'foo-x', data: { ... } }`

Remove an item (DELETE):

- `{ sheet: 'foo', key: 'foo-x' }`

#### PUT `/database`

Add an item. Route body same as `POST`.

#### PATCH `/database`

Update an item. Route body same as `POST`.

#### DELETE `/database`

Remove an item. Route body same as `POST`, omit `data` field.

## Security

Sheets Server comes with a rule based security.

To by pass security, add `{ security: false }` in configs.

### Rule-based

Allow all read and write (public).

```ts
{
  '.read': true,
  '.write': true
}
```

The module borrow idea from Firebase Realtime Database, see <https://firebase.google.com/docs/database/security/quickstart#sample-rules>

### Rule objects

- `now`: current time
- `auth`: auth object
- `root`: data service for root
- `data`: data service for current location
- `newData`: data to be updated
- `$dynamic`: any dynamic data
