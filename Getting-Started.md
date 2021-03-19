This page provides a quick example to get started assuming you've followed the steps on the [Environment Setup](https://github.com/vitrivr/cineast/wiki/Environment-Setup) page.

# Building and running Cineast

There are two ways to run Cineast: using a jar built with Gradle or starting it directly from within an IDE.

Additionally, Cineast has two entry points (jars): `API` and `Standalone`. The `Standalone` entry point is used to run individual commands and automatically exits once the specified command has been completed (but does not start API endpoints), while the `API` entry point does not accept commands at startup, but offers a CLI with the same functionality as the `Standalone` entry point and responds to Websocket / REST queries.

If you plan on using Cineast with vitrivr-ng, use the `API` entry point.

## Building with Gradle

Generate the API jar with `gradlew cineast-api:shadowJar` or the Standalone jar with `gradlew cineast-runtime:shadowJar`. You can then start Cineast using a config file with `java -jar cineast-api/build/libs/cineast-api-x.x-full.jar cineast.json` or run a command using the standalone version with `java -jar cineast-runtime/build/libs/cineast-runtime-x.x-full.jar cineast.json <command>`. Remember that the standalone version does not offer API endpoints for vitrivr-ng or other frontends.

## Building with an IDE

Starting the API is done via the `org.vitrivr.cineast.api.Main` class, which takes one argument: the config file (e.g. `cineast.json`). Depending on the configuration, this launches the WS / Rest / Proto Endpoints.

To run a command directly with the Standalone entry point, use the `org.vitrivr.cineast.standalone.Main` class.

Make sure that the `retriever` modules are consistent with those in your cottontail instance.

## CLI / Util Commands

The Cineast CLI provides a bunch of utilities for developing. Please check out `org.vitrivr.cineast.standalone.cli.CineastCli` for a complete overview. We just provide an example here.

Run  with the arguments `cineast.json help` or use the command `help` from the CLI to see a complete list.

You're reading to either [start extracting features](https://github.com/vitrivr/cineast/wiki/Extracting-Features) or, if you are working on a research project [work with existing data](https://github.com/vitrivr/cineast/wiki/Working-with-Existing-Data)