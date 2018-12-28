# Sheetbase.json

The Sheetbase theme config file.

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
        // custom project urls mapping, format:

        // <config_key>: [<name>, <url_prefix>, <url_suffix>]
    },
    setupHooks: {
        // built-in hooks: https://github.com/sheetbase/cli/blob/master/src/hooks/index.ts
        // list of $ `sheetbase setup` hooks, format:

        // <config_key>: [<description>, <hook>, ... <hook_args>]
    }
}
```