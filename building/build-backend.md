# Build the backend

## Developing

Backend app can be develop similarly to develop a ExpressJS app, server modules help develop quickly, see Server section for more.

Develop your first REST API server using Sheetbase by reading [basic use of the Core server](https://medium.com/@sheetbase/sheetbase-starter-3-the-core-server-d6840bf04f6e), or see [sample](https://github.com/sheetbase-themes/basic-angular/tree/master/backend/src) backend code.

## Generate the distribution package

Sheetbase CLI provides a `build` command for building the project distribution package. To build the backend.

```sh
sheetbase backend build
```

You can build the backend by running the `build` command:

```sh
sheetbase build --backend
```

## Test backend

[Sheetbase Testing](https://github.com/sheetbase/testing) package is a tool for testing Sheetbase server routes.

Install: `npm install --save-dev @sheetbase/testing`

Test the backend with **mocha** and **chai**:

```ts
// import testing browser
import { Browser } from '@sheetbase/testing';

// import app instance
import * as App from '../src/index';

// init a browser instance for the app
const browser = new Browser(App);

// begin test
describe('Home routes', () => {

  it('GET /', () => {
    const { body } = browser.get('/');
    expect(body).to.contain('Sheetbase Backend');
  });

  it('POST /', () => {
    const { body } = browser.post('/');
    expect(body.data).to.eql({ title: 'Sheetbase Backend' });
  });

});
```

See more: <https://github.com/sheetbase/testing>