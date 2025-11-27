# System Design

## Data Model

The advantage of document-oriented data model is that it allows you to store
everything in one document - locality - and it has a flexible schema.

## OpenAPI specs

Check out Swagger Codegen project which allows you to generate code
based on swagger specs.

## HTTP Rest API

### Overview

One of the biggest advantages of having API is loose coupling: you don' need to
know the internal implementation of a service you are communicating with.

### Asynchronous Responses

Sometimes a client requests some long-running operation. In this case, you should
return a response which contains a URI to the status endpoint: /api/v1/status/<id>.

### Partial Responses

Partial Responses may be used to stream large files.

https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design
