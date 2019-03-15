# Backend

Run backend related commands.

## Options

- `subCommand`: Optional supported sub-commands.

## Sub-commands

### `build`

Build backend distribution package.

- `sheetbase backend build`

### `push`

Push backend code to GAS server.

- `sheetbase backend push` // push backend code

### `deploy`

Deploy new version of the backend.

- `sheetbase backend deploy` // push and update the web app

### `install|i`, `uninstall|un`, `run`

Install or uninstall backend dependencies.

Run a backend script.

- `sheetbase backend install` // install dependencies
- `sheetbase backend run xxx` // run backend xxx script

### `*`

Run a command in backend folder.

- `sheetbase backend xxx` // equal `cd backend && xxx`