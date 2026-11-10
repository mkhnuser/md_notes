# Application Layer

## HTTP 1.1

### How do you transfer a body?

1. `Content-length` header is used when you send the whole HTTP body.
2. `Transfer-Encoding: chunked` header is used when you send an HTTP body in chunks.

### Application Optimization

Because of the way HTTP is constructed,
your application might want to read HTTP headers and / or HTTP body asynchronously:

      GET /shop/products?category=shoes HTTP/1.1\r\n
      Host: www.example.com\r\n
      User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)\r\n
      Accept: application/json\r\n
      Accept-Language: en-US,en;q=0.9\r\n\r\n

### Same-value Headers

Suppose you are given the following HTTP request:

      GET /resource HTTP/1.1\r\n
      Some-Header: one\r\n
      Some-Header: two\r\n
      Some-Header: three\r\n\r\n

Then, according to HTTP RFC, after the headers parsing, you should concatenate these values:

      Some-Header: one, two, three

### Chunked Encoding

Suppose a large blob of data has to be sent.
Or, suppose a file of an unknown size has to be sent.
`Transfer-Encoding: chunked` header is used when you send an HTTP body in chunks.
Each chunk is sent using the underlying TCP connection.

Note: chunked encoding is not supported in other HTTP versions.

### Trailer Headers

Trailer headers are headers which can be found in an HTTP response, after an HTTP body.

Note: browsers generally ignore them and prohibit access to them,
though they are defined in HTTP RFCs.

### Custom Headers

One should prefix custom headers with an `X`:

      X-Content-MD5-Checksum: ...
      X-Response-Generation-Duration: ...

### MIME types

MIME types instruct a client how to interpret a data that's being sent:

      Content-Type: application/json
      Content-Type: plain/text
      Content-Type: image/png
      Content-Type: video/mp4

### File Download

So, to implement a file download from a server, you should rely on:

1. `Content-length` for small files or Chunked Encoding for file streaming.
2. Appropriate MIME type.

          For example, for video file you would specify:

          Content-Type: video/mp4
