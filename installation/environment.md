# Environment Setup

To get started with Sheetbase, the only requirement is a Node & npm environment.

Of course, you will also need an editor. We recommend VS Code, a free, batteries-included text editor made by Microsoft.

## Node & npm

Almost all tooling for modern JavaScript projects is based in **Node.js**. The [download](https://nodejs.org/en/download/) page has prebuilt installation packages for all platforms. We recommend selecting the LTS version to ensure best compatibility.

Node is bundled with **npm**, the package manager for JavaScript.

To verify the installation, open a new terminal window and run:

```sh
$ node --version
$ npm --version
```

## Git

Git is required for publishing the frontend to Gihub Pages, the version control system Git is highly recommended. First, install the command-line utility from the [download](https://git-scm.com/downloads) page.

To verify the installation, open a new terminal window and run:

```sh
$ git --version
```

## Setup Google account

### Enable Apps Script API

Sheetbase hosts the backend on Google Apps Script, it needs to enable first, go to <https://script.google.com/home/usersettings>, then enable the API. Manage your Google Apps Script projects at <https://script.google.com>.

### Connect Apps Script in Drive

Add manage Google Apps Script from your Google Drive.

`My Drive > Connect more apps > (search for Google Apps Script) > Connect`

### Install Google Clasp

Google clasp is a tool for developing Google Apps Script project locally. To install, run:

```sh
$ npm install -g @google/clasp
```
