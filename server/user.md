# User Server

Sheetbase user management.

Git repo: <https://github.com/sheetbase/user-server/>

## Getting started

Install: `npm install --save @sheetbase/user`

Usage:

```ts
import { auth } from '@sheetbase/user';

const Auth = auth({ /* configs */ });

```

## Configs

Sheetbase auth configs

### databaseDriver

Database driver for auth module, for now only driver support is [@sheetbase/sheets](https://github.com/sheetbase/sheets).

```ts
import { sheets } from '@sheetbase/sheets';
import { auth, sheetsDriver } from '@sheetbase/user';

// Sheets instance
const Sheets = sheets({ /* configs */ });

const Auth = auth({
  databaseDriver: sheetsDriver(Sheets.toAdmin()),
  /* other configs */
});
```

### encryptionSecret

Secret key for signing token.

### emailPrefix

App name or any prefix for using when sending OOB emails.

### authUrl

Custom url for handling oob actions, a string or a builder that recieves a mode and a code then returns the url.

```ts
type AuthUrl = string | ((mode: string, oobCode: string) => string);
```

```ts
// auth url with the apiKey
{
authUrl: (mode, oobCode) => ScriptApp.getService().getUrl() +
        '?e=auth/action&' +
        `mode=${mode}&oobCode=${oobCode}&`
        `apiKey=${apiKey}`,
}
```

### emailSubject

Email subject builder.

```ts
type EmailSubject = (mode: string) => string;
```

### emailBody

Email body builder.

```ts
type EmailBody = (mode: string, url: string, userData: UserData) => string;
```

## Account

Account related actions.

- `user`: create a user instance from data
- `getUser`: get a user
- `isUser`: check if a user exists
- `getUserByEmailAndPassword`: get user by email & password
- `getUserByCustomToken`: by custom token
- `getUserAnonymously`: anomymously
- `getUserByIdToken`: id token
- `getUserByOobCode`: oob code
- `getUserByRefreshToken`: refresh token
- `getUserByOauthProvider`: oauth provider
- `getPublicUsers`: public users
- `isValidPassword`: check if password is valid

## User

The user object.

- `getData`
- `getInfo`
- `getIdToken`
- `comparePassword`
- `getProvider`
- `getProfile`
- `getPublicProfile`
- `updateProfile`
- `setAdditionalData`
- `setSettings`
- `setProfilePublicly`
- `setProfilePrivately`
- `updateClaims`
- `setlastLogin`
- `setEmail`
- `confirmEmail`
- `setPassword`
- `setUsername`
- `setPhoneNumber`
- `setOob`
- `setRefreshToken`
- `delete`
- `save`

## Middlewares

- `Auth.IdTokenMiddleware`
- `Auth.UserMiddleware`

## Routes

To add routes to your app, see options [AddonRoutesOptions](https://github.com/sheetbase/server/blob/eb221ec3034d6b53abe11bc1942e1920c8f8d81f/src/lib/types.ts#L71):

```ts
Auth.registerRoutes(options?: AddonRoutesOptions);
```
