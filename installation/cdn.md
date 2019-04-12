# Sheetbase Packages

Depending on whether you're using Angular, another framework, or none at all, there are a few different ways to install Sheetbase.

## The Sheetbase Javascript client

A library for using Sheetbase with any Javascript framework or none of all.

```sh
npm install --save @sheetbase/client@latest
```

## Using Sheetbase in Angular

When using Sheetbase in an Angular project, install the latest @sheetbase/angular package from npm. This comes with all of the Sheetbase components and Angular specific services and features.

```sh
npm install --save @sheetbase/angular@latest
```

Each time there is a new Sheetbase release, the version will increment. The version can be updated using npm, as well.

## Using Sheetbase from a CDN

Sheetbase can also be included from a CDN by adding a script tag!

It's recommended to use unpkg to access the library from a CDN. To get the latest version, add the following `<script>` tag inside the `<head></head>` element in an HTML file:

```html
<script src="https://unpkg.com/@sheetbase/client@latest/dist/sheetbase.min.js"></script>
```

With this it's possible to use all of the Sheetbase components without having to install anything.

This does not install Angular or any frameworks. This allows use of Sheetbase client without a framework.