# Getting started

Using Sheetbase to build a website/app.

## Starting

You can use Sheetbase platform to build a REST API only or a fully functional application.

### Build a website/app

Using the CLI, install [@sheetbase/cli](https://github.com/sheetbase/cli) and start a project:

```sh
$ npm install -g @sheetbase/cli
$ sheetbase start <project_name>
```

Or manually, clone a theme from the themes list: <https://sheetbase.net/themes>

### Build a REST API server

Clone blank backend app: <https://github.com/sheetbase/blank-server-app>

## Workflow

The [Sheetbase CLI](https://github.com/sheetbase/cli) provides convenient commands for easyly build and deploy a Sheetbase project.

### At the backend (server)

For a theme, backend code lives in **backend/** folder.

- Test: $ `sheetbase backend test`
- Build: $ `sheetbase backend build`
- Push code to server: $ `sheetbase backend push`
- Deploy: $ `sheetbase backend deploy`

### At the frontend (client)

For a theme, frontend code lives in **frontend/** folder.

- Test: $ `sheetbase frontend test`
- E2E: $ `sheetbase frontend e2e`
- Build: $ `sheetbase frontend build`
- Prerender content: $ `sheetbase frontend prerender`
- SEO optimization: $ `sheetbase frontend seo`
- Deploy: $ `sheetbase frontend deploy`