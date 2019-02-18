# Sheetbase Packages

Depending on whether you're using Angular, another framework, or none at all, there are a few different ways to install Sheetbase.

## Using Sheetbase in Angular (developing)

When using Sheetbase in an Angular project, install the latest @sheetbase/angular package from npm. This comes with all of the Sheetbase components and Angular specific services and features.

`$ npm install @sheetbase/angular@latest --save`

Each time there is a new Sheetbase release, the version will increment. The version can be updated using npm, as well.

## Using Sheetbase from a CDN

Sheetbase can also be included from a CDN by adding a script tag!

It's recommended to use unpkg to access the library from a CDN. To get the latest version, add the following `<script>` tag inside the `<head></head>` element in an HTML file:

```html
<script src="https://unpkg.com/@sheetbase/client@latest/dist/sheetbase.js"></script>
```

With this it's possible to use all of the Sheetbase components without having to install anything.

This does not install Angular or any frameworks. This allows use of Ionic components without a framework.