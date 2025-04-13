## Concept

- Cross-Site Scripting (XSS) attacks are a type of injection.
    - It injects a malicious scripts are injected into otherwise benign and trusted websites.
- XSS attacks attempt to inject JavaScript in trusted sites.
    - Injected JavaScript can then steal tokens from cookies and local storage.
    - Common XSS attacks are usually caused by improper validation of data passed to the backend
- Any data received from clients must always be sanitized.
    - If cookies are used, it is possible to protect them from being accessed by JavaScript by setting the `HttpOnly` flag.
    - The `HttpOnly` flag, while useful, will not protect the cookie from CSRF attacks.
- Cross-Site Scripting (XSS) attacks occur when:
    - Data enters a Web application through an untrusted source, most frequently a web request.
    - The data is included in dynamic content that is sent to a web user without being validated for malicious content.
- The malicious content sent to the web browser often takes the form of a segment of JavaScript, but may also include HTML, Flash, or any other type of code that the browser may execute.
    - Transmitting private data, like cookies or other session information, to the attacker
    - Redirecting the victim to web content controlled by the attacker, or performing other malicious operations on the user’s machine under the guise of the vulnerable site.

## Category

### Reflected XSS Attacks

- Non-persistent cross-site scripting attack
- Data injected by attacker is reflected in the response.
- Reflected attacks are those where the injected script is reflected off the web server
    - An error message
    - Search result
    - Any other response that includes some or all of the input sent to the server as part of the request.
- Reflected attacks are delivered to victims via another route
    - In an e-mail message
    - On some other website.
- When a user is tricked into
    - Clicking on a malicious link,
    - Submitting a specially crafted form
    - Browsing to a malicious site
    
    ⇒ The injected code travels to the vulnerable web site
    
    - Which reflects the attack back to the user’s browser.
        - The browser then executes the code because it came from a “trusted” server.

### Stored XSS Attacks

- Non-persistent cross-site scripting attack
- Injected script is permanently stored on the target servers.
    - Database
    - Message forum
    - Visitor log
    - Comment field
- The victim then retrieves the malicious script from the server when it requests the stored information.
- Persistent XSS is more harmful that non-persistent XSS, because the script will automatically execute whenever the user opens the page to see the content.

### DOM-based cross-site scripting attack

- It occurs when the XSS vector executes as a result of a DOM modification on a website in a user’s browser.
- On the client side, the HTTP response does not change but the script executes in malicious manner.
    - This is the most advanced and least-known type of XSS.

## Reasons why cross-site scripting occurs

- The primary reason for cross-site script attacks is the trust of developers for users.

- Developers easily think that users will never try to perform anything wrong, so they create applications without using any extra efforts to filter user input in order to block any malicious activity.

- This attack has so many variants.

### Create a good XSS filter to block most XSS vectors

- We have to sanitize some data before being used on website.
    - The URL
    - HTTP referrer objects
    - GET parameters from a form
    - POST parameters from a form
    - Window.location
    - Document.referrer
    - document.location
    - document.URL
    - document.URLUnencoded
    - cookie data
    - headers data
    - database data, if not properly validated on user input
1. Encode special characters.
2. Use libraries for preventing XSS attack