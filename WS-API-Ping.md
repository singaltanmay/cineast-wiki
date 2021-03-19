## Message Type
[`PING`](Message-Type-Glossary#ping)

## Description
Pings the server and returns the status message.

## Request Description
A [`PingRequest`](Objects-Glossary#pingrequest) object is to be sent to ping the server.

## Example Request Message
```json
{
  "messageType": "PING"
}
```

## Example Response Message
```json
{
  "status": "OK",
  "messageType": "PING"
}
```

## Response Description
* A [`PingResponse`](Objects-Glossary#pingresponse) object will be received which contains the server status.