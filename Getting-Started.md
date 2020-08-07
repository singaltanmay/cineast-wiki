This page provides a quick example to get started with two scenarios: Working _with_ already extracted features, and working with a small multimedia collection. Both scenarios assume that you either have a jar or have executed the setup as described on the [Environment Setup](https://github.com/vitrivr/cineast/wiki/Environment-Setup) page.

# Building and running Cineast

There are two ways to run Cineast: using a jar built with Gradle and starting it directly from within an IDE.

Additionally, Cineast has two entry points: `API` and `Standalone`. The `Standalone` entry point is used to run individual commands and automatically exits once the specified command has been completed, while the `API` entry point does not accept commands at startup, but offers a CLI and responds to queries.

## Building with Gradle

Generate the API jar with `gradlew cineast-api:fatJar` or the Standalone jar with `gradlew cineast-runtime:fatJar`. You can then start Cineast using a config file with `java -jar cineast-api/build/libs/cineast-api-x.x-full.jar cineast.json` or run a command using the standalone version with `java -jar cineast-runtime/build/libs/cineast-runtime-x.x-full.jar cineast.json <command>`.

## Building with an IDE

Starting the API is done via the `org.vitrivr.cineast.api.Main` class, which takes one argument: the config file (e.g. `cineast.json`). Depending on the configuration, this launches the WS / Rest / Proto Endpoints.

To run a command directly with the Standalone entry point, use the `org.vitrivr.cineast.standalone.Main` class.

Make sure that the `retriever` modules are consistent with those in your cottontail instance.

## CLI / Util Commands

The Cineast CLI provides a bunch of utilities for developing. Please check out `org.vitrivr.cineast.standalone.cli.CineastCli` for a complete overview. We just provide an example here.

Run  with the arguments `cineast.json help` or use the command `help` from the CLI to see a complete list.

# First Extraction

To extract features from data, you need a cineast config file and an extraction job config file that describes the location of your data and which features to extract. The basic structure of an extraction job config file is described on the [Extraction Configuration](https://github.com/vitrivr/cineast/wiki/Extraction-Configuration) page.

The following instructions assume that you are executing the commands from inside the Cineast API CLI started with the cineast config file as the only argument e.g. `java -jar path/to/cineast_api.jar cineast.json`. If you are using the Standalone version of Cineast, you can perform the same commands by appending them to `java -jar path/to/cineast_standalone.jar cineast.json`.

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
3. Post-process features in Cottontail DB (this step is necessary to allow the retrieval of features through Cineast):
```
optimize
```

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
3. Post-process features in Cottontail DB:
```
optimize
```

# Retrieval

This scenario assumes the following:
- You have a running [Cottontail DB](https://github.com/vitrivr/cottontaildb) instance with a `cottontaildb-data/` folder containing cineast data (segments, objects, metadata, feature data)

## Retrieve Information about a Segment

To retrieve all metadata and features of a segment, use the `org.vitrivr.cineast.standalone.Main` class with the arguments `cineast.json retrieve-single --segmentid v_02497_13`, where the first argument is the config, the second the command and the third one provides the segmentid you want to know more about.

## Retrieval with a User Interface

To actually search your collection, you can use [vitrivr-ng](https://github.com/vitrivr/vitrivr-ng) as a frontend for cineast.