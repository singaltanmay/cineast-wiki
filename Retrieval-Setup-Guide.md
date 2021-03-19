# Full Stack vitrivr

This guide explains how to set up [Cineast](https://github.com/vitrivr/cineast) in a way, that the full [vitrivr](https://vitrivr.org) stack is functional for __retrieval__ (also known as __online__ mode).

After following these steps, you should have a running Cineast instace, that also serves vitrivr's UI, [vitrivr-ng](https://github.com/vitrivr/vitrivr-ng) and the media files.

## Prerequisites

* Previously setup the database layer, [CottontailDB](https://github.com/vitrivr/cottontaildb/)
* Previously extracted or somehow got data into CottontailDB
* Having the media files corresponding to the data
* All software requirements, such as a JDK >8
* Cloned or downloaded [vitrivr-ng](https://github.com/vitrivr/vitrivr-ng)
  * Performed `npm install` and `ng build --prod` in the VitrivrNG folder
* **Optional**: Ideally vitrivr-ng and cineast are siblings in the file tree, in order that the path for VitrivrNG is `../vitrivr-ng`. This path is used later in this guide.


## Setup

As stated in the [Prerequisites](#Prerequisites) above, we expect you to have a CottontailDB instance running with appropriate data.
Furthermore, for the sake of this guide, there are media files (e.g. videos, images, etc... ) at `/media/files/` and the previous extraction by cineast produced thumbnails at `/media/thumbnails/`.

1. Build Cineast using gradle (`./gradlew distZip`) and extract the distribution to somewhere sensible (in this guide, it's `/vitrivr/cineast/`).
2. Copy or create a config along the lines of the [default config](https://github.com/vitrivr/cineast/blob/master/cineast.json) to the cineast instance (in this guide `/vitrivr/cineast`).
3. Adjust the `database` section corresponding to your setup. In this guide, we have CottontailDB running on the same machine, thus it's:
   
  ```json
    "database": {
      "host": "localhost",
      "selector": "COTTONTAIL",
      "writer": "COTTONTAIL",
      "port": 1865,
      "plaintext": true
    }
  ```
  
This is pretty much the default value.

4. Navigate down to the `api` section in the config and adjust ports, thread pool size as needed and then, configure these settings:
  
  * `"serveContent": true` - This is in order to enable serving the media files, otherwise the `thumbnailLocation` and `objectLocation` settings would get ignored
  * `"serveUI": true` - Enable serving the UI from Cineast (i.e. navigating in your browser to `<cineast-host>:<cineast-port>` will result in having VitrivrNG being served).
  * `"uiLocation": "../vitrivr-ng/dist"` - The location of the UI. This is basically the path to wherever you build VitrivrNG to (using `ng build --prod`)
  * `"thumbnailLocation": "/media/thumbnails/"` - The location of all the thumbnails previously generated in an extraction step.
  * `"objectLocation": "/media/files/"` - The location of all the media files. **IMPORTANT**: During extraction, the media object's path is stored relative to the extraction root, during runtime, it is expected that this `objectLocation` setting resembles this and should therefore be `/path/to/extraction/root`.

 5. Ultimately head over to your VitrivrNG distribution files at `../vitrivr-ng/dist` and edit the `config.json` file there:

  * The `api.host` should be localhost for a local setup, or whatever your Cineast instance is.
  * The two `resources` entries should also point to your Cineast instance

   - `"host_thumbnails": "http://<cineast-host>:<cineast-port>/thumbnails/:s"` - Basically the address of the Cineast host suffixed with `/thumbnails/:s`. `:s` will be replaced by the segment id
   - `"host_objects": "http://<cineast-host>:<cineast-port>/objects/:o"` - Basically the address of the Cineast host suffixed with `/objects/:o`. `:o` will be replaced by the object id

  In our example setup, this results in the `api` and `resource` section of the VitrivrNG config being as follows:

  ```json
  "api": {
    "host": "localhost"
  },
  "resources": {
    "host_thumbnails": "http://localhost:4567/thumbnails/:s",
    "host_objects": "http://localhost:4567/objects/:o"
  }
  ```

6. Test your setup by navigating in you browser to `<protocol>://<cineast-host>:<cineast-port>` (with default settings: `http://localhost:4567`)  and see
whether VitrivrNG is served. Perform a test query and confirm both, the thumbnails are properly rendered and also the video preview is working.