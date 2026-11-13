# Browser

## Origin

Origin = scheme + host name + port.

## Same Origin Policy

Local storage, session storage, and IndexedDB are per origin.
No origin can access another origin data.
Understand: cookies have a different notion of origin.

## Cookies

Cookies introduce the concept of a state to the HTTP protocol.
Cookies can be set both on a frontend and on a backend.
Use two-factor authentication to protect your app from session hijacking.

## Strict Transport Security

String Transport Security says to a browser to always upgrade to HTTPS.

## CSP

Content Security Policy might mitigate XSS attack.

## CSRF attack

A CSRF attack often relies on cookies:
a browser has to automatically send authentication credentials during an attack.
To mitigate this attack, use anti-CSRF token and configure cookies to `SameSite`.
