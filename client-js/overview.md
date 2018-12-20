# Javascript Client

Sheetbase client for Javascript provide easy APIs for accessing Sheetbase server app.

## Install

- TS/ES2015: `npm install @sheetbase/client`

- From CDN: [https://unpkg.com/@sheetbase/client@0.0.2/dist/sheetbase.js](https://unpkg.com/@sheetbase/client@0.0.2/dist/sheetbase.js)

## Usage

```ts
import * as sheetbase from '@sheetbase/client';

const app = sheetbase.initializeApp({
    backendUrl: '...',
});

const result = await app.api().get('/');

```

### Options

- `backendUrl`: The backend url.
- `apiKey` (optional): Built-in API authorization.

## Parts

### `app.api()`

Send request to the Sheetbase server.

Server module: [https://github.com/sheetbase/core-server](https://github.com/sheetbase/core-server)

### `app.database()`

Client for server database.

Server module: [https://github.com/sheetbase/sheets-server](https://github.com/sheetbase/sheets-server)

### `app.storage()`

Client for server storage.

Server module: [https://github.com/sheetbase/drive-server](https://github.com/sheetbase/drive-server)

### `app.mail()`

Client for server mail.

Server module: [https://github.com/sheetbase/gmail-server](https://github.com/sheetbase/gmail-server)

### `app.auth()`

Client for server auth.

Server module: [https://github.com/sheetbase/user-password-server](https://github.com/sheetbase/user-password-server)

## Api reference

See: [https://sheetbase.github.io/client/api/](https://sheetbase.github.io/client/api/)