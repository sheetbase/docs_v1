# Config

Config the project. Proxy of **project config**

Sub-commands: list|ls, update|set, import|im, export|ex

## Options

- `subCommand`: Optional supported sub-commands, default: **list**.
- `params`: Command params, comma-separated.

## Sub-commands

### `list|ls`

List project configs.

- `sheetbase config list` // list all configs

### `update|set`

Set or update project configs.

- `sheetbase config update` // rebuild configs from sheetbase.json
- `sheetbase config set key=value|...` // set configs

### `import|im`

Import project configs.

- `sheetbase config import xxx.json` // import configs from xxx.json

### `export|ex`

Export project configs.

- `sheetbase config export` // export configs to exports/... .json
- `sheetbase config export xxx.json` // export configs to xxx.json