# Security

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
