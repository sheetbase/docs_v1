# Frontend

Run frontend related commands.

## Options

- `subCommand`: Optional supported sub-commands.

## Sub-commands

### `install|i` / `uninstall|un` / `run|*`

Install or uninstall frontend dependencies.

Run a frontend script.

- `sheetbase frontend install` // install deps
- `sheetbase frontend run build` // run frontend build script
- `sheetbase frontend build` // run frontend build script

### `*`

Run a command in frontend folder.

- `sheetbase frontend ng build` // equal `cd frontend && ng build`