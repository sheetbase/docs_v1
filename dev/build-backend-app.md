# Build a backend app

Server app is a backend app that run on Google Apps Script server.

- Clone this repo: https://github.com/sheetbase/blank-server-app
- See readme for more info.

## Workflow

- Build: $ `npm run build`
- Test: $ `npm run test`
- Upload code to GAS: $ `npm run deploy`

## Structure

- `src/`: Main source.
- `tests/`: Test related resources.
- `.clasp.json, .claspignore`: @google/clasp config files.
- `appsscript.json`: Google apps script config file.
- `rollup.config.js`: Bundling tool config file.
  
## Build tool

Sheetbase backend module use [@sheetbase/app-scripts](https://github.com/sheetbase/app-scripts) to build final code that can push to Google Apps Script server for execution.

- Transpile Typescript code.
- Bundle transpiled code using Rollup.