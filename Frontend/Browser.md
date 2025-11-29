# Browser

## Same Origin Policy

Web Storage and IndexedDB are per origin. No origin can access another origin data.
Cookies have a different notion of origin.
You should use CORS for cross origin requests.

## CORS

You can make a request to a resource, however, if remote origin does not match your
current origin, then the browser won't allow you to access the response.

Servers control CORS by settings HTTP HEADERS.
