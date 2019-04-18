# Build the frontend

## Developing

Develop the frontend app according to the frontend framework: Angular, Vue, React, ...

## Generate the distribution package

Sheetbase CLI provides a `build` command for building the project distribution package. To build the frontend.

```sh
sheetbase frontend build
```

Optional, pre-render the app, may need Chrome path setup below.

```sh
sheetbase frontend prerender
```

You can also run all the command above with one command.

```sh
sheetbase build --frontend
```

## Setup Chrome path

Sheetbase CLI need Chrome for `sheetbase frontend prerender` command. By default, it looks for environment variable named `GOOGLE_CHROME` or `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe` on Windows.

You can set your Chrome path variable to different Chrome execution location.

### Windows

For Windows user, open **Start menu**, search for `variables`, select `Edit environment variables for your account`, then click `New ...`:

- Variable name: `GOOGLE_CHROME`
- Variable value: (path to chrome.exe)

Click `OK` to save. Check if it set correctly, from command line, run to see the ouput:

```sh
echo %GOOGLE_CHROME%
```

### macOS and Linux

```sh
export GOOGLE_CHROME=<path to chrome execution>
```

Verify by running:

```sh
echo $GOOGLE_CHROME
```