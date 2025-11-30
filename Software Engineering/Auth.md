# Authentication and Authorization

## OAuth Standard

### OAuth2 Password Bearer Auth

You want to authenticate user so that it can access some protected endpoints.
You've decided to use OAuth2 for this, where Auth stands for authorization.

Let's say you have /login endpoint.
Then a user must send form-encoded `username` and `password` to /login.
Note that these fields have to be named precisely in this way.
If a user is authenticated successfully, you issue a token.

```Python
return {access_token: <access_token>, token_type: "bearer"}
```

If a user is not authenticated successfully,
you respond with 401 Unauthorized HTTP code.

```Python
raise HTTPException(
    status_code=status.HTTP_401_UNAUTHORIZED,
    detail="Incorrect username or password",
    headers={"WWW-Authenticate": "Bearer"},
)
```

Note that you respond with a header that signifies that you expect a user to obtain a Bearer token.

Then, when a user wants to access a protected endpoint, it sends Authentication: Bearer <token>.
You validate that a token hasn't been tempered with.
If it hasn't, you grant access to the protected endpoint.
If it has, you ask user to authenticate again by raising 401 Unauthorized HTTP code.

Remember that a JWT token is encoded, but not encrypted: anyone can see its content.
