# Security

## Same Origin Policy

Web Storage and IndexedDB are per origin.
Importand: no origin can access another origin data.
Understand: cookies have a different notion of origin.

## Cookies

Cookies introduce the concept of a state to the HTTP protocol.

You use cookies to store sessions, shopping cart, track users;
they can be set both on frontend and backend.

Use two-factor authentication to protect your app from hijacked cookies (session hijacking).

## Strict Transport Security

String Transport Security says to a browser to always upgrade to HTTPS.
https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Strict-Transport-Security

## CSP

Content Security Policy might mitigate XSS attack.

## CSRF

CSRF relies on cookie-based sessions
since a browser has to send authentication credentials during an attack.
One can try mitigate this attack by settings SameSite attribute of a cookie.
One can also use anti-CSRF token.
