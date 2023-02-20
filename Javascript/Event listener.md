# Event listener

Category: Javascript
Tags: Concept, Low

## **Bubbling & Capturing**

- Bubbling (default): Trigger event của child trước mới tới event của parent
- Capturing: Trigger event của parent trước mới tới event của child

```jsx
addEventListener(event, function, useCapture);
useCapture: bool
```

## Event
****preventDefault****

- Prevent default effect, event of tag
- Prevent default sẽ chặn call event khác của chính element đó

```jsx
$modelThumb.on("touchstart", (e) => {
  e.preventDefault(); // => chặn click của $modelThumb
  e.stopPropagation();
  return true;
});
```

### ****stopPropagation****

- Stop trigger event của parent

### ****stopImmediatePropagation****

- Stop trigger event của parent
- Stop các event listener khác của element đó