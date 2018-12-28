# Build Sheetbase Theme

A Sheetbase theme (website/app) is a combination of Sheetbase server app and a client app.

## Structure

- `backend/`: Backend app code.
- `frontend/`: Frontend app code.
- `sheetbase.json`: Sheetbase config file.

## Workflow

### Backend

- Test: $ `sheetbase backend test`
- Build: $ `sheetbase backend build`
- Push code to server: $ `sheetbase backend push`
- Deploy: $ `sheetbase backend deploy`

### Frontend

- Test: $ `sheetbase frontend test`
- E2E: $ `sheetbase frontend e2e`
- Build: $ `sheetbase frontend build`

## Sample themes

- Blank Angular: <https://github.com/sheetbase-themes/blank-angular>
- Basic Angular: <https://github.com/sheetbase-themes/basic-angular>
- Simpleblog Angular: <https://github.com/sheetbase-themes/simpleblog-angular>