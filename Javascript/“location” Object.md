# “location” Object

Category: Javascript
First Source: %E2%80%9Cwindow%20Object%202fd4a2a949334bd4b9622e623a849116.md
Tags: Common, Concept

- The `window.location` object can be used to get the current page address (URL) and to redirect the browser to a new page.

# `location.href`

![Screenshot 2023-02-12 125642.png](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Screenshot_2023-02-12_125642.png)

- Returns the href (URL) of the current page
- Redirect tab hiện tại qua đổi giá trị của `location.href`

```jsx
window.location.href = "https://ExampleURL.com/";
```

## `location.origin`

![Screenshot 2023-02-12 130236.png](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Screenshot_2023-02-12_130236.png)

- Returns a string containing the canonical form of the origin of the specific location.
- Read only

### `location.protocol`

![Screenshot 2023-02-12 130321.png](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Screenshot_2023-02-12_130321.png)

- Returns the web protocol used (http: or https:)

### `location.host`

![Screenshot 2023-02-12 130544.png](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Screenshot_2023-02-12_130544.png)

- A string containing the host, that is the *hostname*, a `':'`, and the *port* of the URL.

`location.hostname` 

![Screenshot 2023-02-12 130659.png](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Screenshot_2023-02-12_130659.png)

- Returns the domain name of the web host

`location.port`

![Screenshot 2023-02-12 130841.png](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Screenshot_2023-02-12_130841.png)

- A string containing the port number of the URL.

## `location.pathname`

![Untitled](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Untitled.png)

- Returns the path and filename of the current page
- A string containing an initial `'/'` followed by the path of the URL, not including the query string or fragment.

## `location.search`

![Untitled](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Untitled%201.png)

- A string containing a `'?'` followed by the parameters or "querystring" of the URL.

## `location.hash`

![Untitled](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Untitled%202.png)

- A string containing a `'#'` followed by the fragment identifier of the URL.

# Methods

## `location.assign()`

- Loads the resource at the URL provided in parameter.
- Giống đổi giá trị của `location.href` nhưng an toàn hơn
    - Có thể catch exception

## `location.reload()`

- Reloads the current URL, like the `Refresh` button.

`location.replace()`

- Replaces the current resource with the one at the provided URL (redirects to the provided URL).
- The difference from the `assign()` method and setting the `href` property is that after using `replace()` the current page will not be saved in session History, meaning the user won't be able to use the `back` button to navigate to it.

---

- `replace()` thay thế trang hiện tại = url khác nhưng không lưu vào History ⇒ không back lại

## `location.toString()`

- Returns a string containing the whole URL.
- It is a synonym for `location.href`, though it can't be used to modify the value.