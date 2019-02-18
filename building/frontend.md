# Build the frontend

## Developing

Develop the frontend app according to the frontend framework: Angular, Vue, React, ...

## Generate the distribution package

Sheetbase CLI provides a `build` command for building the project distribution package. To build the frontend.

```sh
$ sheetbase frontend build
```

## Optional frontend building

Pre-render content.

```sh
$ sheetbase frontend prerender
```

Generate sitemap.xml and robots.txt

```sh
$ sheetbase frontend seo
```

## The `build` command

You can run all the command above with one command.

```sh
$ sheetbase build --frontend
```