This page provides information on how to test retrieval functionality using the Cineast CLI. You can execute the commands in two ways:
- Using the `org.vitrivr.cineast.standalone.Main` class with the arguments `$config.json $command`
- Using the Cineast CLI, which is available for both Standalone and API main methods.

It is also useful if you want to know more about which CLI starting points to look at to understand the Cineast retrieval codebase better.

## Retrieve Information about a Segment

To retrieve all metadata and features of a segment, use `retrieve-single --segmentid v_02497_13`, where the first argument is the config, the second the command and the third one provides the segmentid you want to know more about.

**Note**: you can also use vitrivr-ng and access `url/mediasegment/v_02497_13`, where the last argument is the segmentid. This will provide you with a visually more appealing variant.