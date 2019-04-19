# Gmail Server

Send email using Gmail in Sheetbase backend app.

Git repo: <https://github.com/sheetbase/gmail/>

## Getting started

Install: `npm install --save @sheetbase/gmail`

Usage:

```ts
import { gmail } from "@sheetbase/gmail";

const Gmail = gmail(
  /* options */ {
    prefix: "MyApp"
  }
);

const { threadId } = Gmail.send({
  recipient: "xxx@xxx.xxx"
});
```

## Configs

### forwarding

- Type: `string`
- Default: current account email.

Manage email from different account.

### prefix

- Type: `string`
- Default: `Sheetbase`.

For better management, all email subject will be prefix with a string and labeled `prefix:category`.

### categories

- Type: `object`
- Default: an uncategoriezed category: `{ uncategorized: { title: 'Uncategorized', silent: true } }`.

List of support categories, all email will be sorted to one of these categories.

```ts
{
  categories: {
    message: 'Messages',
    misc: {
      title: 'Misc',
      silent: true
    }
  }
}
```

### templates

- Type: `object`
- Default: `{}`.

List of supported templates.

```ts
{
  templates: {
    hello: (data: any) => `Hello ${data.name}!`,
  }
}
```

## Gmail

Interface for sending email.

- `quota`: view remaining daily quota.
- `send`: send email.

### quota

View remaining daily quota.

```ts
const { remainingDailyQuota } = Gmail.quota();
```

### send

Send email.

```ts
// To: xxx@xxx.xxx
// Subject: Send me email
// Content: Hello world!
// Label: <prefix>:Uncategorized
const { threadId } = Gmail.send({
  recipient: "xxx@xxx.xxx",
  subject: "Send me email",
  options: {
    htmlBody: `<p>Hello world!</p>`
  }
});

// To: ...
// Subject: ...
// Content: ...
// Label: <prefix>:Messages
Gmail.send(
  {
    /* ... */
  },
  "message"
);

// To: ...
// Subject: ...
// Content: Hello John!
// Label: ...
Gmail.send(
  {
    recipient: "xxx@xxx.xxx",
    subject: "Send me email"
  },
  "message",
  {
    hello: { name: "John" }
  }
);

// force silent = false
Gmail.send(
  {
    /* ... */
  },
  null,
  null,
  false
);
```

## Routes

To add routes to your app, see options [AddonRoutesOptions](https://github.com/sheetbase/server/blob/eb221ec3034d6b53abe11bc1942e1920c8f8d81f/src/lib/types.ts#L71):

```ts
Gmail.registerRoutes(options?: AddonRoutesOptions);
```

### Default disabled

Disabled routes by default, to enable set `{ disabledRoutes: [] }` in `registerRoutes()`:

```ts
[
  "post:/mail" // send email
];
```

### Endpoints

#### GET `/mail`

Get `quota`.

#### POST `/mail`

Send email. Route body:

- `mailingData`: mail data
- `category`: category name
- `template`: template config
- `silent`: override category silent

Send an email:

```ts
{
  mailingData: {
    recipient: 'xxx@xxx.xxx',
    subject: 'Send me email',
    options: {
      htmlBody: `<p>Hello world!</p>`,
    }
  }
}
```

With category:

```ts
{
  mailingData: { /*  */ },
  category: 'message'
}
```

With template:

```ts
{
  mailingData: { /*  */ },
  template: {
    hello: { name: 'John' }
  }
}
```

Override category silent:

```ts
{
  mailingData: { /*  */ },
  silent: false,
}
```
