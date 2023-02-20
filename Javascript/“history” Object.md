# “history” Object

Category: Javascript
First Source: %E2%80%9Cwindow%20Object%202fd4a2a949334bd4b9622e623a849116.md
Tags: Common, Concept

## `history.back()`

- Same as clicking back in the browser
- To move backward through history

## `history.forward()`

- Same as clicking forward in the browser
- To move forward through history

## `history.go(number)`

- Moving to a specific point in history

```jsx
window.history.go(-1) // same history.back()
window.history.go(1) // same history.forward()

// refreshing the page
window.history.go(0)
window.history.go()
```

## `history.length`

- The number of pages in the history stack