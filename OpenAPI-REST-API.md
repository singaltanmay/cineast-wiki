Cineast can be interfaced with using its [OpenAPI](https://swagger.io/specification/) REST API.

To view the REST API documentation, navigate to `cineast-url:port/swagger-ui` where `cineast-url` is the URL of a running Cineast instance and `port` is the port the REST API is configured to use (4567 by default).
The OpenAPI specifications used to automatically generate client code for the REST API can be accessed similarly at `cineast-url:port/openapi-specs`.

## Usage

Using the OpenAPI Specifications, you have to choose your own language and then generate the bindings accordingly. We recommend to use the official [OpenAPI Generators](https://github.com/OpenAPITools/openapi-generator).

> **NOTE** Please be aware that due to a bug, currently it is recommended to turn off the validation step.

## Re-generate OpenAPI Specifications

To re-generate the OpenAPI Specifications, please follow the steps outlined in the [README](github.com/vitrivr/cineast/tree/master#generate-openapi-specification)