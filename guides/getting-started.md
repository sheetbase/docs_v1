# Getting started

Using Sheetbase to build a website/app.

## Build a website/app

### Using the CLI

- Install [@sheetbase/cli](https://github.com/sheetbase/cli) $: `npm install -g @sheetbase/cli`.
- Start a project $: `sheetbase start <project_name>`

### Manually

- Clone a theme, see themes list: <https://sheetbase.net/themes>

## Build a REST API server

- Clone blank backend app: <https://github.com/sheetbase/blank-server-app>

## Workflow

### Backend/server

For theme, backend code lives in **backend/** folder.

- Test: $ `sheetbase backend test`
- Build: $ `sheetbase backend build`
- Push code to server: $ `sheetbase backend push`
- Deploy: $ `sheetbase backend deploy`

### Frontend/client

For theme, frontend code lives in **frontend/** folder.

- Test: $ `sheetbase frontend test`
- E2E: $ `sheetbase frontend e2e`
- Build: $ `sheetbase frontend build`