# Google

Manage Google accounts.

Sub-commands: list|ls, connect|add, disconnect|remove|rm, default.

`sheetbase google [subCommand] [params...] [options]`

## Options

- `subCommand`: Supported sub-commands.
- `params`: Command params, comma-separated.
- `-y,--yes`: (connect) Agree on account connection.
- `-c,--creds`: (connect) Save credential to .googlerc.json.
- `-f,--full`: (connect) Not recommended, grant full access to Drive.
- `-d,--default`: (list) Show default account only.

## Sub-commands

### `list|ls`

List connected accounts.

- `sheetbase google list` // see all accounts
- `sheetbase google ls -d` // see the default account only

### `connect|add`

Connect an account.

- `sheetbase google connect` // start an connection
- `sheetbase google connect -y` // do not ask
- `sheetbase google add --creds` // also save credential to the project

### `disconnect|remove|rm`

Diconnect a connected account.

- `sheetbase google disconnect <id>` // disconnect the account with the id
- `sheetbase google remove default` // disconnect the default account
- `sheetbase google rm local` // disconnect the local --creds account
- `sheetbase google rm all` // disconnect all accounts, excerpt local one

### `default`

Change or list the default account.

- `sheetbase google default` // see the default account
- `sheetbase google default <id>` // switch the default account