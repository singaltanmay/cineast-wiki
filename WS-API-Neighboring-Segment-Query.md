## Message Type
[`Q_NESEG`](Message-Type-Glossary#q_neseg)

## Description
Make a lookup for the [`SegmentDescriptors`](Objects-Glossary#segmentdescriptor) that are neighbors of the provided segment ID.

## Request Description
* [`NeighboringSegmentQuery`](Objects-Glossary#neighboringsegmentquery) message is to be sent.


## Example Request Message
```json
{
  "segmentId": "i_iG9qUCIPLRWr8zvY_1",
  "count": 4,
  "messageType": "Q_NESEG"
}
```

## Example Response Messages
```json
{
  "queryId": "f3fed426-5712-4246-afa7-e3b82183640c",
  "messageType": "QR_START"
}

{
  "content" :[ ],
  "queryId":"f3fed426-5712-4246-afa7-e3b82183640c",
  "messageType":"QR_SEGMENT"
}

{
  "queryId": "f3fed426-5712-4246-afa7-e3b82183640c",
  "messageType": "QR_END"
}
```

## Response Description
* 3 messages will be recieved in the order - [`QueryStart`](Objects-Glossary#querystart), [`SegmentQueryResult`](Objects-Glossary#segmentqueryresult) followed by [`QueryEnd`](Objects-Glossary#queryend).
* Neighboring Segment result will be in [`SegmentQueryResult`](Objects-Glossary#segmentqueryresult) message.
