
## Extracting to Intermediary Format

Sometimes you may want to extract features to an intermediary file format (e.g. JSON, PROTO, etc.) before importing them into a database. To do this, adjust the extraction job config file accordingly and run just the extraction command:
```
extract --extraction extraction_config.json
```

## Importing from Intermediary Format

To import previously extracted features in a supported intermediary file format (in this example JSON) into a running Cottontail DB instance use the following commands:

1. Set up the database schema if it isn't already:
```
setup --extraction extraction_config.json
```
2. Import features:
```
import --type json --input path/to/extracted/features
```
**Note:** Features imported into Cottontail DB must be post-processed to allow retrieval through Cineast, however, this is performed by default after the `import` command. In case automatic optimization was disabled with the `--no-finalize` flag, this can be manually invoked with:
```
optimize
```
