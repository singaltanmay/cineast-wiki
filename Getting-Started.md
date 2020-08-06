This page provides a quick example to get started with two scenarios: Working _with_ already extracted features, and working with a small multimedia collection. Both scenarios assume that you either have a jar or have executed the setup as described on the [Environment Setup](https://github.com/vitrivr/cineast/wiki/Environment-Setup) Page.

# Extracted Features
This scenario assumes the following:
- You have a running cottontailDB instance with a `cottontaildb-data/` folder containing cineast data (segments, objects, metadata, feature data)

## Starting the API ##

### Using Gradle ###
Generate the api jar using `gradlew cineast-api:fatJar`. You can then start cineast using a config file with `java -jar cineast-api/build/libs/cineast-api-2.5-full.jar cineast.json`

### Inside an IDE ###

Starting the API is done via the `org.vitrivr.cineast.api.Main` class, which takes one argument: the config file (e.g. `cineast.json`). Depending on the configuration, this launches the WS / Rest / Proto Endpoints.

Make sure that the `retriever` modules are consistent with those in your cottontail instance.

# First Extraction

*Coming Soon*

## CLI / Util Commands
The Cineast CLI provides a bunch of utilities for developing. Please check out `org.vitrivr.cineast.standalone.cli.CineastCli` for a complete overview. We just provide an example here.

Run `org.vitrivr.cineast.standalone.Main` with the arguments `cineast.json help` to see a complete list.

### Retrieve Information about a Segment
To retrieve all metadata and features of a segment, use the `org.vitrivr.cineast.standalone.Main` class with the arguments `cineast.json retrieve-single --segmentid v_02497_13`, where the first argument is the config, the second the command and the third one provides the segmentid you want to know more about.

## Retrieval with a User Interface
To actually search your collection, check out for example [vitrivr-ng](https://github.com/vitrivr/vitrivr-ng) as a frontend for cineast