# React Basic

## Virtual DOM

### Questtions

1. How would you explain the concept of the Virtual DOM, and why is it a key performance optimization in React?
  - Virtual DOM is like a copy of real DOM that is kept in computer’s memory. 
  - When something changes in the app, React changes this copy first. 
  - Then, it compares the copy with the real web page and updates only the parts that are different. 
  - This makes the update process faster because the real web page does not need to change completely every time. 
  - Because updating the real page can be slow, using the Virtual DOM helps React work quickly and efficiently.

2. Can you describe in detail how React’s diffing (or reconciliation) algorithm works with the Virtual DOM, and what strategies it employs to minimize updates to the real DOM?
  - Diffing is the process that when something changes, React makes a new Virtual DOM and then looks at both the old and new copies.
  - React finds the differences between the two copies. 
  - After that, it updates only the part of the real DOM that changed. 
  - This way, React does not change the whole page at once, which saves time. 
  - The diffing algorithm groups changes together so it does less work on the real DOM, making the app faster.

3. In large-scale applications, what potential limitations or bottlenecks might arise from the Virtual DOM mechanism, and what approaches or architectural changes would you recommend to address these issues?

  - In large applications, the Virtual DOM may face some limits. 
  - For example, if there are many components or very complex data, the process of comparing the old Virtual DOM with the new one can take extra time. 
  - This can slow down the update of the page. 
  - To fix this, I would break the application into smaller parts. 
  - I would also use techniques such as memoization (using React.memo) to avoid re-rendering parts that do not change. 
  - In addition, using code splitting and lazy loading can help manage the load on the Virtual DOM. These changes keep the app fast, even when it grows large.

4. Compare and contrast the Virtual DOM and the Shadow DOM. What are their main differences in purpose and implementation, and in which scenarios would each be most beneficial?
  - Virtual DOM and Shadow DOM are two different ideas. 
  - The Virtual DOM is a lightweight copy of the real DOM that React uses in memory. 
  - It helps to check changes and update only the parts of the page that have changed, which makes the updates faster. 
  - Shadow DOM, however, is a browser feature used to encapsulate a portion of the DOM. 
  - This means that it keeps styles and code separate from the rest of the page. 
  - Virtual DOM is mainly used to improve performance in apps, while Shadow DOM is useful for creating web components that need isolated styles and structure. 
  - In a typical React app, developers usually work with the Virtual DOM, but if you want more control over the styles and encapsulation, the Shadow DOM is very helpful.

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

1. Explain the role of the render function in a React component and its contribution to the UI update process:

- It is the function that returns the JSX that describes what the component looks like.
- It is called every time the component’s state or props change.
- React uses the returned output to compare the new view with the previous one.
- This comparison lets React update only the parts of the real DOM that have changed.
- This selective updating makes the UI update process faster and more efficient.

2. How do you ensure that render functions remain pure and free of side effects, and what strategies do you use to improve their performance in large-scale applications?

- I ensure the render function is pure by keeping it focused only on returning JSX.
- I avoid putting any data updates or external function calls inside the render.
- I handle side effects in lifecycle methods or with hooks like useEffect instead.
- I use React.memo or PureComponent to avoid unnecessary re-renders.
- I split large components into smaller ones to maintain clarity and boost performance.

3. What best practices do you recommend for structuring and maintaining complex render methods to support clarity and performance?

- I break the UI into smaller, reusable components to keep each render simple.
- I organize the code by using helper functions when the JSX becomes too complex.
- I separate components into container components for logic and presentational components for display.
- I make sure that every component’s render function is easy to read and maintain.
- I use optimization techniques like React.memo to improve rendering performance.

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

1. How do you simulate componentDidMount using useEffect?

- By passing an empty dependency array ([]) to useEffect, the effect runs only once after the first render.
- This setup is used to execute initialization code, similar to componentDidMount in class components.

2. How do you implement a componentDidUpdate-like behavior in a functional component?

- By specifying certain variables in the dependency array of useEffect, you can trigger the effect only when those variables change.
- This mimics componentDidUpdate by running the effect after updates that involve changes to specific state or prop values.

3. How do you handle cleanup actions (similar to componentWillUnmount) using useEffect?

- You return a cleanup function from the useEffect callback.
- This cleanup function is executed before the next effect runs or when the component unmounts, ensuring proper resource management.

4. How can multiple useEffect hooks be used together in one functional component?

- You can declare multiple useEffect hooks to separate different concerns (e.g., one for data fetching and one for event listeners).
- This separation makes the component code more organized and easier to maintain.

5. What happens if you do not provide a dependency array to useEffect?
- The effect will run after every render of the component.
- This may lead to performance issues if the effect is heavy or if it causes unwanted repeated side effects.

6. How would you simulate getSnapshotBeforeUpdate behavior in a functional component?
- There is no direct equivalent to getSnapshotBeforeUpdate, but you can use useRef to store previous values.
- Combining useRef with useEffect allows you to compare previous and current values after rendering, similar to capturing a snapshot.

7. What are some potential pitfalls when using multiple useEffect hooks regarding their execution order?

- The execution order of useEffect hooks is determined by their order in the component’s code.
- Unintended side effects can occur if dependencies are not well managed or if the hooks rely on each other’s results.
- Documenting dependencies and keeping effects simple helps avoid issues related to order and unexpected behavior.

8. In this code, does action 1 or action 2 run first

```jsx
useEffect(() => {
  // action 1
}, [])

useEffect(() => {
  // action 2
}, [stateA])
```

- At the mounting phase, they run in the order they are declared in the code.
- That means action 1 runs first, followed by action 2.

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

1. What is the primary difference between state and props in React?

State:
• Managed locally within a component.
• Mutable and can be updated over time.
• Used to store data that affects the component's behavior and rendering.

Props:
• Passed into a component from a parent.
• Immutable within the component (read-only).
• Used to share data and configuration across components.

2. How does the useState hook work in a functional component?

- It returns an array with two items: the current state value and a setter function to update that value.
- When the state is updated using the setter, React re-renders the component with the new state.
- It provides a simple way to add and manage state in functional components without using class components.

3. What is lazy initialization in useState, and when would you use it?

- Lazy initialization involves passing a function to useState rather than a direct value.
- The function is executed only once to compute the initial state on the first render.
- It is beneficial when the computation of the initial state is expensive or time-consuming.

4. How does React handle state updates when the new state is the same as the current state?

- React compares the new state value with the current state.
- If they are equal, React bails out of the update process and does not trigger a re-render.
- This optimization helps improve performance by avoiding unnecessary renders.

5. Why should you avoid updating state directly and rely on the setter function provided by useState?

- Direct mutations of state do not trigger a re-render, leading to an inconsistent UI.
- Relying on the setter function ensures that the change is queued and processed correctly by React.
- It maintains the principle of immutability, which is critical for predictable updates and efficient state management.

6. Compare between "Lazy initial state" and useMemo to transform a prop value into a new variable

Lazy Initial State (useState with a function):
• The initialization function is executed only once during the first render.
• It is ideal for performing a one-time, expensive computation that sets up initial state.
• Once the state is set, changes to the prop do not trigger a re-computation of that state value.
• It is mainly used when you need to compute an initial state value and the result remains constant or changes through state updates (e.g., via setState).

useMemo:
• It computes a value on every render only when its dependencies change.
• It is used to memoize an expensive computation that depends on the current prop value.
• When transforming a prop value, useMemo updates the computed value if the prop changes, avoiding recalculations if the prop is unchanged.
• It keeps the value up-to-date in response to changes while still optimizing performance by caching the result.

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

1. What is the role of the useEffect hook in functional components?
- It lets you perform side effects (such as data fetching, subscriptions, or manual DOM updates).
- It acts as a replacement for various lifecycle methods from class components.
- It runs after rendering and can run again if specific dependencies change.

2. How do you optimize useEffect to run only when necessary?
- Specify a dependency array that includes only the variables that should trigger the effect.
- This practice prevents unnecessary runs of the effect, improving application performance.

3. What does passing an empty dependency array to useEffect imply?
- It implies that the effect will run only once after the component’s initial render.
- This is ideal for initialization tasks and ensures that the effect does not run on subsequent updates.

4. How do you manage asynchronous tasks in useEffect and prevent potential race conditions?

- You should define an inner asynchronous function inside or outside the useEffect callback rather than making the callback async.
- Use an AbortController or a flag variable to cancel ongoing asynchronous tasks if the component unmounts or if new effects begin before previous ones complete.
- Return a cleanup function from useEffect to cancel pending requests or timers, ensuring that stale responses do not update state.
- Carefully check that the component is still mounted or that the current request is valid before updating state.
- This approach prevents race conditions when multiple asynchronous operations might overlap.

5. How does the dependency array affect useEffect behavior, and what common pitfalls should developers be aware of?

T- he dependency array tells React when the effect should re-run by specifying the variables the effect depends on.
- Omitting a dependency may lead to stale closures, where the effect uses outdated values.
- Including variables that change frequently may cause the effect to re-run unnecessarily, leading to performance issues or infinite loops.
- Providing an empty dependency array means the effect behaves like componentDidMount, running only once.

6. How can you optimize performance when using multiple useEffect hooks with overlapping dependencies?

- Consider combining related effects into a single useEffect if they share the same dependency array and logic.
- Split the component logically if the overlapping dependencies indicate different responsibilities that can be isolated in separate components.
- Ensure that each useEffect has a precise dependency array to avoid redundant work and to improve code readability and maintainability.
- Properly implement cleanup functions to release resources that may be shared across these effects.
- Use useMemo or useCallback for values or functions used within useEffect to ensure referential stability, minimizing unnecessary re-renders or re-executions.

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

1. What is React Context, and why is it used?

- React Context provides a way to pass data through the component tree without having to pass props manually at every level.
- It is useful for sharing global data such as themes, user information, or localization data that multiple components need to access.
- By using context, you can avoid "prop drilling," which makes your code cleaner and easier to maintain.
- This design is especially beneficial for large-scale applications with deeply nested components.

2. How do you create and use a context with the useContext hook?

- You create a context by calling React.createContext(), which returns a context object that includes both a Provider and a Consumer.
- Wrap your component tree with the Provider, passing the necessary value via the value prop.
- In a child component, call useContext(MyContext) to access the context value directly, without the need for a Consumer component.
- This approach simplifies the way components get their data and avoids extra nesting in your JSX.

3. What are some potential drawbacks or limitations of using React Context, and how can they be mitigated?

- When the context value changes, all consuming components will re-render, which might lead to performance issues if the context holds frequently changing data.
- Overuse of context for managing local state or excessive nesting of Providers can make your code harder to understand and maintain.
- To mitigate these issues, keep the context values as simple as possible and consider using memoization (e.g., React.memo or useMemo) to limit unnecessary re-renders.
- In scenarios where many independent pieces of data are managed, splitting the context into multiple providers might be a better approach.

4. How can you implement dependency injection in React?

Create a Dependency Context:
• Use React.createContext() to create a context that will hold your dependencies (for example, API clients, configuration objects, or services).

Wrap Your Component Tree with a Provider:
• In your main application or in a specific component tree, wrap the children with the context’s Provider.
• Pass the dependencies as the value to the Provider.

Consume Dependencies with useContext:
• In any child component that requires one or more of the injected dependencies, call const dependencies = useContext(DependencyContext).
• This retrieves the dependency values provided, allowing the component to use them without needing to pass props through each level.

Benefits:
• This approach decouples components from the specifics of their dependencies, making it easier to swap them out during testing or for different environments.
• It avoids prop drilling and keeps your component tree clean and maintainable.
• It promotes better modularity, as components focus on their own logic rather than managing dependency passing.

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
