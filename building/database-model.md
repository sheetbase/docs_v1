# Using database models

Database models were used to easily create the table structure in Google Sheets. We provide a package for common use cases at [@sheetbase/models](https://github.com/sheetbase/models).

Every model was put in a dot JSON file, file name is the sheet name.

```json
// sheet: categories
// categories.json
{
  // sheet id
  "gid": 101,
  // indicate a public sheet
  "public": true,
  // table schema
  "schema": [
    { "name": "#", "type": "number", "width": 50 },
    { "name": "title", "width": 200 },
    { "name": "$key", "width": 200 }
  ]
}
```

## Define models

Using models from [@sheetbase/models](https://github.com/sheetbase/models) by puting its name to the *sheetbase.json* file.

```json
{
  // ...
  "models": [
    "categories",
    "posts"
  ]
}
```

You can also create your own models by placing .json files in the `models/` folder at the project's root.

## Create tables from models

Create tables based on models by running the command:

```sh
sheetbase model
```

All tables will be created, now you may open the database and add new data.
