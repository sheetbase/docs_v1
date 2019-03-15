# Config the project

Main configuration file is `sheetbase.json`. You can config your project by edit this file.

The `configs` field is for app configuration, after changing the value you need to run `$ sheetbase config update` to update config files in the backend and frontend folders. Or set values by running `$ sheetbase config set key=value`, this is the recommended way to set app configs.

```sh
$ sheetbase config set key=value
```

There may be a frontend app config file, for Angular apps, it located in `frontend/src/app/app.config.ts`. We not include this config file to `sheetbase.json` in case you want to reuse the frontend with different backend stack but not Sheetbase backend.

## `driveFolder`

Project Drive folder, this value was created and set automatically when starting a project using the Sheetbase CLI `$ sheetbase start ...`

You should NOT change this value. To quickly view this folder in your Google Drive, run `$ sheetbase url -o drive`.

## `configs`

All Sheetbase related backend and frontend app configs comes here.

```ts
{
    backend: {
        // [key: string]: any,
    },
    frontend: {
        // [key: string]: any,
    },
}
```

## `configMaps`

Use to tells the CLI if a config value belong to the backend or the frontend, when set value using `$ sheetbase config set key=value`.

```ts
{
    backend: [], // string[]
    frontend: [], // string[]
}
```

## `urlMaps`

This tells the CLI how to display and open project urls correctlly when running `$ sheetbase urls` and `$ sheetbase url -o ...`.

```ts
{
    // [config_key: string]: [name: string, url_prefix: string, url_suffix: string]

    any: ['foo', 'https://foo.com?id=']
}
```

## `setupHooks`

When running `$ sheetbase setup`, there are custom theme config values can be created and set automatically. See a list of built-in hooks: <https://github.com/sheetbase/cli/blob/master/src/hooks/index.ts>

```ts
{
    // [config_key: string]: [description: string, hookName: string, ... hook_args: []]

    key: ['My secret key', 'randomStr']
}
```

## `deployment`

Deployment configs for easily deploy frontend app with the Sheetbase CLI. For now, it supports deploying to **Github Pages**, later supported for Firebase, shared hosting, server, ...

```ts
{
    provider: 'github',
    url: 'https://<org>.github.io/<repo>', // Github domain or custom domain
    srcDir: '', // path to 'src' folder, default: ./frontend/src
    wwwDir: '', // path to 'www' folder, default: ./frontend/www
    stagingDir: '', // custom staging folder, default: ~/sheetbase_staging/<project_name>
    destination: {
        gitUrl: 'https://github.com/<org>/<repo>.git', // github .git url
        // master: true, // use master branch else user gh-pages branch
    }
}
```

## Prerender

There are two files live in `frontend/src/`, the `prerender.json` for config prerendering and the `robots.txt` for SEO.

Prerendering config format:

```ts
// frontend/src/prerender.json
{
  "items": [ // list of string or config object
    'contact', // <url>/contact
    'page/abc', // .../page/abc
    // load all items from database
    // then prerender items
    {
      "from": "categories", // categories sheet
      "location": "category", // .../category/<category_key>
      // these value assist sitemap.xml generation
      "changefreq": "yearly",
      "priority": "0.3"
    },
    {
      "from": "posts",
      "location": "post", // .../post/<post_key>
      "changefreq": "daily",
      "priority": "1.0"
    }
  ],
  // include a loading screen
  // true = default loading screen
  "loading": /* true */ { // or custom
        "html": "<div class=\"loading-screen\">Loading ...</div>",
        "css": ".loading-screen{color:'red';}"
  },
}
```

`robots.txt` follows the standard format, <http://www.robotstxt.org/>.