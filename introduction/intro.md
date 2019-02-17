# Introduction

Sheetbase is a platform that provide tools for developing modern websites and apps using free cloud services provided by Google.

It is free and fast for developer to build a product that do not carry heavy workload.

## Concept

A **Sheetbase project** (aka. Theme/Website/App) contains the BACKEND part and the FRONTEND part, communicates via REST API.

![Sheetbase](https://sheetbase.net/assets/images/explain.png "https://sheetbase.net")

### The Backend

The backend code runs in a cloud environment provides by [Google Apps Script](https://developers.google.com/apps-script/), which features come from a wide range of Google services: Google Sheets for **Database**, Drive for **Storage**, Gmail for **Mailing**, ... and other non-Google services by the external API.

### The Frontend

The client side powered by modern Javascript technology and any system that is able to contact a REST API server.

## What news?

It's been some time since the [first introducing of Sheetbase](https://medium.com/@lamnhan/introducing-sheetbase-a-new-way-to-build-websites-and-apps-c6a6bccb6254), the feedback is great, so we decided to push the platform further by rebuilding mostly every parts of it, includes:

- Using Typescript.
- Modular packages (server modules: Core, Sheets, Drive, Gmail, API Key, ...).
- Redesign theme system.
- Official [Javascript client](https://github.com/sheetbase/client) (w/ framework wrappers: [Angular](https://github.com/sheetbase/angular), ...).
- Rebuild the CLI.
- Rebuild themes: <https://sheetbase.net/themes>.

Hope you enjoy! Love <3