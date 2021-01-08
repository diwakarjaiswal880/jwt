# JSON Web Token (JWT) in go
## Introduction
A JSON Web Token (JWT) is a compact and self-contained way of securely transmitting information between parties as a JSON object, and they are commonly used by developers in their APIs. JWTs are popular because:
1. A JWT is stateless. That is, it does not need to be stored in a database (persistence layer), unlike opaque tokens.
2. The signature of a JWT is never decoded once formed, thereby ensuring that the token is safe and secure.
3. A JWT can be set to be invalid after a certain period of time. This helps minimize or totally eliminate any damage that can be done by a hacker, in the event that the token is hijacked.
