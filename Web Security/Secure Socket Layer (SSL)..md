# Secure Socket Layer (SSL)

Category: Security
First Refrence: What%20is%20SSL%2027d9ca2ea09c495da82f73633f050de5.md, What%20is%20SSL%20Handshake%207488b1edea6348eead9e099ae8ec4ebe.md, Is%20SSL%20Handshake%20executed%20with%20every%20request%20c5efb185061a447a87c26c3291809780.md, What%20are%20the%20steps%20of%20SSL%20Handshake%20ca979779452b4e19af7c363ff376f367.md
Tags: Common, Concept

## Concept

- Secure Socket Layer is a standard that allow to setup a safety encrypted connection between web server (Host) and web browser (Client)

## SSL Handshake

![SSL.png](Secure%20Socket%20Layer%20(SSL)%20a912a9ea6d6f40a387e906d2f10f5d1f/SSL.png)

- SSL Handshake is the process that kicks off a communication session that uses TLS encryption.
- HTTP 1.1 use keepalive to reuse a connection.
- HTTP 2 is single-connection by default.
- The subsequent calls are encrypted via the session key unless the session is ended.
1. Client request init Secure Socket Layer (SSL) to server
2. Server response `encrypted public key` & `certificate`
3. Client uses algorithm to check `cetificate` is valid.
4. Client sends back `encrypted public key` to server.
5. Server decrypted `encrypted public key` to check.
6. Server responses `encrypted content`.
7. Client receive `encrypted content` and finish `SSL/TLS handshake` connection.

---