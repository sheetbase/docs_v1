# Frontend

Run frontend related commands.

## Options

- `subCommand`: Optional supported sub-commands.

## Sub-commands

### `build`

Build frontend distribution package.

- `sheetbase frontend build`

### `prerender`

Prerender the frontend.

- `sheetbase frontend prerender`
- `sheetbase frontend prerender --force *` // force prerender all
- `sheetbase frontend prerender -f category` // force prerender categories sheet as well as all routes contains "category"
- `sheetbase frontend prerender -f category,tag` // multiple force, separated by comma
- `sheetbase frontend prerender --only category` // prerender only categories sheet as well as all routes contains "category"
- `sheetbase frontend prerender -o category,tag` // multiple only, separated by comma

### `deploy`

Deploy the frontend.

- `sheetbase frontend deploy`
- `sheetbase frontend deploy -m "Git message"` // custom git commit message

### `install|i`, `uninstall|un`, `run`

Install or uninstall frontend dependencies.

Run a frontend script.

- `sheetbase frontend install` // install dependencies
- `sheetbase frontend run xxx` // run frontend xxx script

### `*`

Run a command in frontend folder.

- `sheetbase frontend xxx` // equal `cd frontend && xxx`