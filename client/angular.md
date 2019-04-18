# Sheetbase Angular

Sheetbase Angular is a wrapper of [@sheetbase/client](https://github.com/sheetbase/client) for Angular apps.

See more: <https://github.com/sheetbase/angular>


## Getting started

Install: `npm install --save @sheetbase/client @sheetbase/angular`

```ts
import { initializeApp } from '@sheetbase/client/app';
import { SheetbaseService } from '@sheetbase/angular';

// create a Sheetbase app
const sheetbaseApp = initializeApp(/* options */);

// init the Sheetbase service
this.sheetbaseService.setApp(sheetbaseApp);

// using
const result = await this.sheetbaseService.api().get('/');
```

## Services

- `SheetbaseService`: wrapper of Sheetbase app
- `ApiService`: wrapper of app.api()
- `DatabaseService`: wrapper of app.database()
- `AuthService`: wrapper of app.auth()
- `MailService`: wrapper of app.mail()
- `StorageService`: wrapper of app.storage()
- `LocalstorageService`: wrapper of app.localstorage()
- `CacheService`: wrapper of app.cache()
- `FetchService`: wrapper of app.fetch()
- `AppService`: app stuffs
- `NavService`: navigation
- `DataService`: useful data methods
- `CurrencyService`: format and convert currency
- `DateService`: format date time

## Components

- `sheetbase-oauth-popup`: oauth popup handler
- `sheetbase-oops`: 404 component
- `sheetbase-skeleton`: skeleton component

## Pipes

- `filter`: simple filter
- `o2a`: turn object into array
- `safe`: safe html binding or url