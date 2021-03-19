Both REST & WebSocket API uses various JSON Objects for query & results. This page lists all shared objects model and their field descriptions for reference. A link to the object description on this page will be available in the whole API Docs wherever that particular object is being used.

## Credentials
credentials of an added user in cineast

```
Credentials : Object
{
  "username": String,
  "password": String
}
```
* `username` is the username of the added user in cineast.
* `password` is the corresponding password of the added user in cineast.

## ExtractionContainerMessage
A message containing the items to be extracted.

<pre>
ExtractionContainerMessage : Object
{
  "items": Array&lt;<a href="Objects-Glossary#extractionitemcontainer">ExtractionItemContainer</a>&gt;
}
</pre>
* `items` is a list of [`ExtractionItemContainers`](Objects-Glossary#extractionitemcontainer) containing details about objects to be extracted.

## ExtractionItemContainer
An `ExtractionItemContainer` contains all the information for ONE item which is supposed to be extracted. A container MUST contain a path linking to the item to be extracted. The corresponding object MUST contain the mediaType so an item can be handed out to different extraction handlers.

<pre>
ExtractionItemContainer : Object
{
  "object": <a href="Objects-Glossary#multimediaobjectdescriptor">MultimediaObjectDescriptor</a>,
  "metadata": Array&lt;<a href="Objects-Glossary#multimediametadatadescriptor">MultimediaMetadataDescriptor</a>&gt;
}
</pre>
* `object` contains details about the item to be extracted.
* `metadata` to be associated with the object.

## Hints
hints used in [`QueryConfig`](Objects-Glossary#queryconfig) for tuning the query.

```
Hints : Enum {
  exact, inexact, lsh, ecp, mi, pq, sh, va, vaf, vav, sequential, empirical
}
```
* `config` attribute in [`SimilarityQuery`](Objects-Glossary#similarityquery), `queryId` & `hints` in [`QueryConfig`](Objects-Glossary#queryconfig) are optional and can be omitted.


## IdList
Contains a list of ids which can be used as a payload in request.

```
IdList : Object
{
  "ids": Array<String>
}
```
* `ids` is an array of String which represents an id.

## MediaType
An Enum, the value of which tells the type of media an object is

```
MediaType : Enum
{
  VIDEO, IMAGE, AUDIO, MODEL3D, UNKNOWN
}
```

## MetadataLookup
This object represents a MetadataLookup message, i.e. a request for a metadata lookup.

<pre>
MetadataLookup : Object
{
  "objectids": Array&lt;String&gt;,
  "domains": Array&lt;String&gt;,
  "messageType": "<a href="Message-Type-Glossary#m_lookup">M_LOOKUP</a>"
}
</pre>
* `objectids` is a list of object ID's for which metadata should be looked up.
* `domains` is a list of metadata domains that should be considered. If empty, all domains are considered!
* `messageType` is always [`M_LOOKUP`](Message-Type-Glossary#m_lookup).

## MetadataQueryResult
This object contains list of [`MultimediaMetadataDescriptors`](Objects-Glossary#multimediametadatadescriptor) & is received as a part of [`MetadataLookup`](Objects-Glossary#metadatalookup) results. 

<pre>
MetadataQueryResult : Object
{
  "content": Array&lt;<a href="Objects-Glossary#multimediametadatadescriptor">MultimediaMetadataDescriptors</a>&gt;,
  "queryId": String,
  "messageType": "<a href="Message-Type-Glossary#qr_metadata">QR_METADATA</a>"
}
</pre>
* `content` will be a list of [`MultimediaMetadataDescriptors`](Objects-Glossary#multimediametadatadescriptor).
* `queryId` will be same as what was in the request if specified or else will be randomly generated.
* `messageType` is always [`QR_METADATA`](Message-Type-Glossary#qr_metadata).

## MoreLikeThisQuery
This object represents a MoreLikeThisQuery message, i.e. a request for search more like the provided segment.

<pre>
MoreLikeThisQuery : Object
{
  "segmentId": String,
  "categories": Array<String>,
  "config": <a href="Objects-Glossary#queryconfig">QueryConfig</a>,
  "messageType": "<a href="Message-Type-Glossary#q_mlt">Q_MLT</a>"
}
</pre>
* `segmentId` is the id of the segment for which more-like-this query is to be performed.
* `categories` is the list of named feature categories that should be considered when doing More-Like-This.
* `config` attribute is optional and can be supplied for additional query configurations.
* `messageType` is always [`Q_MLT`](Message-Type-Glossary#q_mlt).

## MultimediaMetadataDescriptor
Contains metadata about the object.

```
MultimediaMetadataDescriptor : Object
{
  "objectId": String,
  "domain": String,
  "key": String,
  "value": String
}
```
* `objectId` is the id of the object this metadata belongs to.
* `domain` tells the metadata domain (e.g. EXIF, IPTC, DC...).
* `key` is the key of the metadata.
* `value` is the value corresponding to the `key`.

## MultimediaObjectDescriptor
Contains details about a particular multimedia object.

<pre>
MultimediaObjectDescriptor : Object
{
  "objectId": String,
  "name": String,
  "path": String,
  "mediatype": <a href="Objects-Glossary#mediatype">MediaType</a>,
  "contentURL": String
}
</pre>
* `objectId` uniquely identifies a given `MultimediaObjectDescriptor` object.
* `name` is the name of the multimedia object.
* `path` is the path of multimedia object known to Cineast.
* `mediaType` is the type of multimedia the object is.
* `contentURL` is the absolute path of the multimedia object.

## NeighboringSegmentQuery
This object represents a NeighboringSegmentQuery message, i.e. a request for a neighbour-search.

<pre>
NeighboringSegmentQuery : Object
{
  "segmentId": String,
  "count": Int,
  "config": <a href="Objects-Glossary#queryconfig">QueryConfig</a>,
  "messageType": "<a href="Message-Type-Glossary#q_neseg">Q_NESEG</a>"
}
</pre>
* `segmentId` is the id of the segment for which neighbors should be retrieved.
* `count` is the Number of neighbors that should be retrieved.
* `config` attribute is optional and can be supplied for additional query configurations.
* `messageType` is always `<a href="Message-Type-Glossary#q_neseg">Q_NESEG</a>`.

## ObjectQueryResult
This object contains list of [`MultimediaObjectDescriptors`](Objects-Glossary#multimediaobjectdescriptor) & is received as a part of query results.

<pre>
ObjectQueryResult : Object
{
  "content": Array&lt;<a href="Objects-Glossary#multimediaobjectdescriptor">MultimediaObjectDescriptor</a>&gt;,
  "queryId": String,
  "messageType": "<a href="Message-Type-Glossary#qr_object">QR_OBJECT</a>"
}
</pre>
* `content` will be a list of [`MultimediaObjectDescriptors`](Objects-Glossary#multimediaobjectdescriptor).
* `queryId` will be same as what was in the request if specified or else will be randomly generated.
* `messageType` will always be [`QR_OBJECT`](Message-Type-Glossary#qr_object).

## PingRequest
An object to be sent to ping the server

<pre>
PingRequest : Object
{
  "messageType": "<a href="Message-Type-Glossary#ping">PING</a>"
}
</pre>
* `messageType` is always [`PING`](Message-Type-Glossary#ping) to specify it's a ping request.

## PingResponse
An object received which contains ping status of the server.

<pre>
PingResponse : Object
{
  "status": <a href="Objects-Glossary#pingstatus">PingStatus</a>,
  "messageType": "<a href="Message-Type-Glossary#ping">PING</a>"
}
</pre>
* `status` tells the ping result of the server.
* `messageType` is always [`PING`](Message-Type-Glossary#ping).

## PingStatus
An enum which specifies the all the ping status of the server.

```
PingStatus : Enum
{
  UNKNOWN, OK, ERROR
}
```

## QueryComponent
It represents a query container with multiple [`QueryTerms`](Objects-Glossary#queryterm).

<pre>
QueryComponent : Object
{
  "terms": Array&lt;<a href="Objects-Glossary#queryterm">QueryTerm</a>&gt;
}
</pre>
* `terms` is a list of [`QueryTerms`](Objects-Glossary#queryterm).

## QueryConfig
A configuration object which is used to tune query.

<pre>
QueryConfig : Object
{
  "queryId": String
  "hints": Array&lt;<a href="Objects-Glossary#hints">Hints</a>&gt;
}
</pre>
* `queryId` will be same as what was in the request if specified or else will be randomly generated.
* `hints` is a list of [`Hints`](Objects-Glossary#hints) supplied to tune query.

## QueryEnd
This object is received at the end of query results when using WebSockets.

<pre>
QueryEnd : Object
{
  "queryId": String,
  "messageType": "<a href="Message-Type-Glossary#qr_end">QR_END</a>"
}
</pre>
* `queryId` will be same as what was in the request if specified or else will be randomly generated.
* `messageType` will always be [`QR_END`](Message-Type-Glossary#qr_end).

## QueryError
This object is receieved if an error occurs during retrieval.

<pre>
QueryError : Object
{
  "queryId": String,
  "message": String,
  "messageType": "<a href="Message-Type-Glossary#qr_error">QR_ERROR</a>"
}
</pre>
* `queryId` will be same as what was in the request if specified or else will be randomly generated.
* `message` is the error message.
* `messageType` is always [`QR_ERROR`](Message-Type-Glossary#qr_error).

## QueryTerm
It represents a particular query term in a [`QueryComponent`](Objects-Glossary#querycomponent).

<pre>
QueryTerm : Object
{
  "type": <a href="Objects-Glossary#querytermtype">QueryTermType</a>,
  "data": String,
  "categories": Array&lt;String&gt;
}
</pre>
* type is a [`QueryTermType`](Objects-Glossary#querytermtype) which tells the type of query term.
* QueryTerm Object ```data``` format:

[`QueryTermType`](Objects-Glossary#querytermtype) | data
--- | ---
IMAGE | <ul><li>Must be a valid Data URI.</li><li>Format : "data:image/png;base64,**base64String**".</li><li>**base64String** to be replaced with actual image base64 data.</li></ul>
AUDIO | <ul><li>Must be a valid Data URI.</li><li>Format : "data:audio/wav;base64,**base64String**".</li><li>**base64String** to be replaced with actual audio3 base64 data.</li><li>Only wav audio is currently supported.</li><li>Audio settings **must** be 22050Hz sample rate, Mono channel, 16bit PCM.</li></ul>
MOTION | <ul><li>Must be a valid Data URI.</li><li>Format : "data:application/json;base64,**base64String**".</li><li>**base64String** to be replaced with actual motion base64 data which is a JSON object of model MotionDataModel described below.</li></ul><pre>MotionDataModel : Object <br>{<br>&nbsp;&nbsp;"foreground" : Array&lt;Path&gt;,<br>&nbsp;&nbsp;"background" : Array&lt;Path&gt;<br>}<br><br>Path : Object <br>{<br>&nbsp;&nbsp;"path": Array&lt;Point&gt;<br>}<br><br>Point : Object<br>{<br>&nbsp;&nbsp;"x": Float<br>&nbsp;&nbsp;"y": Float<br>}</pre> <ul><li>`x` is relative X position ranging from 0 for extreme left to 1 for extreme right.</li><li>`y` is relative Y position ranging from 0 for extreme top to 1 for extreme bottom.</li><ul>
MODEL3D | <ul><li>Supports two types of data - either the JSV4 JSON format for Meshes OR a valid image (for 2D sketch to 3D model lookup).<br><ol><li>JSV4 JSON format<br><ul><li>Must be a valid Data URI.</li><li>Format : "data:application/3d-json;base64,**base64String**".</li><li>**base64String** to be replaced with valid 3D Model data. The **base64String** gets parsed into 3D Mesh and treated as Geometry JSON used by the Three.js JavaScript library.</li></ul></li><li>2D sketch to 3D model lookup<br><ul><li>Must be a valid Data URI.</li><li>Format : "data:image/png;base64,**base64String**".</li><li>**base64String** to be replaced with actual image base64 data.</li></ul></li></ol></li>
LOCATION | <ul><li>data is a JSON object with model described below</li><li>Latitude value must lie between [-90,90]</li><li>Longitude value must lie between [-180,180)</li></ul><pre>LocationDataModel : Object <br>{<br>&nbsp;&nbsp;"latitude" : Float,<br>&nbsp;&nbsp;"longitude" : Float<br>}</pre>
TIME | <ul><li>The data must be a string which represents a valid instant in UTC. It is parsed using [Instant#parse](https://docs.oracle.com/javase/8/docs/api/java/time/Instant.html#parse-java.lang.CharSequence-).</li></ul>
TEXT | <ul><li>The data must be a string, the text to search for.</li></ul>
TAG | <ul><li>Must be a valid Data URI.</li><li>Format : "data:application/json;base64,**base64String**".</li><li>**base64String** to be replaced with actual base64 data which is an array of JSON object of model TagModel described below.</li></ul><pre>TagModel : Object <br>{<br>&nbsp;&nbsp;"id" : String,<br>&nbsp;&nbsp;"name": String,<br>&nbsp;&nbsp;"description": String,<br>&nbsp;&nbsp;"weight": Float<br>}</pre><ul><li>id attribute is required but others can be omitted.</li><li>default value of weight if not supplied is 1.0</li><ul>

* QueryTerm Object ```categories```:

The categories are the collection of features to search for. They can be found [here](https://github.com/vitrivr/cineast/blob/master/cineast.json). All the nodes in `features` block in `retriever` block are categories with subnodes being the features belonging to that particular category.

## QueryTermType
An Enum which tells the type of a query term.

```
QueryTermType : Enum
{
  IMAGE, AUDIO, MOTION, MODEL3D, LOCATION, TIME, TEXT, TAG
}
```

## QueryStart
This object is received at the start of query results when using WebSockets.

<pre>
QueryStart : Object
{
  "queryId": String,
  "messageType": "<a href="Message-Type-Glossary#qr_start">QR_START</a>"
}
</pre>
* `queryId` will be same as what was in the request if specified or else will be randomly generated.
* `messageType` will always be [`QR_START`](Message-Type-Glossary#qr_start).

## SegmentDescriptor
Contains details about a particular multimedia object's segment.

```
SegmentDescriptor : Object
{
  "segmentId": String,
  "objectId": String,
  "start": Int,
  "end": Int,
  "startabs": Float,
  "endabs": Float,
  "sequenceNumber": Int,
  "count": Int
}
```
* `segmentId` uniquely identifies a given `SegmentDescriptor` object.
* `objectId` is the id of the segment's object.
* `start` tells the start frame of this segment if applicable else is 0.
* `end` tells the end frame of this segment if applicable else is 0.
* `startabs` tells the absolute starting time (in s) of this segment if applicable else is 0.
* `endabs` tells the absolute ending time (in s) of this segment if applicable else is 0.
* `sequenceNumber` is the segment's sequence number. All segments of an object have incremental sequence number starting from 1.
* `count` is the total frames in this segment.

## SegmentQueryResult
This object contains list of [`SegmentDescriptors`](Objects-Glossary#segmentdescriptor) & is received as a part of query results.

<pre>
SegmentQueryResult : Object
{
  "content": Array&lt;<a href="Objects-Glossary#segmentdescriptor">SegmentDescriptor</a>&gt;,
  "queryId": String,
  "messageType": "<a href="Message-Type-Glossary#qr_segment">QR_SEGMENT</a>"
}
</pre>
* `content` will be a list of [`SegmentDescriptors`](Objects-Glossary#segmentdescriptor").
* `queryId` will be same as what was in the request if specified or else will be randomly generated.
* `messageType` will always be [`QR_SEGMENT`](Message-Type-Glossary#qr_segment).

## SegmentWeight
It contains a segment's matched value for a query.

```
SegmentWeight : Object
{
  "key": String,
  "value": Float
}
```
* `key` is the segment id for which this object contains matched value.
* `value` is the matched value for the query.

## SessionState
Contains the state of a session

<pre>
SessionState : Object
{
  "id": String,
  "validUntil": Long,
  "type": <a href="Objects-Glossary#sessiontype">SessionType</a>
}
</pre>
* `id` is the session id.
* `validUntil` tells till when the session is valid.
* `type` tells the type of session.

## SessionType
An enum which tells the type of the session.

```
SessionType : Enum
{
  UNAUTHENTICATED, USER, ADMIN
}
```

## SimilarityQuery
This object represents a similarity-query message, i.e. a request for a similarity-search.

<pre>
SimilarityQuery : Object
{
  "containers": Array&lt;<a href="Objects-Glossary#querycomponent">QueryComponent</a>&gt;,
  "config": <a href="Objects-Glossary#queryconfig">QueryConfig</a>,
  "messageType": "<a href="Message-Type-Glossary#q_sim">Q_SIM</a>"
}
</pre>
* `containers` is a list of [`QueryComponents`](Objects-Glossary#querycomponent).
* `config` attribute is optional and can be supplied for additional query configurations.

## SimilarityQueryResult
This object contains a list of [`SegmentWeights`](Objects-Glossary#segmentweight) & is received as a part of query results.

<pre>
SimilarityQueryResult : Object
{
  "content": Array&lt;<a href="Objects-Glossary#segmentweight">SegmentWeight</a>&gt;,
  "category: String,
  "queryId": String,
  "messageType": "<a href="Message-Type-Glossary#qr_similarity">QR_SIMILARITY</a>"
}
</pre>
* `content` will be a list of [`SegmentWeight`](Objects-Glossary#segmentweight).
* `queryId` will be same as what was in the request if specified or else will be randomly generated.
* `category` is the category for which this query result is.
* `messageType` will always be [`QR_SIMILARITY`](Message-Type-Glossary#qr_similarity).

## SimilarityResult
Contains similarity query results.

<pre>
SimilarityResult : Object
{
  "categories": Array&lt;String&gt;,
  "results": Array&lt;<a href="Objects-Glossary#similarityqueryresult">SimilarityQueryResult</a>&gt;
}
</pre>
* `categories` will contain all the categories queried.
* `results` is a list of [`SimilarityQueryResults`](Objects-Glossary#similarityqueryresult) containing results of similarity query.

## StartSessionMessage
Message to be sent when starting a session.

<pre>
StartSessionMessage : Object
{
  "credentials": <a href="Objects-Glossary#credentials">Credentials</a>
}
</pre>
* `credentials` is the credentials of an added user in cineast.

## Tag
A tag associated with an object.

```
Tag : Object
{
  "id": String,
  "name": String,
  "description": String
}
```
* `id` is the id of the object this tag belongs to.
* `name`: name of the tag.
* `description`: description of the tag.