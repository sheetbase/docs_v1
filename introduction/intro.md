# Introduction

Sheetbase is a platform that provide tools for developing modern websites and apps using free cloud services provided by Google.

It is free and fast for developer to build a product that do not carry heavy workload.

## Concept

A **Sheetbase project** (aka. a Sheetbase Theme/Website/App) contains the BACKEND part and the FRONTEND part, communicates via REST API.

![Sheetbase](https://sheetbase.dev/assets/images/explain.png "https://sheetbase.dev")

### At the server (backend)

The backend code runs in a cloud environment provides by [Google Apps Script](https://developers.google.com/apps-script/), which features come from a wide range of Google services: Google Sheets for **Database**, Drive for **Storage**, Gmail for **Mailing**, ... and other non-Google services by the external API.

### At the client (frontend)

The client side powered by modern Javascript technology and any system that is able to contact a REST API server.

## What news?

It's been some time since the [first introducing of Sheetbase](https://medium.com/@lamnhan/introducing-sheetbase-a-new-way-to-build-websites-and-apps-c6a6bccb6254), the feedback is great, so we decided to push the platform further by rebuilding mostly every parts of it, includes:

- Using Typescript.
- Modular packages (server modules: Core, Sheets, Drive, Gmail, API Key, User, ...).
- Redesign theme system.
- Official [Javascript client](https://github.com/sheetbase/client) (with framework wrappers: [Angular](https://github.com/sheetbase/angular), ...).
- Rebuild the CLI.
- Rebuild themes: <https://sheetbase.dev/themes>.

Hope you enjoy! Love <3