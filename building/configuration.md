# Config the project

Main configuration file is `sheetbase.json`. You can config your project by edit this file.

The `configs` field is for app configuration, after changing the value you need to run `$ sheetbase config update` to update config files in the backend and frontend folders. Or set values by running `$ sheetbase config set key=value`, this is the recommended way to set app configs.

```sh
$ sheetbase config set key=value
```

## `driveFolder`

Project Drive folder, this value was created and set automatically when starting a project using the Sheetbase CLI `$ sheetbase start ...`

You should NOT change this value. To quickly view this folder in your Google Drive, run `$ sheetbase url -o drive`.

## `configs`

All backend and frontend app configs comes here.

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

Use to tells the CLI if a config value belong to the backend, or a frontend when set value using `$ sheetbase config set key=value`.

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

When running `$ sheetbase setup`, there are custom app config values can be created and set automatically. See alist of built-in hooks: <https://github.com/sheetbase/cli/blob/master/src/hooks/index.ts>

```ts
{
    // [config_key: string]: [description: string, hookName: string, ... hook_args: []]

    key: ['My secret key', 'randomStr']
}
```

## `deployment`

Deployment configs for easilly deploy frontend app with the Sheetbase CLI. For now, it supports deploying to **Github Pages**, later supported for Firebase, shared hosting, server, ...

```ts
{
    provider: 'github',
    url: 'https://<org>.github.io/<repo>', // app domain
    srcDir: '', // path to 'src' folder, default: ./frontend/src
    wwwDir: '', // path to 'www' folder, default: ./frontend/www
    stagingDir: '', // custom staging folder, default: ~/sheetbase_staging/<project_name>
    destination: {
        gitUrl: 'https://github.com/<org>/<repo>.git', // git url
        master: true, // use master branch
        changeBase: true, // change base tag from '/' to github url
    }
}
```

## `prerender`

Configs for local prerender resources, used by `$ sheetbase frontend prerender` and `$ sheetbase frontend seo`.

```ts
{
    // [table: string]: SheetbasePrerender,
    // see SheetbasePrerender interface: https://github.com/sheetbase/cli/blob/44d04d8f682d308cc8de816016b5198a57a7d567/src/services/project.ts#L31

    foo: {
        location: 'my-foo',
        keyField: 'slug',
        rewriteFields: { title: 'name' },
    }
}
```