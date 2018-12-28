# Build a backend module

Server module for developing server app.

- Clone this repo: <https://github.com/sheetbase/blank-server-module>
- See readme for more info.

## Structure

- `src/`: Main source.
- `tests/`: Test related resources.
- `.clasp.json, .claspignore`: @google/clasp config files.
- `appsscript.json`: Google apps script config file.
- `rollup.config.js`: Bundling tool config file.
  
## Workflow

- Test: $ `npm run test`
- Build: $ `npm run build`
- Upload code to GAS: $ `cd deploy && clasp push`

## Build tool

Sheetbase backend module use [@sheetbase/app-scripts](https://github.com/sheetbase/app-scripts) to build final code that can push to Google Apps Script server for execution.

- Transpile Typescript code.
- Bundle transpiled code using Rollup.
- Generate README file.
- Generate API reference using Typedoc.