# Feature Extraction
Without extracting features from data, you will not receive any results for queries.
To extract features from data, you need a cineast config file and an extraction job config file that describes the location of your data and which features to extract. The basic structure of an extraction job config file is described on the [Extraction Configuration](https://github.com/vitrivr/cineast/wiki/Extraction-Configuration) page.

The following instructions assume that you are executing the commands from inside the Cineast CLI (available both in the API and standalone Jar)

## Best Practices
The following sections are only a guide for simple extraction of small-scale collections. For larger collections, be aware that we recommend using external parallelism for the time being (see [#115](https://github.com/vitrivr/cineast/issues/115)). For distributed extraction, we recommend extracting everything first to JSON / PROTO and then importing at the end. This is easier to back up and more reliant. Consult the [corresponding Wiki page](https://github.com/vitrivr/cineast/wiki/Extraction-to-File---Import) for details.


## Extracting directly to Cottontail DB

In the most simple use case, features are extracted directly into a running Cottontail DB instance. The instructions to set up and run Cottontail DB can be found [on its GitHub page](https://github.com/vitrivr/cottontaildb).

1. Set up the database schema for the extracted features:
```
setup --extraction extraction_config.json
```
If the database already contains existing data or a schema you would like to remove, additionally append the option `--clean`.

2. Run the data extraction:
```
extract --extraction extraction_config.json
```
