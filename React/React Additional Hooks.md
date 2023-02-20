# React Additional Hooks

Category: React
First Refrence: What%20is%20useReducer%20519a861c8fe844d79610c9824b3bf17b.md, What%20is%20Memozation%202fd3adc3f3f64cccb57c3415acfdfffd.md, What%20is%20React%20memo%20cf552aad517e411db8561798741dd023.md, What%20is%20useMemo%202ca9caee5d1f46e19df7313a991e14a0.md, What%20is%20useCallback%20bacb6c94146444b8ab1ee9c2e0a550e3.md, What%20is%20the%20difference%20between%20useRef%20and%20createRe%20736cdfde5bc344979b8f3dba7de7b867.md, What%20is%20forwardRef%208df1688293a341c795ed2f153bf86923.md, When%20needed%20to%20use%20Memoization%20aa5b4fe17ead4958ade6cdbd0401528b.md
Tags: Basic, Concept

## useReducer

- An alternative to `useState`
- This hook use logic similar to Redux.
    1. It has a reducer function to process updating state.
    2. Whenever we want to set state, we dispatch a action to do that.

```jsx
const initialState = {count: 0};

function reducer(state, payload) {
  switch (payload.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
    </>
  );
}
```

## Memoization

- An optimization technique is used primarily to speed up computer programs by storing the results of expensive function calls and returning the cached result when the same inputs occur again.
    - Cache return of previous times.
    1. Calculate and save the results for each set of inputs.
    2. When we pass the input we used before, we do not recalculate, but return available results.

### Higher-Order Component `React.memo()`

- `React.memo()` similar to Pure Component.
- Pure Component is used for class component.
- `React.memo()` is used for functional component.
- Component is re-render when value of poperty is changed.
- Using shallow comparison.

```jsx
// Class component - PureComponent
export default class Hero extends PureComponent {
	render() {
		return <div>Super hero!</div>
	}
}

// Functional component - React.memo
function Hero() {
	return <div>Super hero!</div>
}
export default React.memo(Hero);
```

### useMemo

- A hook creates a memoized value and only calculate new value when the dependencies change.

```jsx
const memoizedValue = useCallback(
  () => { // args 1: process callback
    doSomething(a, b);
		return memoizedValue;
  },
  [a, b], // args 2: dependencies
);
```

### useCallback

- Create a function that will not re-create when the component re-renders.
- Hook creates a memoized callback and only create new callback when dependencies change.

```jsx
const memoizedCallback = useCallback(
  () => { // args 1: memoizedValue also memoizedCallback
    doSomething(a, b);
  },
  [a, b], // args 2: dependencies
);
```

- If you use empty dependencies, never create a new function.
    - `useCallback(fn, deps)` is equivalent to `useMemo(() => fn, deps)`

## useRef

- `useRef` returns a mutable ref object.
- When change value ⇒ NOT trigger re-render
    - Unlike state

### ref in JSX

```jsx
<tag ref={refVariable}></tag>

refCallback = (node) => { ...doSmt with node }
<tag ref={refCallback}></tag>
```

Accessing DOM nodes in the same React component

1. useRef

```jsx
import React, { useRef } from 'react';

const SimpleRef = () => {
    const inputRef = useRef<HTMLInputElement>(null);

    const onClick = () => {
        console.log('INPUT VALUE: ', inputRef.current?.value);
    }

    const onClickFocus = () => {
        console.log('Focus input');
        inputRef.current?.focus();
    }

    return (
        <div>
            <input ref={inputRef} />
            <button onClick={onClick}>Log value</button>
            <button onClick={onClickFocus}>Focus on input</button>
        </div>
    );
};
```

1. Callback Ref

```jsx
const SimpleCallbackRef = () => {
    let inputRef: HTMLInputElement | null;

    const onClick = () => {
        console.log('INPUT VALUE: ', inputRef?.value);
    }

    const onFocusClick = () => {
        console.log('Focus input');
        inputRef?.focus();
    }
    console.log('Rendering')
    return (
        <div>
            <input ref={node => { inputRef = node; }} />
            <button onClick={onClick}>Log value</button>
            <button onClick={onFocusClick}>Focus on input</button>
        </div>
    );
};
```

### forwardRef

- Ref forwarding is a technique for automatically passing a ref through a component to one of its children.
- Ref forwarding is an opt-in feature that lets some components take a ref they receive, and pass it further down (in other words, “forward” it) to a child.
- It is used for Functional components. This is a function with arguments are props and ref to returned component. So we can process ref to this component inside it, and also pass ref into its children.

```jsx
const FancyButton = React.forwardRef((props, ref) => (
  <button ref={ref} className="FancyButton">
    {props.children}
  </button>
));

// You can now get a ref directly to the DOM button:
const ref = React.createRef();
<FancyButton ref={ref}>Click me!</FancyButton>;
```

---

# Vocabulary

- Alternative: thay thế