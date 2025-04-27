# Cookie

Category: Web Storage
First Refrence: What%20is%20Cookie%20e35ea1a59a714a908ebd9a64c152b008.md, What%20the%20maximum%20amount%20of%20data%20that%20can%20be%20stored%204e4ebbcb0ab542859678f41b842a30db.md, What%20types%20of%20Data%20can%20be%20stored%20in%20cookie%20dcfdb1525a224684b8db8e9298db8f54.md, How%20the%20cookies%20are%20transmitted%20between%20client%20and%2029b21224e84641e38e92d64fe623e603.md, Describe%20the%20difference%20between%20a%20'cookie',%20'sessi%2096a72b4b2cce400b9845b7eff59385e9.md, How%20to%20prevent%20request%20from%20another%20website%20taking%208e4966ac1c574b919e78566269260c1a.md
Tags: Basic, Concept

## Concept

- Cookies are key/value pairs used by websites to store state information on the browser.
- A cookie is a piece of text that a Web server can store on the client's hard drive.
    - Cookies allow a website to store information on the user's computer and then retrieve it.
    - The pieces of information will be stored as name-value pairs.
    - Cookies are passed back and forth between the client and the server via the request + response header
- All cookies of a website will be maintained in separate cookie file and its max size will be 4KB.
- Parts of cookie:
    1. Name: unique name of cookie, not case sensitive
    2. Value
    3. Domain: which our cookies are valid
    4. Path: specified in domain
    5. Expiration
    6. Secure Flag

## Set-Cookie

- Header option of both request and response to define cookies

```html
Set-Cookie: <name>=<value>[; <Max-Age>=<age>]
`[; expires=<date>][; domain=<domain_name>]
[; path=<some_path>][; secure][; HttpOnly]

Set-Cookie: _bold-dev_session=NGp6ajRhYmRUZ3FiaE9UajFIZVIyVjM4OTJTbmlXN3Q2UFh4UkRtVThDeUNQd0xjdWp; path=/; expires=Wed, 11 May 2022 10:33:35 GMT; secure; HttpOnly; SameSite=Lax
```

## Type of Cookie

### **Session cookies**

- A session cookie is sent by a website server to a browser for temporary use during a limited timeframe.
- Session cookies are enabled by default.
- Their purpose is help individual web pages load faster and improve navigation through a website.
- Each time the browser requests a web page from the server, it includes the session cookie in header of request.
- At the end of website session (all tabs of that website are closed, browser is closed), those cookies are deleted.
- This type of cookie is stored in temporary memory and is only available during an active browser session.
- A common example of a session cookie in action is in the shopping cart feature found on most e-commerce websites.
    - The session cookie stores the items that the user has added to their cart
    - They browse through the site, the items in the cart will follow them.

### Persistent cookies

- Continuous cookies
- A persistent cookie is capable of providing websites with user data, settings and any information for future visits.
- Persistent cookies can help isolate and identify a specific client and are capable of traversing a user's path toward a website.
- They are stored as text files on the hard drive of a computer and usually have expiration dates.
- Persistent cookies facilitate setting the following preferences:
    - Favorites or internal bookmarks
    - User authentication
    - Login details
    - Menu preferences
    - Theme selection, if applicable
    - Language preferences

## Cookie Scraping

- Stealing cookies attack
- In this attack, the attacker takes over the user's session.
    - A session starts when a user logs into a particular service, for example online banking, and ends when they log out.
    - The attack is based on the knowledge had by hacker  about the user's session cookie.
- To prevent that attack, we should use HTTPS, SSL certificate, add `HttpOnly` flag and Domain for cookie
    - So server can check cookie is come from valid client.

### Secure cookie

- Used only through HTTPS
- `HttpOnly` is an additional flag included in a `Set-Cookie` HTTP response header. Using the `HttpOnly` flag when generating a cookie helps mitigate the risk of client side script accessing the protected cookie (if the browser supports it).

---

# Vocabulary

- Mitigate: giảm thiểu
- Persistent: kiên trì
- Temporary: tạm thời
- Navigation: dẫn đường, đường dẫn
- Preference: tùy chọn