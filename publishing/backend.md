# Deploy backend

## Build the distribution package

```sh
sheetbase build -b
```

## Deploy/update

Backend code is distributed to Google Apps Script server. Run this command to redeploy.

```sh
sheetbase deploy -b
```

## Google authorization

The backend app may require different [Google Oauth scopes](https://developers.google.com/identity/protocols/googlescopes) for accessing certain Google services. You must approve the process whenever changing scopes.

Note that, these permissions require by YOUR backend app and manage by you only, not anything related or managed by Sheetbase developers.

See scopes from Google Apps Script editor: `File > Project properties > (Scopes tab)`

To change scopes manually, see: <https://developers.google.com/apps-script/concepts/scopes>. Be aware, changing scopes may break your backend when no permission for running certain functions.

When the backend app requires more scopes, it will show an error message like: `Not authorized ...`. To authorize again, go to the Apps Script editor:

1. From `Publish`
2. Click `Deploy as webapp...`
3. Select the latest version from `Project version:`
4. Click `Update`
5. A permission review dialog show up, click `Review Permissions`
6. Follow [the Oauth process](https://developers.google.com/apps-script/guides/client-verification), feel free to ignore the **unverified app** error
7. May redeploy the backend: `sheetbase deploy -b`