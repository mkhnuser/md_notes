# Security

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

Content Security Policy might mitigate XSS attack
since it allows you to control from where your content should be uploaded.

## CSRF

CSRF relies on cookie-based sessions since a browser has to send auth credentials during an attack.
You can try mitigating this attack by settings SameSite attribute of a cookie.

Recall that Site != Origin.

You can mitigate this attack by using Anti CSRF token on your forms.

A server generates a unique CSRF token,
send it with a form,
a user submits a form with this token and the server validates this token.

Usually a CSRF token is per-session;
so you can access it at any time to do the validation.

So, you can have the following outline for creating a session:

    def create_session(user_id):
        token = random()
        session_id = random()
        store(session_id with token)
        return session_id
```
