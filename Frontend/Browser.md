# Browser

## Same Origin Policy

Web Storage and IndexedDB are per origin. No origin can access another origin data.
Cookies have a different notion of origin.
You should use CORS for cross origin requests.

## CORS

You can make a request to a resource, however, if remote origin does not match your
current origin, then the browser won't allow you to access the response.

Servers control CORS by settings HTTP HEADERS.

## Cookies

HTTP is stateless. You use cookies to introduce state.
Cookies are browser-specific which makes it impossible to use it on mobiles.
Cookies have a different notion of origin.
Site != origin.

Cookies might be hijacked and so sessions might be stolen.
Use two-factor auth to prevent this.

You use cookies to store sessions, shopping cart, track users.
You can set a cookies on a frontend and on a backend.

## Strict Transport Security

String Transport Security says to a browser upgrade to HTTPS.

https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Strict-Transport-Security

## CSP

Content Security Policy might make XSS attack "not so severe".
