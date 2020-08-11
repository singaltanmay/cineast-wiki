To extract features from data for use with Cineast, an extraction job config JSON file must be used.

Here is a very basic example of such a job config file:
```json
{
	"input": {
		"path": "/path/to/data",
		"depth": 2,
		"id": {
			"name": "SequentialObjectIdGenerator",
			"properties": {}
		}
	},
	"extractors": [
		{"name": "AverageColor"},
		{"name": "MedianColor"}
	],
	"exporters": [
		{
			"name": "ShotThumbnailsExporter",
			"properties": {
				"destination":"/output/path/for/thumbnails"
			}
		}
	],
	"database": {
		"writer": "COTTONTAIL",
		"selector": "COTTONTAIL"
	}
}
```

The extraction config file is made up of four main parts: `input`, `extractors`, `exporters` and `database`.

## Input

The most important parts of the `input` object are:
- `path`: The path to the source data directory.
- `depth`: The depth up to which the data directory should be explored for data (e.g. a depth value of `2` searches the files in the specified directory and immediate subdirectories).
- `id`: An object containing the classname of the desired object ID generator and related properties. The available ID generators can be found in the [idgenerator package](https://github.com/vitrivr/cineast/tree/master/src/org/vitrivr/cineast/core/idgenerator).

## Extractors

The `extractors` list contains objects each containing the name of feature extractor class. The available feature extractors can be found in the [features package](https://github.com/vitrivr/cineast/tree/master/src/org/vitrivr/cineast/core/features).

## Exporters

The `exporters` list contains objects each with the name of an exporter class and associated properties. The available exporters can be found in the [exporter package](https://github.com/vitrivr/cineast/tree/master/src/org/vitrivr/cineast/core/features/exporter). These are used to export additional data, such as thumbnails in the example above.

## Database

The `database` object contains information on where the extracted data should be written, by specifying a `writer` and a `selector` option. The writer is responsible for writing the extracted data, while the selector is responsible for making sure that data that already exists in the output location (in case of e.g. a database) is not written a second time. The available options can be found in the [DatabaseConfig class](https://github.com/vitrivr/cineast/blob/master/src/org/vitrivr/cineast/core/config/DatabaseConfig.java).

The above example would attempt to write the extracted data directly into a Cottontail DB instance. To instead write extracted data as JSON files, the `database` object would have to be replaced with:
```json
"database":{
	"selector": "JSON",
	"writer": "JSON",
	"host": "/output/path/for/extracted/data/jsons"
}
```

## Type
If you wish to only extract a specific type of media, e.g. image sequences, then specify the type in the top-level config.
Otherwise, the extraction will process all media content in the given folder. 
```json
"type": "IMAGE_SEQUENCE"
```
For a full list of supported types, see [`org.vitrivr.cineast.core.data.MediaType`](https://github.com/vitrivr/cineast/blob/master/src/org/vitrivr/cineast/core/data/MediaType.java).