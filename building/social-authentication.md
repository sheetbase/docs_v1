# Social authentication

Need more setup to allow user login using Google and Facebook.

Open a route to `/__/auth/handler` in your app that handle the oauth result:

```ts
if (window.opener !== null && !window.opener.closed) {
  // process result
  window.opener.handleOauthResult(window.location.hash);
}
// close popup
window.close();
```
