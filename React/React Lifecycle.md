# React Lifecycle

Category: React
First Refrence: Describe%20React's%20lifecycle%2083e71403db5947509b668209e9c1e191.md, Where%20should%20make%20API%20in%20the%20component%20lifecycle%20W%204a56b57cb3064a0fb910e3b75f7a8e63.md, What%20happens%20when%20calling%20setState%201ad837bc808b4073b1e90ec91b14baf8.md, Why%20call%20setState%20instead%20of%20directly%20changing%20the%20b36abb974a074b77b2b2ffb0853b06a3.md, Does%20React%20re-render%20all%20components%20and%20sub%20compon%207d40dd5b036749e6a8cc7d1cf9670ad6.md, What%20is%20different%20between%20State%20and%20Props%20d27bb098d73e4bb495feccddb8d0614e.md, What%20is%20different%20between%20attributes%20and%20propertie%204886e51a5b524568a6024727409d9e4d.md, If%20you%20need%20to%20access%20the%20DOM%20node%20in%20a%20React%20comp%201a3b63b933484388bd21190e21cfd5d6.md, How%20to%20use%20context%20in%20class%20component%20359257cecfad47c3aad089bbc0fb2d94.md, When%20a%20React%20app%20renders%20slowly,%20how%20do%20you%20find%20o%2072be85b8e71247debb2bd978976af20a.md, How%20to%20pass%20data%20to%20deeply%20nested%20components%20witho%202dc3ef8c30094464a17a06fd20761f86.md, What%20is%20Context%20in%20React%20b99cf87febe74ba4b1d1e2a10acb8ceb.md, What%20happen%20if%20you%20don%E2%80%99t%20bind%20method%20in%20class%20comp%20918108683dcc4b32881028017f3b8a95.md, How%20to%20create%20a%20event%20listener%20in%20React%20b404cf0d1e434702b43d3160da9af2eb.md
Tags: Basic, Concept

# ****Lifecycle****

- There are 3 phases of React Lifecycle.

## 1. Mounting

- Putting elements into the DOM.
- Mounting occurs when the component is placed on the DOM container and the component is rendered on a webpage.
- React has 4 built-in methods that gets called, in this order, when mounting a component:

### 1.1. `constructor`

```jsx
constructor(props)
```

- This stage requires the developer to define properties and the initial state of the component.

### 1.2. `static getDerivedStateFromProps`

```jsx
static getDerivedStateFromProps(props, state)
```

- This function transforms value of props into a state of component.
    - Update state based on props.
- It is invoked right before calling the render method, both on the initial mount and on subsequent updates.
- It should return an object to update the state, or `null` to update nothing.
- Deriving state leads to verbose code and makes your components difficult to think about.

### 1.3. `render`

```jsx
render()
```

- Render elements to DOM node.

### 1.4. `componentDidMount`

```jsx
componentDidMount()
```

- Is invoked immediately after a component is mounted.
    - If you need to load data from a remote endpoint, this is a good place to instantiate the network request.
- Calling `setState()` immediately ****in `componentDidMount()` will trigger an extra rendering, but it will happen before the browser updates the screen.
    - This guarantees that even though the `render()` will be called twice in this case, the user won’t see the intermediate state.
    - Use this pattern with caution because it often causes performance issues.

## 2. Updating

- A component is updated whenever there is a change in the component's state or props.
- React has 5 built-in methods that gets called, in this order, when a component is updated:

### 2.1. `static getDerivedStateFromProps`

- Updates state from value of props.

### 2.2. `shouldComponentUpdate`

- Check state or properties changed or not to decide to update UI or not.

### 2.3. `render()`

- Re-render UI after deciding to updates component.

### 2.4. `getSnapshotBeforeUpdate`

```jsx
getSnapshotBeforeUpdate(prevProps, prevState)
```

- Invoked right before the most recently rendered output is committed.
- It enables component to capture some information from the DOM before it is potentially changed.
- Any value returned by this lifecycle method will be passed as a parameter to `componentDidUpdate()`.
    - It may occur in UIs like a chat thread that need to handle scroll position in a special way.
- A snapshot value (or `null`) should be returned.

```jsx
class ScrollingList extends React.Component {
  constructor(props) {
    super(props);
    this.listRef = React.createRef();
  }

  getSnapshotBeforeUpdate(prevProps, prevState) {
    // Are we adding new items to the list?
    // Capture the scroll position so we can adjust scroll later.
    if (prevProps.list.length < this.props.list.length) {
      const list = this.listRef.current;
      return list.scrollHeight - list.scrollTop;
    }
    return null;
  }

  componentDidUpdate(
		prevProps, 
		prevState, 
		snapshot? // returned from getSnapshotBeforeUpdate
	) {
    // If we have a snapshot value, we've just added new items.
    // Adjust scroll so these new items don't push the old ones out of view.
    // (snapshot here is the value returned from getSnapshotBeforeUpdate)
    if (snapshot !== null) {
      const list = this.listRef.current;
      list.scrollTop = list.scrollHeight - snapshot;
    }
  }

  render() {
    return (
      <div ref={this.listRef}>{/* ...contents... */}</div>
    );
  }
}
```

### 2.5. `componentDidUpdate`

```jsx
componentDidUpdate(prevProps, prevState, snapshot)
```

- Called after a component is re-rendered.
- Use this as an opportunity to interact with the DOM when the component has been updated.
- This is also a good place to do network requests as long as you compare the current props to previous props.

## 3. Unmounting

- A component is detached from the DOM container.
- React has only 1 built-in method that gets called when a component is unmounted:

### 3.1. `componentWillUnmount()`

- Is called when the component is about to be removed from the DOM.
- You should not call **`setState()`** in `componentWillUnmount()` because the component will never be re-rendered.

## State

### setState

- `setState()` schedules an update to a component’s state object.
- `setState()` enqueues changes to the component state and tells React that this component and its children need to be re-rendered with the updated state.
- When state changes, the component responds by re-rendering.
    - `setState()` will always lead to a re-render unless `shouldComponentUpdate()` returns `false`.
- Think of `setState()` as a request rather than an immediate command to update the component.
    - For better perceived performance, React may delay it, and then update several components in a single pass.
    - `setState()` does not always immediately update the component.
    - This makes reading `this.state` right after calling `setState()` a potential pitfall.
- Argument of `setState` can be new value of state or updater function.

```jsx
(state, props) => stateChange
```

- `state` is a reference to the component state at the time the change is being applied.
    - It should not be directly mutated.
- Call `setState` instead of directly changing the state value.
    - `setState` helps to control of the state across all components.
    - If update it directly, calling the `setState()` afterward may just replace the update you made.
    - When directly update the state, it does not change `this.state` immediately.
    - Instead, it creates a pending state transition, and accessing it after calling this method will only return the present value.

### state & props

- In React, both `this.props` and `this.state` represent the rendered values.
- `props` are passed into the component
- `props` should be not changed
- `state` is created in the component
- `state` is changeable

## Ref

- Ref object stores data independently with component.
    - When changing its data, not trigger re-render component.
    - When re-rendering component, ref object still holds its value.
- `ref.current` holds its current value.
- To access the DOM node, use `createRef` to create a variable that reference to DOM node via `ref` props.
- There are a few good use cases for refs:
    - Managing focus, text selection, or media playback.
    - Triggering imperative animations.
    - Integrating with third-party DOM libraries.
- When a ref is passed to an element in `render`, a reference to the node becomes accessible at the `current` attribute of the ref.

## Context

- Context provides a way to pass data through the component tree without passing props down manually at every level.
- Context data is passed down on the `value`prop using the `Context.Provider` component. It can be consumed using the `Context.Consumer` component or the `contentType` static property of class.
1. Create context variable using `React.createContext()`
2. Use provider of this context as a Container inside Parent component.
3. Pass state into context via value prop of provider.
4. In deeply nested component, assign context into static property name `contextType`
5. Use context value via `context` attribute of class.

```
// Context lets us pass a value deep into the component tree
// without explicitly threading it through every component.
// Create a context for the current theme (with "light" as the default).
const ThemeContext = React.createContext('light'); // [1]

class App extends React.Component {
  render() {
    // Use a Provider to pass the current theme to the tree below.
    // Any component can read it, no matter how deep it is.
    // In this example, we're passing "dark" as the current value.
    return (
			{/* [2] + [3] */}
      <ThemeContext.Provider value="dark">
        <Toolbar />
      </ThemeContext.Provider>
    );
  }
}

// A component in the middle doesn't have to
// pass the theme down explicitly anymore.
function Toolbar() {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

class ThemedButton extends React.Component {
  // Assign a contextType to read the current theme context.
  // React will find the closest theme Provider above and use its value.
  // In this example, the current theme is "dark".
  static contextType = ThemeContext; // [4]
  render() {
		{/* [5] */}
    return <Button theme={this.context} />;
  }
}

```

---

# Vocabulary

- potential pitfall: cạm bẫy tiềm ẩn
- mutate: đột biến
- transition: sự chuyển đổi