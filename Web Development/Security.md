# Security

## Strict Transport Security

String Transport Security says to a browser to always upgrade to HTTPS.

## CSP

Content Security Policy might mitigate XSS attack.

## CSRF attack

A CSRF attack often relies on cookies:
a browser has to automatically send authentication credentials during an attack.
To mitigate this attack, use anti-CSRF token and configure cookies to `SameSite`.
