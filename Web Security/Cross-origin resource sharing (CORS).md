## Concept

- An HTTP-header based mechanism.
- CORS behavior is not an error, it’s a security mechanism to protect users.
- Allows a server to indicate any origins (domain, scheme, or port) other than its own from which a browser should permit loading resources.
- To access other origin
    1. Server should enable the cross origin requests for that domain.
    2. Frontend add CORS header option into request
        - `Access-Control-Allow-Origin`: domain is allowable
        - `Access-Control-Request-Method`: HTTP methods are allowable
        - `Access-Control-Request-Headers`: Options will be sent with the request.