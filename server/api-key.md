# API Key Server

Sheetbase middleware to authorize with the API Key.

Git repo: <https://github.com/sheetbase/api-key/>

## Getting started

Install: `npm install --save @sheetbase/api-key`

Usage:

```ts
import { middleware as apiKeyMiddleware } from '@sheetbase/api-key';

const ApiKeyMiddleware = apiKeyMiddleware({ key: 'xxx' });

router.get('/', ApiKeyMiddleware, (req, res) => {
  return res.send('Aye!');
});

```

## Configs

### key

- Type: `string`

A single key.

### apiKeys

- Type: `{[key: string]: string | APIKey}`

Multiple api keys for multiple clients.

```ts
interface APIKey {
    value?: string;
    id?: string;
    title?: string;
    description?: string;
    createdAt?: string | number;
    [k: string]: any;
}
```

### failure

- Type: `(req: RouteRequest, res: RouteResponse) => any` (Sheetbase route handler)

Custom handler if not passed, default showing an unauthorized message.

```ts
{
  failure: (req, res) => res.json({ hey: 'Go away!' })
}
```

### trigger

- Type: `(req: RouteRequest, apiKey: APIKey) => void`

Trigger when the middileware is call, useful for logging multiple API keys usage.

```ts
{
  trigger: (req, apiKey) => {
    return console.log('A client access using this API Key:', apiKey);
  }
}
```