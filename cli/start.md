# Start

Start a new project. Proxy of **project start**

## Options

- `projectName`: Name of the project, auto default.
- `resource`: Resource to create the project with, default to theme **blank_angular**.
- `-i,--install`: Install npm packages.
- `-m,--no-setup`: Do not run setup command.

## Examples

- `sheetbase start` // start a new theme project, with **blank-angular**
- `sheetbase start my_website` // start a new theme project in **my_website** folder
- `sheetbase start xxx basic-angular` // start a new theme project, with **basic-angular** theme
- `sheetbase start xxx <org/name>` // start a new theme project, from github repo
- `sheetbase start xxx url.zip` // start a project from .zip url
- `sheetbase start xxx url.git` // start a project from .git url
- `sheetbase start -i` // also install dependencies
- `sheetbase start --no-setup` // not run `setup` command