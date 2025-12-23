# HTTP API Design

## HTTP Rest API

### Overview

One of the biggest advantages of having API is loose coupling: you don' need to
know the internal implementation of a service you are communicating with.

### Asynchronous Responses

Sometimes a client requests some long-running operation. In this case, you might
return a response which contains a URI to the status endpoint: /api/v1/status/<id>.

### Partial Responses

Partial Responses may be used to stream large files.
https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design
