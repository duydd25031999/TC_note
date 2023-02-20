# Web Session

Category: Web Storage
First Refrence: What%20is%20Session%20c4dbc366e4524ff28fb2fe8ccc69a67c.md, What%20is%20Session%20ID%20dd8b24ada43f41d5b1887c9edf9e1a26.md, What%20is%20sessionStorage%209e3558fba382495b93734466c1040074.md
Tags: Basic, Concept

## Concept

- A session refers to all the requests that a single client makes continuously to a server.
    - It can expire after a period of time from creation or after there is no new request after a timeframe depending on the developer.
- When server create new session. It stores session information.
- Session ID is id of record of session information.
    - Session information includes user information.
    - Session ID can be stored in cookie.

## Server-side cookie

- Session is also called as Server-side cookie.
- Stores a single cookie on the browser containing a unique Session Identifier.
    - Information of Session between server and browser is usually stores in Database.
    - SessionId - Id of the record of Session is stored in Cookie
- When browser sends another request contains cookie,  server uses sessionId in cookie to get Session information.
    - Check authetication.
    - Get user information.
- Session (Server-side cookie) is different from `sessionStorage`

## `sessionStorage`

- `sessionStorage` is similar to `localStorage`
    - `localStorage` doesn't expire
    - `sessionStorage` is cleared when the page session ends.
- Whenever a document is loaded in a particular tab in the browser, a unique page session gets created and assigned to that particular tab.
    - That page session is valid only for that particular tab.
    - A page session lasts as long as the tab or the browser is open, and survives over page reloads and restores.
- Opening multiple tabs/windows with the same URL creates `sessionStorage` for each tab/window.
    - Duplicating a tab copies the tab's `sessionStorage` into the new tab.
    - Closing a tab/window ends the session and clears objects in `sessionStorage`.

---