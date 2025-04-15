# React Basic

## Virtual DOM

### Questions

[1. How would you explain the concept of the Virtual DOM, and why is it a key performance optimization in React?](./React_Questions.md#virtual-dom-1)

[2. Can you describe in detail how React’s diffing (or reconciliation) algorithm works with the Virtual DOM, and what strategies it employs to minimize updates to the real DOM?](./React_Questions.md#virtual-dom-2)

[3. In large-scale applications, what potential limitations or bottlenecks might arise from the Virtual DOM mechanism, and what approaches or architectural changes would you recommend to address these issues?](./React_Questions.md#virtual-dom-3)

[4. Compare and contrast the Virtual DOM and the Shadow DOM. What are their main differences in purpose and implementation, and in which scenarios would each be most beneficial?](./React_Questions.md#virtual-dom-4)

------------------

- `The virtual DOM` (VDOM) is a programming `concept` that `representation of a UI` is kept in `memory` and `synced` with the `“real” DOM` by a `library` such as ReactDOM.
    - The virtual DOM is a concept implemented by libraries in JavaScript on top of browser APIs.
- Virtual DOM is a `lightweight JavaScript data format` that is used to `represent` the `content` of the `DOM` at a given `point in time`.
    - It has all the `same properties` as the `DOM` but is `not` as `interoperable` as the DOM.
    - When the `state changes`, `update` the `Virtual DOM first` and then `find` the `corresponding element` on the `real DOM` and to `re-render only it`.
- React `abstracts` away the `DOM` from you, giving a `simpler programming model` and `better performance`.

----

- Một cách lưu trữ cấu trúc nhẹ của giao diện người dùng trong bộ nhớ, được đồng bộ hóa với DOM thực bởi ReactDOM, giúp cải thiện hiệu suất bằng cách chỉ cập nhật các phần đã thay đổi khi trạng thái thay đổi.
- Đó là 1 mapping giữa state và DOM, để khi 1 state thay đổi thì phần DOM tương ứng sẽ thay đổi theo, khiến cho hiệu suất được tối ưu hơn.

### Shadow DOM

<aside>
💡 A Shadow DOM is a `hidden DOM` which can be `attached` to any element `inside real DOM`.

</aside>

- `The Shadow DOM` is a `browser technology` designed primarily for `scoping variables` and `CSS` in `web components`.
- It works `like a normal DOM`.
- In Shadow DOM, `all of its markup and style will be scoped`.
- It refers to the browser’s potential to `add` a `subtree of DOM elements` into the `rendering of a document`, but `not` into the `DOM tree` of the `main document`.

----

- Công nghệ trình duyệt để cô lập biến và CSS trong các thành phần web, tạo ra một cây con DOM không thêm vào cây DOM chính, tập trung vào việc đóng gói hơn là hiệu suất.

| Virtual DOM | Shadow DOM |
| --- | --- |
| It revolves around solving performance issues. | It revolves around the concept of encapsulation. |
| It is a complete representation of an actual DOM.	 | It is not a complete representation of the entire DOM. |
| It groups together several changes and does a single re-render instead of many small ones.	 | It adds a subtree of DOM elements into the rendering of a document, instead of adding it to the main document’s DOM tree. |
| It creates a copy of the whole DOM object.	 | It creates small pieces of the DOM object having their own, isolated scope. |
| It does not isolate the DOM.	 | It isolates the DOM. |
| It does not help with CSS scoping.	 | It helps with CSS scoping. |

## Render function

### Questions

[1. Explain the role of the render function in a React component and its contribution to the UI update process:](./React_Questions.md#render-function-1)

[2. How do you ensure that render functions remain pure and free of side effects, and what strategies do you use to improve their performance in large-scale applications?](./React_Questions.md#render-function-2)

[3. What best practices do you recommend for structuring and maintaining complex render methods to support clarity and performance?](./React_Questions.md#render-function-3)

----

- Every React component is `required` to have the `render()` function.
- The `render()` function `returns only` the `React element`.
- The `render()` function is a specific `description of the UI` at `any given time`.
- So if the `data changes`, React will perform the `UI update` with the `corresponding data`.
- When the data changes, React will `automatically call` the `render()` function to update the UI.

----

- Mỗi React component cần hàm render() để trả về các React element mô tả giao diện.
### JSX

- JSX is a `syntax extension` to Javascript `used in ReactJS` that allows writing `Javascript` that looks `similar to HTML`.
- `After the compilation`, the JSX is translated to `React.createElement` calls.
- JSX just provides `syntactic sugar` for the `React.createElement(component, props, ...children)` function.
- Using JSX to create `HTML elements` as a `JavaScript code`, that will be `placed inside the DOM without` using `createElement()` or `appendChild()` methods.

---

- JSX là một phần mở rộng cú pháp JavaScript, giúp tạo cấu trúc giống HTML, được biên dịch thành React.createElement.

# React Lifecycle

- There are 3 phases of React Lifecycle.

### Questions

[1. How do you simulate componentDidMount using useEffect?](./React_Questions.md#react-lifecycle-1)

[2. How do you implement a componentDidUpdate-like behavior in a functional component?](./React_Questions.md#react-lifecycle-2)

[3. How do you handle cleanup actions (similar to componentWillUnmount) using useEffect?](./React_Questions.md#react-lifecycle-3)

[4. How can multiple useEffect hooks be used together in one functional component?](./React_Questions.md#react-lifecycle-4)

[5. What happens if you do not provide a dependency array to useEffect?](./React_Questions.md#react-lifecycle-5)

[6. How would you simulate getSnapshotBeforeUpdate behavior in a functional component?](./React_Questions.md#react-lifecycle-6)


[7. What are some potential pitfalls when using multiple useEffect hooks regarding their execution order?](./React_Questions.md#react-lifecycle-7)

[8. In this code, does action 1 or action 2 run first?](./React_Questions.md#react-lifecycle-8)

```jsx
useEffect(() => {
  // action 1
}, [])

useEffect(() => {
  // action 2
}, [stateA])
```

---------------------

## 1. Mounting

- Gán component vào trong Virtual DOM, từ đó render compoent lần đầu tiên

----

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

- Render lại component khi state, prop, context của component thay đổi

----

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

- Quá trình xóa component khỏi Virtual DOM

----

- A component is detached from the DOM container.
- React has only 1 built-in method that gets called when a component is unmounted:

### 3.1. `componentWillUnmount()`

- Is called when the component is about to be removed from the DOM.
- You should not call **`setState()`** in `componentWillUnmount()` because the component will never be re-rendered.

## Ref

### Question

1. What is a ref in React and how does it differ from state?

- A ref provides a way to access and store a reference to a DOM element or a mutable value in a component.
- Updating a ref does not trigger a re-render, while updating state does.
- Refs are useful for situations where you need to manage values that persist across renders without affecting the UI.

2. How does the useRef hook work in functional components and what are its typical use cases?

- useRef returns a mutable object with a .current property that can hold any value.
- The initial value is set only once and persists throughout the component’s lifecycle.
- Common use cases include:
  - Accessing a DOM node directly (e.g., focusing an input).
  - Storing a mutable value that does not need to cause re-render when it changes.
  - Integrating with third-party libraries where direct DOM manipulation is required.

3. Can you provide an example of how to use useRef to manage focus on an input element and discuss potential benefits or pitfalls?

Example Usage:
• Create a ref using const inputRef = useRef(null).
• Attach it to an input element using `<input ref={inputRef} />`.
• In an event handler or effect, call inputRef.current.focus() to set focus on the input element.

Benefits:
• It allows imperative control over the DOM while avoiding unnecessary re-renders.
• It helps to integrate with non-React code or third-party libraries seamlessly.

Pitfalls:
• Overuse of refs can lead to code that is harder to maintain because it bypasses React’s declarative data flow.
• Relying too much on imperative actions may make the component behavior less predictable.

----

- Quản lý dữ liệu độc lập với vòng đời của React
- Khi thay đổi giá trị không làm React Component update

------

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



# Hook concept

## Concept

- Hooks are backwards-compatible.
- Hooks are functions that let you “hook into” React state and lifecycle features from functional components.
- They let using React without classes.

### Problems with React class component

- **It’s hard to reuse stateful logic between components.**
    - React doesn’t offer a way to “attach” reusable behavior to a component.
    - Class components design use render props and higher-order components that try to solve this.
    - *Hooks allow you to reuse stateful logic without changing component hierarchy.*
- **Complex components become hard to understand.**
    - Old lifecycle has many status ⇒ when fetching data will be scattered.
    - Components might perform some data fetching in `componentDidMount` and `componentDidUpdate`. However, the same `componentDidMount`method might also contain some unrelated logic that sets up event listeners, with cleanup performed in `componentWillUnmount`.
    - *Hooks let you split one component into smaller functions based on what pieces are related (such as setting up a subscription or fetching data).*
- **Classes confuse both people and machines.**
    - People can understand props, state, and top-down data flow perfectly well but still struggle with classes.
    - The distinction between function and class components in React and when to use each one leads to disagreements even between experienced React developers.
    - *Hooks let you use more of React’s features without classes.*

# Manage State

## Local state

- Local state is data we manage in one or another component.
- Local state is most often managed in React using the `useState` or `useReducer`.

## Global state

- Global state is data we manage across multiple components.
- Global state is necessary when we want to get and update data anywhere in our app, or in multiple components at least.

## Server state

- Data that comes from an external server that must be integrated with our UI state.
- Server state is a simple concept, but can be hard to manage alongside all of our local and global UI state.

## URL state

- Data that exists on our URLs, including the pathname and query parameters.
- Using React Router, get all the information using `useHistory` or `useLocation`.

# React Basic Hook

## State

### Questions

[1. What is the primary difference between state and props in React?](./React_Questions.md#state-1)

[2. How does the useState hook work in a functional component?](./React_Questions.md#state-2)

[3. What is lazy initialization in useState, and when would you use it?](./React_Questions.md#state-3)

[4. How does React handle state updates when the new state is the same as the current state?](./React_Questions.md#state-4)

[5. Why should you avoid updating state directly and rely on the setter function provided by useState?](./React_Questions.md#state-5)

[6. Compare between "Lazy initial state" and useMemo to transform a prop value into a new variable](./React_Questions.md#state-6)

----

- Chức năng quản lý dữ liệu của component theo khái niệm bất biến (immutability)
- State sẽ không được gán giá trị trực tiếp mà phải thông qua hàm setState

----

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

### useState

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

### **Lazy initial state**

- If the initial state is the result of an expensive computation, you may provide a function instead of inital value.

```jsx
const [state, setState] = useState(() => {
  const initialState = someExpensiveComputation(props);
  return initialState;
});
```

### **Bailing out of a state update**

- If you update a State Hook to the same value as the current state, React will bail out without rendering the children or firing effects.
- React may still need to render that specific component again before bailing out.
    - That shouldn’t be a concern because React won’t unnecessarily go “deeper” into the tree.

## useEffect

### Questions

[1. What is the role of the useEffect hook in functional components?](./React_Questions.md#use-effect-1)

[2. How do you optimize useEffect to run only when necessary?](./React_Questions.md#use-effect-2)

[3. What does passing an empty dependency array to useEffect imply?](./React_Questions.md#use-effect-3)

[4. How do you manage asynchronous tasks in useEffect and prevent potential race conditions?](./React_Questions.md#use-effect-4)

[5. How does the dependency array affect useEffect behavior, and what common pitfalls should developers be aware of?](./React_Questions.md#use-effect-5)

[6. How can you optimize performance when using multiple useEffect hooks with overlapping dependencies?](./React_Questions.md#use-effect-6)

-----

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

## Context

### Questions

[1. What is React Context, and why is it used?](./React_Questions.md#context-1)

[2. How do you create and use a context with the useContext hook?](./React_Questions.md#context-2)

[3. What are some potential drawbacks or limitations of using React Context, and how can they be mitigated?](./React_Questions.md#context-3)

[4. How can you implement dependency injection in React?](./React_Questions.md#context-4)

---

- Truyền dữ liệu qua nhiều tầng component hơn là sử dụng Props chỉ được 1-1
- Mỗi Context gồm 2 component
  - Provider: Lưu trữ 

----

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

### useContext

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

  return <p style={{ inject.color }}>This text is {inject.color}</p>;
};

export default App;
```
