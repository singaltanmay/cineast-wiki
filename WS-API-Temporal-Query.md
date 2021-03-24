** Note: This page is a work in progress **

## Message Type
[`Q_TEMPORAL`](Message-Type-Glossary#q_temporal)

## Description
Executes the temporal-query based on the [`TemporalQueryComponent`](Objects-Glossary#temporalquerycomponent) objects provided in the [`TemporalQuery`](Objects-Glossary#temporalquery).

## Request Description
* A [`TemporalQuery`](Objects-Glossary#temporalquery) message is to be sent for a query.
* A [`TemporalQuery`](Objects-Glossary#temporalquery) can chain any number of queries together that will be individually evaluated and return an independent [`SimilarityQueryResult`](Objects-Glossary#similarityqueryresult) with its own `containerId` which is assigned with positive integers starting from 0.

## Example Request Message
```json
{
  "queries": [
    {
      "stages": [
        {
          "terms": [
            {
              "categories": [
                "globalcolor",
                "localcolor"
              ],
              "data": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAAEsCAYAAAB5fY51AAAABHNCSVQICAgIfAhkiAAAA/BJREFUeJzt1EENACEQwMDjPK5/KWCBH2kyo6CvrpnZH0DA/zoA4JZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZBgWkGFYQIZhARmGBWQYFpBhWECGYQEZhgVkGBaQYVhAhmEBGYYFZByqbwRWgrbyBwAAAABJRU5ErkJggg\u003d\u003d",
              "type": "IMAGE"
            }
          ]
        }
      ]
    }
    ],
  "messageType": "Q_SIM"
}
```

## Example Response Messages
```json
{
   "queryId":"3bdc0a0e-fb08-4336-acec-6bb1194019ba",
   "messageType":"QR_START"
}

{
  "content": [
    {"segmentId":"i_EWl4f23vAlZ66okc_1","objectId":"i_EWl4f23vAlZ66okc","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1},
    {"segmentId":"i_9ZkTXIT2916JCrbU_1","objectId":"i_9ZkTXIT2916JCrbU","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1},
    {"segmentId":"i_3GB3sNdQd4w7WjcT_1","objectId":"i_3GB3sNdQd4w7WjcT","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1},
    {"segmentId":"i_FY2grSrjXYT7JJcN_1","objectId":"i_FY2grSrjXYT7JJcN","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1},
    {"segmentId":"i_iG9qUCIPLRWr8zvY_1","objectId":"i_iG9qUCIPLRWr8zvY","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1},
    {"segmentId":"i_ezec2nn4mynGHSes_1","objectId":"i_ezec2nn4mynGHSes","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1},
    {"segmentId":"i_A4sdAf4Wy89TQ84I_1","objectId":"i_A4sdAf4Wy89TQ84I","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1},
    {"segmentId":"i_B4629NLw9Lgp5to6_1","objectId":"i_B4629NLw9Lgp5to6","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1},
    {"segmentId":"i_xzlhDn9baGyQdmAn_1","objectId":"i_xzlhDn9baGyQdmAn","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1},
    {"segmentId":"i_dfPuM6Tvih4K7YDD_1","objectId":"i_dfPuM6Tvih4K7YDD","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1}
  ],
  "queryId": "4a743bc1-291f-496f-9137-e5acbe3daf06",
  "messageType": "QR_SEGMENT"
}

{ 
  "content": [
    {"objectId":"i_EWl4f23vAlZ66okc","name":"Stunning Computer background image for high definition display monitor 706 - zUYJxnJ HD Desktop Wallpaper.jpg","path":"Stunning Computer background image for high definition display monitor 706 - zUYJxnJ HD Desktop Wallpaper.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataStunning Computer background image for high definition display monitor 706 - zUYJxnJ HD Desktop Wallpaper.jpg"},
    {"objectId":"i_9ZkTXIT2916JCrbU","name":"Stunning Computer background image for high definition display monitor 707 - iMiatJq HD Desktop Wallpaper.jpg","path":"Stunning Computer background image for high definition display monitor 707 - iMiatJq HD Desktop Wallpaper.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataStunning Computer background image for high definition display monitor 707 - iMiatJq HD Desktop Wallpaper.jpg"},
    {"objectId":"i_3GB3sNdQd4w7WjcT","name":"Stunning Computer background image for high definition display monitor 0707 - KkjQP7G HD Desktop Wallpaper.jpg","path":"Stunning Computer background image for high definition display monitor 0707 - KkjQP7G HD Desktop Wallpaper.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataStunning Computer background image for high definition display monitor 0707 - KkjQP7G HD Desktop Wallpaper.jpg"},
    {"objectId":"i_FY2grSrjXYT7JJcN","name":"Stunning Computer background image for high definition display monitor 0712 - TrSCBIg HD Desktop Wallpaper.jpg","path":"Stunning Computer background image for high definition display monitor 0712 - TrSCBIg HD Desktop Wallpaper.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataStunning Computer background image for high definition display monitor 0712 - TrSCBIg HD Desktop Wallpaper.jpg"},
    {"objectId":"i_iG9qUCIPLRWr8zvY","name":"Stunning Computer background image for high definition display monitor 713 - EgR6Tnr HD Desktop Wallpaper.jpg","path":"Stunning Computer background image for high definition display monitor 713 - EgR6Tnr HD Desktop Wallpaper.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataStunning Computer background image for high definition display monitor 713 - EgR6Tnr HD Desktop Wallpaper.jpg"},
    {"objectId":"i_ezec2nn4mynGHSes","name":"Stunning Computer background image for high definition display monitor 0707 - LOwW1X7 HD Desktop Wallpaper.jpg","path":"Stunning Computer background image for high definition display monitor 0707 - LOwW1X7 HD Desktop Wallpaper.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataStunning Computer background image for high definition display monitor 0707 - LOwW1X7 HD Desktop Wallpaper.jpg"},
    {"objectId":"i_A4sdAf4Wy89TQ84I","name":"Stunning Computer background image for high definition display monitor 0711 - PaTBrNY HD Desktop Wallpaper.jpg","path":"Stunning Computer background image for high definition display monitor 0711 - PaTBrNY HD Desktop Wallpaper.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataStunning Computer background image for high definition display monitor 0711 - PaTBrNY HD Desktop Wallpaper.jpg"},
    {"objectId":"i_B4629NLw9Lgp5to6","name":"Stunning Computer background image for high definition display monitor 0708 - dP700Wa HD Desktop Wallpaper.jpg","path":"Stunning Computer background image for high definition display monitor 0708 - dP700Wa HD Desktop Wallpaper.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataStunning Computer background image for high definition display monitor 0708 - dP700Wa HD Desktop Wallpaper.jpg"},
    {"objectId":"i_xzlhDn9baGyQdmAn","name":"Stunning Computer background image for high definition display monitor 0711 - YQdOoOq HD Desktop Wallpaper.jpg","path":"Stunning Computer background image for high definition display monitor 0711 - YQdOoOq HD Desktop Wallpaper.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataStunning Computer background image for high definition display monitor 0711 - YQdOoOq HD Desktop Wallpaper.jpg"},
    {"objectId":"i_dfPuM6Tvih4K7YDD","name":"Stunning Computer background image for high definition display monitor 705 - VovPbOH HD Desktop Wallpaper.jpg","path":"Stunning Computer background image for high definition display monitor 705 - VovPbOH HD Desktop Wallpaper.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataStunning Computer background image for high definition display monitor 705 - VovPbOH HD Desktop Wallpaper.jpg"}
  ],
  "queryId":"fe52b1ae-5c90-41f0-9ccd-05e68119c462",
  "messageType":"QR_OBJECT"
}

{
  "content": [
    {"key":"i_EWl4f23vAlZ66okc_1","value":0.17281249923517794},
    {"key":"i_9ZkTXIT2916JCrbU_1","value":0.13694400922090114},
    {"key":"i_3GB3sNdQd4w7WjcT_1","value":0.12228415395779534},
    {"key":"i_FY2grSrjXYT7JJcN_1","value":0.0366429846129599},
    {"key":"i_iG9qUCIPLRWr8zvY_1","value":0.03524385982887069},
    {"key":"i_ezec2nn4mynGHSes_1","value":0.03478366952769181},
    {"key":"i_A4sdAf4Wy89TQ84I_1","value":0.03186605400763856},
    {"key":"i_B4629NLw9Lgp5to6_1","value":0.023604850806160645},
    {"key":"i_xzlhDn9baGyQdmAn_1","value":0.021909456403031904},
    {"key":"i_dfPuM6Tvih4K7YDD_1","value":0.02112544946293218}
  ],
  "queryId":"fe52b1ae-5c90-41f0-9ccd-05e68119c462",
  "category":"localcolor",
  "messageType":"QR_SIMILARITY"
}

{
  "content": [
    {"segmentId":"i_3GB3sNdQd4w7WjcT_1","objectId":"i_3GB3sNdQd4w7WjcT","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1},
    {"segmentId":"i_9ZkTXIT2916JCrbU_1","objectId":"i_9ZkTXIT2916JCrbU","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1},
    {"segmentId":"i_EWl4f23vAlZ66okc_1","objectId":"i_EWl4f23vAlZ66okc","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1},
    {"segmentId":"i_FmTdNWGCZwtF9efh_1","objectId":"i_FmTdNWGCZwtF9efh","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1},
    {"segmentId":"i_FY2grSrjXYT7JJcN_1","objectId":"i_FY2grSrjXYT7JJcN","start":0,"end":0,"startabs":0.0,"endabs":0.0,"count":1,"sequenceNumber":1}
  ],
  "queryId":"fe52b1ae-5c90-41f0-9ccd-05e68119c462",
  "messageType":"QR_SEGMENT"
}

{
  "content": [
      {"objectId":"i_3GB3sNdQd4w7WjcT","name":"Stunning Computer background image for high definition display monitor 0707 - KkjQP7G HD Desktop Wallpaper.jpg","path":"Stunning Computer background image for high definition display monitor 0707 - KkjQP7G HD Desktop Wallpaper.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataStunning Computer background image for high definition display monitor 0707 - KkjQP7G HD Desktop Wallpaper.jpg"},
      {"objectId":"i_9ZkTXIT2916JCrbU","name":"Stunning Computer background image for high definition display monitor 707 - iMiatJq HD Desktop Wallpaper.jpg","path":"Stunning Computer background image for high definition display monitor 707 - iMiatJq HD Desktop Wallpaper.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataStunning Computer background image for high definition display monitor 707 - iMiatJq HD Desktop Wallpaper.jpg"},
      {"objectId":"i_EWl4f23vAlZ66okc","name":"Stunning Computer background image for high definition display monitor 706 - zUYJxnJ HD Desktop Wallpaper.jpg","path":"Stunning Computer background image for high definition display monitor 706 - zUYJxnJ HD Desktop Wallpaper.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataStunning Computer background image for high definition display monitor 706 - zUYJxnJ HD Desktop Wallpaper.jpg"},
      {"objectId":"i_FmTdNWGCZwtF9efh","name":"IMG_20180802_123604.jpg","path":"IMG_20180802_123604.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataIMG_20180802_123604.jpg"},
      {"objectId":"i_FY2grSrjXYT7JJcN","name":"Stunning Computer background image for high definition display monitor 0712 - TrSCBIg HD Desktop Wallpaper.jpg","path":"Stunning Computer background image for high definition display monitor 0712 - TrSCBIg HD Desktop Wallpaper.jpg","mediatype":"IMAGE","contentURL":"/home/vitrivr/vitrivr-ng/dist/dataStunning Computer background image for high definition display monitor 0712 - TrSCBIg HD Desktop Wallpaper.jpg"}
    ],
    "queryId":"fe52b1ae-5c90-41f0-9ccd-05e68119c462",
    "messageType":"QR_OBJECT"
}

{
  "content": [
      {"key":"i_3GB3sNdQd4w7WjcT_1","value":0.32704686459308396},
      {"key":"i_9ZkTXIT2916JCrbU_1","value":0.3214711219227607},
      {"key":"i_EWl4f23vAlZ66okc_1","value":0.29362388470205847},
      {"key":"i_FmTdNWGCZwtF9efh_1","value":0.2521176900103973},
      {"key":"i_FY2grSrjXYT7JJcN_1","value":0.014330035844392276}
    ],
    "queryId":"fe52b1ae-5c90-41f0-9ccd-05e68119c462",
    "category":"globalcolor",
    "containerId":0,
    "messageType":"QR_SIMILARITY"
}

{
  "queryId":"fe52b1ae-5c90-41f0-9ccd-05e68119c462",
  "messageType":"QR_END"
}
```

## Response Description
* The temporal query result will consist of a series of messages.
* The first message will be of type [`QueryStart`](Objects-Glossary#querystart) & the last message will be of type [`QueryEnd`](Objects-Glossary#queryend).
* Between the [`QueryStart`](Objects-Glossary#querystart) & the last message will be of type [`QueryEnd`](Objects-Glossary#queryend) & [`QueryEnd`](Objects-Glossary#queryend) messages, there will be message groups.
* A message group consist of 3 messages of type viz. [`SegmentQueryResult`](Objects-Glossary#segmentqueryresult), [`ObjectQueryResult`](Objects-Glossary#objectqueryresult) & [`SimilarityQueryResult`](Objects-Glossary#similarityqueryresult) which give results about a particular category (specified in [`SimilarityQueryResult`](Objects-Glossary#similarityqueryresult)).
* It implies that if the total number of categories overall categories specified in the request are N in number, total messages which will be received will be 3N + 2 (2 for [`QueryStart`](Objects-Glossary#querystart) & [`QueryEnd`](Objects-Glossary#queryend)).
* [`SegmentQueryResult`](Objects-Glossary#segmentqueryresult) in a message group will have details about the segments matched within that category in [`SegmentDescriptor`](Objects-Glossary#segmentdescriptor) objects.
* [`ObjectQueryResult`](Objects-Glossary#objectqueryresult) in a message group will have details about the objects for all the segments in [`SegmentQueryResult`](Objects-Glossary#segmentqueryresult) in [`MultimediaObjectDescriptor`](Objects-Glossary#multimediaobjectdescriptor) objects.
* [`SimilarityQueryResult`](Objects-Glossary#similarityqueryresult) in a message group will have details about all the segments along with their matched value, the `category` of this message group, and to which of the temporal queries the result belongs, indicated with `containerId`.

## Errors
If any error occurs, a [`QueryError`](Objects-Glossary#queryerror) object is received.