** Note: This Documentation is from 2019 and needs to be updated **

Cineast listens for messages on the WebSocket endpoint given below.

```
ws://localhost:4567/api/v1/websocket
```
## Key Points:
* `wss` protocol can be used if configured.
* In all the queries using WebSocket API, user sends a valid message, and in response user gets a series of result messages.
* All the messages are in JSON format.
* All messages have a messageType attribute which specifies the type of message.

## Messages
Cineast currently supports 4 types of query/lookup messages via WebSocket API. They are:
* [[Status Check|WS API Ping]]: Ping the server to get the server status.
* [[Similarity Query|WS API Similarity Query]]: Perform a similarity query.
* [[More-Like-This Query|WS API More Like This Query]]: Perform a more-like-this query.
* [[Neighbouring Query|WS API Neighboring Segment Query]]: Perform a neighboring segment query.
