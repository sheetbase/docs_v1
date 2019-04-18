# Core Server

Sheetbase core module for backend app.

Git repo: <https://github.com/sheetbase/server/>

## Getting started

Install: `npm install --save @sheetbase/server`

Usage:

```ts
import { sheetbase } from '@sheetbase/server';

const Sheetbase = sheetbase({ /* configs */ });

Sheetbase.Router.get('/', (req, res) => {
  return res.send('Hello!');
});

```

## Configs

Sheetbase app configurations.

### allowMethodsWhenDoGet

- Type: `boolean`
- Default: `false`

Allows POST, PUT, ... when do GET method, useful for testing in browser without re-deploy the web app.

### views

- Type: `string`
- Default: `''`

Views folder, where to put view templating file. Examples: `views`, `public/views`

### disabledRoutes

- Type: `string[]`
- Default: `[]`

List of disabled routes, format: `method:endpoint`. Examples: `[ 'GET:/', 'POST:/me' ]`

### routingErrors

- Type: [RoutingErrors](https://github.com/sheetbase/server/blob/d15caa7d464e98057e94ca810d22d88881214310/src/lib/types.ts#L67)
- Default: `{}`

List of routing errors, by codes, when do `res.error(code)`, the router will show the coresponding error to the client.

Examples: `{ foo: 'The Foo error.' }`. Then: `res.error('foo')`, the result will be:

```json
{
  "error": true,
  "status": 400,
  "code": "foo",
  "message": "The Foo error."
}
```

## Routing

Sheetbase provide a routing system like [ExpressJS](https://expressjs.com).

The router supports these methods: `GET`, `POST`, `PUT`, `PATCH`, `DELETE`. But only `GET` and `POST` is real HTTP methods, others are just play as a way to organize the app.

`router.get('/', ...)`, accepts a GET request to `...?e=/`

`router.post('/', ...)`, accepts a POST request to `...?e=/`

`router.put('/', ...)`, accepts a POST request to `...?e=/&method=PUT`

`router.patch('/', ...)`, accepts a POST request to `...?e=/&method=PATCH`

`router.delete('/', ...)`, accepts a POST request to `...?e=/&method=DELETE`

`router.all('/', ...)`, accepts all request to `...?e=/`

### Basic use

```ts
router.get("/", (req, res) => {
  return res.send("Hello, world!");
});
```

### Request

```ts
{
  query: Object;
  params: Object; // same as query
  body: Object;
}
```

### Response

- `send`: return string as html or object as json.
- `html`: return html page.
- `json`: return json data.
- `render`: render html template, supports native GAS template, [Handlebars](https://handlebarsjs.com/) and [Ejs](https://ejs.co/).
- `success`: return json data in form of a [ResponseSuccess](https://github.com/sheetbase/server/blob/e6e1235f6b30635860bf3b3945b7fc09f715611b/src/lib/types.ts#L43).
- `error`: return json data in form of a [ResponseError](https://github.com/sheetbase/server/blob/e6e1235f6b30635860bf3b3945b7fc09f715611b/src/lib/types.ts#L32).

### Routing errors

Use `setErrors` to resgister your app routing errors. So that you can just do `res.error(code)` later.

```ts
// set errors
router.setErrors({
  error1: "Error 1",
  error2: { status: 500, message: "Error 2" }
});

// later, in a route
return res.error("error1");
```

### With middlewares

For a certain route.

```ts
const Middleware = (req, res, next) => {
  return next();
};

router.get("/", Middleware, (req, res) => {
  return res.send("Final!");
});
```

For all routes.

```ts
router.use((req, res, next) => {
  return next();
});
```

### Middleware data

Want to send data downstream.

```ts
return next({ foo: "bar" });
```

### Render HTML template

To render HTML template with [Handlebars](https://handlebarsjs.com/) or [Ejs](https://ejs.co/).

Place your template files with the coresponding extensions somewhere in the project, may be `views` folder. Remmber to set it in configs.

For Handlebars, file extension would be `.hbs.html`, for Ejs it is `ejs.html`;

Add the vendor js to your app, before main app code. With app-scripts, the build script would be `sheetbase-app-scripts build --vendor <path to js file>`