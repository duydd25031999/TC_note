# React Basic Hook

Category: React
First Refrence: What%20is%20useState%208c835177389a454eaaf9fbb2b5c66fba.md, useState%20can%20replace%20Redux%207f5faa4cc1a3443d941c7fcf80df4cf5.md, With%20the%20setter%20concept%20in%20useState,%20which%20case%20se%20f3d9875ca0bf40af93f3e3579d1269fa.md, If%20changing%20multiple%20states%20at%20the%20same%20time,%20will%20e620f996c8924c68abb7b75c3ce71082.md, How%20to%20update%20state%20that%20relative%20with%20previous%20st%203c2ab256ab5a416ca3b643b13255dd0d.md, If%20we%20update%20a%20State%20Hook%20to%20the%20same%20value%20as%20the%20444cb238a4024335b18eea71fc9327b5.md, What%20does%20useEffect%20do%209e45d7f403f74ef6939d7f09cc3dbeba.md, Why%20is%20useEffect%20called%20inside%20a%20component%201ca2c149f6c74577831b36d713911e5d.md, Does%20useEffect%20run%20after%20every%20render%20509e307c75d84ec9be19fef92e1a56d1.md, When%20exactly%20does%20React%20clean%20up%20an%20effect%204adfa177271c4cafb7edaf04c41c7400.md, How%20to%20get%20value%20of%20context%20in%20functional%20componen%201325a90dae464ed9a96b5046659f05a1.md
Tags: Basic, Concept

# useState

- Hook to manage state of functional component.
- Returns a stateful value, and a function to update it.
- React may group several state updates into a single re-render to improve performance. Normally, this improves performance and shouldn’t affect your application’s behavior.

```jsx
const [state, setState] = useState(initialState);

// only add new value => pass new value
setState(newValue) => newState

// Functional updates
// If the new state is computed using the previous state
// You can pass a callback to setState.
setState(prevState => {
  // Object.assign would also work
	// Return new value
  return {...prevState, ...updatedValues};
});
```

## **Lazy initial state**

- If the initial state is the result of an expensive computation, you may provide a function instead of inital value.

```jsx
const [state, setState] = useState(() => {
  const initialState = someExpensiveComputation(props);
  return initialState;
});
```

## **Bailing out of a state update**

- If you update a State Hook to the same value as the current state, React will bail out without rendering the children or firing effects.
- React may still need to render that specific component again before bailing out.
    - That shouldn’t be a concern because React won’t unnecessarily go “deeper” into the tree.

# useEffect

- The *Effect Hook* perform side effects in functional components
    - Run after React has mounted or updated the DOM.
    - `useEffect` Hook as `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.
- `useEffect` called inside a component
    - Functional component is before rendering.
    - `useEffect` register a callback for after rendering.
    - Placing `useEffect` inside the component lets us access state variable (or any props) right from the effect.
- `useEffect` return function | undefined
    - return function is Cleanup,  equivalent to `componentDidUnmount`
    - React also cleans up effects from the previous render before running the effects next time.
    - Cleanup is used for clear subcriptions + setInternal + setTimeout.

```jsx
useEffect(() => {
	...
	return cleanupCallback;
}, [dependencies]); 
```

- Called when dependencies change + after re-render
- `dependencies` used for filter states ⇒ auto call when changing filters
- Dependencies is `undefined` ⇒ always called after re-render.
- Dependencies is empty array ⇒ call only one time

```jsx
MOUNTING
- rendering
- run useEffect()
UPDATING
- rendering
- run `useEffect() cleanup` if dependencies is changed.
- run `useEffect()` if dependencies is changed.
UNMOUNTING
- run `useEffect() cleanup`.
```

# useContext

- Accepts a context object (the value returned from `React.createContext`) and returns the current context value for that context.
    - The current context value is determined by the `value` prop of the nearest `<MyContext.Provider>` above the calling component in the tree.

```jsx
import React from 'react';

const ProviderContext = React.createContext();

const App = () => {
  return (
    <ProviderContext.Provider value={{ color: 'red' }}>
      <div className='App'>
        <ChildComponent />
      </div>
    </ProviderContext.Provider>
  );
};

const ChildComponent = () => {
  const inject = React.useContext(ProviderContext);

  return <p style={{ inject.color }}>This text is {color}</p>;
};

export default App;
```

---

# Vocabulary

**Recall**

- hence: kể từ đó
- bail out: quit, leave a project, resign