# JSON Web Token (JWT) in go
## Introduction
A JSON Web Token (JWT) is a compact and self-contained way of securely transmitting information between parties as a JSON object, and they are commonly used by developers in their APIs. JWTs are popular because:
1. A JWT is stateless. That is, it does not need to be stored in a database (persistence layer), unlike opaque tokens.
2. The signature of a JWT is never decoded once formed, thereby ensuring that the token is safe and secure.
3. A JWT can be set to be invalid after a certain period of time. This helps minimize or totally eliminate any damage that can be done by a hacker, in the event that the token is hijacked.

## A JWT is comprised of three parts:
### Header: 
the type of token and the signing algorithm used. The type of token can be “JWT” while the Signing Algorithm can either be HMAC or SHA256.
### Payload: 
the second part of the token which contains the claims. These claims include application-specific data(e.g, user id, username), token expiration time(exp), issuer(iss), subject(sub), and so on.
### Signature: 
the encoded header, encoded payload, and a secret you provide are used to create the signature.

## Token Types
Since a JWT can be set to expire (be invalidated) after a particular period of time, two tokens will be considered in this application:

### Access Token: 
An access token is used for requests that require authentication. It is normally added in the header of the request. It is recommended that an access token has a short lifespan, say 15 minutes. Giving an access token a short time span can prevent any serious damage if a user’s token is tampered with. In the event that the token is hijacked, the hacker only has 15 minutes or less to carry out his operations before the token is invalidated.

### Refresh Token: 
A refresh token has a longer lifespan, usually seven days. This token is used to generate new access and refresh tokens. In the event that the access token expires, new sets of access and refresh tokens are created when the refresh token route is hit (from our application).

## Where to Store a JWT

For a production grade application, it is highly recommended that you store JWTs in an HttpOnly cookie. To achieve this, while sending the cookie generated from the backend to the frontend (client), a HttpOnly flag is sent along the cookie, instructing the browser not to display the cookie through the client-side scripts. Doing this can prevent XSS (Cross Site Scripting) attacks. JWT can also be stored in browser local storage or session storage. Storing a JWT this way can expose it to several attacks such as XSS mentioned above, so it is generally less secure when compared to using `HttpOnly cookie technique.
