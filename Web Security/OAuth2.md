- Authenticate token is given from third party (Facebook, Google, …)
- Access Token: token is used to authenticate for each request in a session.
- Refresh Token: token is used to recreate Access Token when it is expired.
- When session finish, Access Token is also expired, Refresh Token is used to request a new Access Token for new session without login again.
1. Web register authorization with third party.
2. User login through 3rd party’s authorization.
3. 3rd party sends OAuth2 token to server and server store it.
4. User send a request with access token to server.
5. Server forward Access Token to 3rd party to check authenticate.
6. 3rd party response to server => server response to user.