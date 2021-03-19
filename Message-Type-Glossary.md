Most of the requests & responses have a `messageType` field which tells the type of message that object is. This page lists all the message types used along with their brief description for reference. A link to the message type description on this page will be available in the whole API Docs wherever that particular message type is being used.

## PING
**Ping Message**

Describes that a message is of type ping. This could either be used in request or response. [`PingRequest`](Objects-Glossary#pingrequest) & [`PingResponse`](Objects-Glossary#pingresponse) have message type `PING`.

## Q_MLT
**More Like This Query**

Describes that a message is of type [`MoreLikeThisQuery`](Objects-Glossary#morelikethisquery). This message is used to query for more segments which are like the segment provided in the object.

## Q_NESEG
**Neighboring Segment Query**

Describes that a message is of type [`NeighboringSegmentQuery`](Objects-Glossary#neighboringsegmentquery). This message is used to query for more segments which are neighbors of the segment provided in the object.

## Q_SIM
**Similarity Query Message**

Describes that a message is of type [`SimilarityQuery`](Objects-Glossary#similarityquery). This message is used to query for similar segments provided data.

## QR_END
**Query Result End**

Marks the ending of the query results. In WebSocket queries, when multiples messages forms an entire result then the [`QueryEnd`](Objects-Glossary#queryend) object with message type `QR_END` marks the end of result messages.

## QR_ERROR
**Query Result Error**

Describes error in similarity query results. In WebSocket similarity query, when an error occurs, [`QueryError`](Objects-Glossary#queryerror) object with message type `QR_ERROR` is received.

## QR_METADATA
**Query Result Metadata**

Describes that a message is of type [`MetadataQueryResult`](Objects-Glossary#metadataqueryresult). It contains details about object's metadata.

## QR_OBJECT
**Query Result Object**

Describes that a message is of type [`ObjectQueryResult`](Objects-Glossary#objectqueryresult). It contains details about the objects.

## QR_SEGMENT
**Query Result Segment**

Describes that a message is of type [`SegmentQueryResult`](Objects-Glossary#segmentqueryresult). It contains details about the segments.

## QR_SIMILARITY
**Query Result Similarity**

Describes that a message is of type [`SimilarityQueryResult`](Objects-Glossary#similarityqueryresult). It contains details about the segments matched value.

## QR_START
**Query Result Start**

Marks the starting of the query results. In WebSocket queries, when multiples messages forms an entire result then the [`QueryStart`](Objects-Glossary#querystart) object with message type `QR_START` marks the start of result messages.

## SESSION_START
**Session Start**

Describes that a message is of type [`StartSessionMessage`](Objects-Glossary#startsessionmessage). It contains details about the credentials and used to start a session.

