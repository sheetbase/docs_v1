# Publishing a Progressive Web App

Because Sheetbase frontend apps are built with web technologies, they can run just as well as a Progressive Web App as they can a native app. Not sure what PWAs are? Check out Ionic's [PWA Overview](https://ionicframework.com/pwa) for more info.

This guide is for frontend apps that based on Angular + Ionic, officially available from [Ionic Docs](https://ionicframework.com/docs/publishing/progressive-web-app).

## Making an App a PWA

The two main requirements of a PWA are a [Service Worker](https://developers.google.com/web/fundamentals/primers/service-workers/) and a [Web Manifest](https://developers.google.com/web/fundamentals/web-app-manifest/). While it's possible to add both of these to an app manually, the Angular team has an `@angular/pwa` package that can be used to automate this.

The `@angular/pwa` package will automatically add a service worker and a app manifest to the app. To add this package to the app run:

```sh
$ ng add @angular/pwa
```

Once this package has been added run `npm run build` inside the `frontend/` folder and the `www` directory will be ready to deploy as a PWA.

By default, the `@angular/pwa` package comes with Angular logo for the app icons. Be sure to update the manifest to use the correct app name and also replace the icons.

If an app is being deployed to other channels such as Cordova or Electron, you can remove the `"serviceWorker": true` flag from the `angular.json` file

Note: Features like Service Workers and many JavaScript APIs (such as geolocation) require the app be hosted in a secure context. When deploying an app through a hosting service, be aware they HTTPS will be required to take full advantage of Service Workers.