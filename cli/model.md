# Model

Create database models.
Proxy of **project model**

## Options

- `schemaFiles`: List of schema files.
- `-d,--database`: Custom database.
- `-c,--clean`: Remove the default 'Sheet1'.

## Exmaples

- `sheetbase model` // create all models, come with the project
- `sheetbase model xxx.json` // create xxx model, from xxx.json schema
- `sheetbase model -c` // create models, also delete 'Sheet1'
- `sheetbase model -d XXX` // create models, to XXX database.