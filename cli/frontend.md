# Frontend

Run frontend related commands.

## Options

- `subCommand`: Optional supported sub-commands.

## Sub-commands

### `build`

Build frontend distribution package.

- `sheetbase frontend build`

### `deploy`

Deploy the frontend.

- `sheetbase frontend deploy`

### `install|i`, `uninstall|un`, `run`

Install or uninstall frontend dependencies.

Run a frontend script.

- `sheetbase frontend install` // install dependencies
- `sheetbase frontend run xxx` // run frontend xxx script

### `*`

Run a command in frontend folder.

- `sheetbase frontend xxx` // equal `cd frontend && xxx`