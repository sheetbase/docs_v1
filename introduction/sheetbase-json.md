# Sheetbase.json

The Sheetbase project config file.

See sample config file: <https://github.com/sheetbase-themes/simpleblog-angular/blob/master/sheetbase.json>

```ts
{
    driveFolder: '', // project root folder id
    configs: {
        backend: {}, // backend app configs
        frontend: {}, // frontend app configs
    },
    configMaps: {
        backend: [], // list of backend config keys
        frontend: [], // list of frontend config keys
    },
    urlMaps: {
        // custom project urls mapping

        // [config_key: string]: [name: string, url_prefix: string, url_suffix: string]
    },
    setupHooks: {
        // built-in hooks: https://github.com/sheetbase/cli/blob/master/src/hooks/index.ts
        // list of `sheetbase setup` hooks

        // [config_key: string]: [description: string, hookName: string, ... hook_args: []]
    },
    models: [
        // built-in models
        // string
        // or
        // { from: string, name: string, gid: string | number, public: boolean }
    ],
    deployment: {
        // deployment configs
        provider: 'github', // deployment provider
        url: 'https://<org>.github.io/<repo>', // app domain
        // srcDir: '', // path to 'src' folder, default: ./frontend/src
        // wwwDir: '', // path to 'www' folder, default: ./frontend/www
        // stagingDir: '', // custom staging folder, default: ~/sheetbase_staging/<project_name>
        destination: {
            gitUrl: 'https://github.com/<org>/<repo>.git', // git url
            // master: true, // use master branch
        }
    }
}
```