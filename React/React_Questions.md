# React Basic

## Virtual DOM

### virtual-dom-1

**Q:** How would you explain the concept of the Virtual DOM, and why is it a key performance optimization in React?
  - Virtual DOM is like a copy of real DOM that is kept in computer’s memory. 
  - When something changes in the app, React changes this copy first. 
  - Then, it compares the copy with the real web page and updates only the parts that are different. 
  - This makes the update process faster because the real web page does not need to change completely every time. 
  - Because updating the real page can be slow, using the Virtual DOM helps React work quickly and efficiently.

### virtual-dom-2

**Q:** Can you describe in detail how React’s diffing (or reconciliation) algorithm works with the Virtual DOM, and what strategies it employs to minimize updates to the real DOM?
  - Diffing is the process that when something changes, React makes a new Virtual DOM and then looks at both the old and new copies.
  - React finds the differences between the two copies. 
  - After that, it updates only the part of the real DOM that changed. 
  - This way, React does not change the whole page at once, which saves time. 
  - The diffing algorithm groups changes together so it does less work on the real DOM, making the app faster.

### virtual-dom-3

**Q:** In large-scale applications, what potential limitations or bottlenecks might arise from the Virtual DOM mechanism, and what approaches or architectural changes would you recommend to address these issues?

  - In large applications, the Virtual DOM may face some limits. 
  - For example, if there are many components or very complex data, the process of comparing the old Virtual DOM with the new one can take extra time. 
  - This can slow down the update of the page. 
  - To fix this, I would break the application into smaller parts. 
  - I would also use techniques such as memoization (using React.memo) to avoid re-rendering parts that do not change. 
  - In addition, using code splitting and lazy loading can help manage the load on the Virtual DOM. These changes keep the app fast, even when it grows large.

### virtual-dom-4

**Q:** Compare and contrast the Virtual DOM and the Shadow DOM. What are their main differences in purpose and implementation, and in which scenarios would each be most beneficial?
  - Virtual DOM and Shadow DOM are two different ideas. 
  - The Virtual DOM is a lightweight copy of the real DOM that React uses in memory. 
  - It helps to check changes and update only the parts of the page that have changed, which makes the updates faster. 
  - Shadow DOM, however, is a browser feature used to encapsulate a portion of the DOM. 
  - This means that it keeps styles and code separate from the rest of the page. 
  - Virtual DOM is mainly used to improve performance in apps, while Shadow DOM is useful for creating web components that need isolated styles and structure. 
  - In a typical React app, developers usually work with the Virtual DOM, but if you want more control over the styles and encapsulation, the Shadow DOM is very helpful.

## Render function

### render-function-1

**Q:** Explain the role of the render function in a React component and its contribution to the UI update process:

- It is the function that returns the JSX that describes what the component looks like.
- It is called every time the component’s state or props change.
- React uses the returned output to compare the new view with the previous one.
- This comparison lets React update only the parts of the real DOM that have changed.
- This selective updating makes the UI update process faster and more efficient.

### render-function-2

**Q:** How do you ensure that render functions remain pure and free of side effects, and what strategies do you use to improve their performance in large-scale applications?

- I ensure the render function is pure by keeping it focused only on returning JSX.
- I avoid putting any data updates or external function calls inside the render.
- I handle side effects in lifecycle methods or with hooks like useEffect instead.
- I use React.memo or PureComponent to avoid unnecessary re-renders.
- I split large components into smaller ones to maintain clarity and boost performance.

### render-function-3

**Q:** What best practices do you recommend for structuring and maintaining complex render methods to support clarity and performance?

- I break the UI into smaller, reusable components to keep each render simple.
- I organize the code by using helper functions when the JSX becomes too complex.
- I separate components into container components for logic and presentational components for display.
- I make sure that every component’s render function is easy to read and maintain.
- I use optimization techniques like React.memo to improve rendering performance.

## React Lifecycle

### react-lifecycle-1

**Q:** How do you simulate componentDidMount using useEffect?

- By passing an empty dependency array ([]) to useEffect, the effect runs only once after the first render.
- This setup is used to execute initialization code, similar to componentDidMount in class components.

---

### react-lifecycle-2

**Q:** How do you implement a componentDidUpdate-like behavior in a functional component?

- By specifying certain variables in the dependency array of useEffect, you can trigger the effect only when those variables change.
- This mimics componentDidUpdate by running the effect after updates that involve changes to specific state or prop values.

---

### react-lifecycle-3

**Q:** How do you handle cleanup actions (similar to componentWillUnmount) using useEffect?

- You return a cleanup function from the useEffect callback.
- This cleanup function is executed before the next effect runs or when the component unmounts, ensuring proper resource management.

---

### react-lifecycle-4

**Q:** How can multiple useEffect hooks be used together in one functional component?

- You can declare multiple useEffect hooks to separate different concerns (e.g., one for data fetching and one for event listeners).
- This separation makes the component code more organized and easier to maintain.

---

### react-lifecycle-5

**Q:** What happens if you do not provide a dependency array to useEffect?

- The effect will run after every render of the component.
- This may lead to performance issues if the effect is heavy or if it causes unwanted repeated side effects.

---

### react-lifecycle-6

**Q:** How would you simulate getSnapshotBeforeUpdate behavior in a functional component?

- There is no direct equivalent to getSnapshotBeforeUpdate, but you can use useRef to store previous values.
- Combining useRef with useEffect allows you to compare previous and current values after rendering, similar to capturing a snapshot.

---

### react-lifecycle-7

**Q:** What are some potential pitfalls when using multiple useEffect hooks regarding their execution order?

- The execution order of useEffect hooks is determined by their order in the component’s code.
- Unintended side effects can occur if dependencies are not well managed or if the hooks rely on each other’s results.
- Documenting dependencies and keeping effects simple helps avoid issues related to order and unexpected behavior.

---

### react-lifecycle-8

**Q:** In this code, does action 1 or action 2 run first

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

## State

### state-1

**Q:** What is the primary difference between state and props in React?

State:
• Managed locally within a component.
• Mutable and can be updated over time.
• Used to store data that affects the component's behavior and rendering.

Props:
• Passed into a component from a parent.
• Immutable within the component (read-only).
• Used to share data and configuration across components.

---

### state-2

**Q:** How does the useState hook work in a functional component?

- It returns an array with two items: the current state value and a setter function to update that value.
- When the state is updated using the setter, React re-renders the component with the new state.
- It provides a simple way to add and manage state in functional components without using class components.

---

### state-3

**Q:** What is lazy initialization in useState, and when would you use it?

- Lazy initialization involves passing a function to useState rather than a direct value.
- The function is executed only once to compute the initial state on the first render.
- It is beneficial when the computation of the initial state is expensive or time-consuming.

---

### state-4

**Q:** How does React handle state updates when the new state is the same as the current state?

- React compares the new state value with the current state.
- If they are equal, React bails out of the update process and does not trigger a re-render.
- This optimization helps improve performance by avoiding unnecessary renders.

---

### state-5

**Q:** Why should you avoid updating state directly and rely on the setter function provided by useState?

- Direct mutations of state do not trigger a re-render, leading to an inconsistent UI.
- Relying on the setter function ensures that the change is queued and processed correctly by React.
- It maintains the principle of immutability, which is critical for predictable updates and efficient state management.

---

### state-6

**Q:** Compare between "Lazy initial state" and useMemo to transform a prop value into a new variable

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

## useEffect

### use-effect-1

**Q:** What is the role of the useEffect hook in functional components?

- It lets you perform side effects (such as data fetching, subscriptions, or manual DOM updates).
- It acts as a replacement for various lifecycle methods from class components.
- It runs after rendering and can run again if specific dependencies change.

---

### use-effect-2

**Q:** How do you optimize useEffect to run only when necessary?

- Specify a dependency array that includes only the variables that should trigger the effect.
- This practice prevents unnecessary runs of the effect, improving application performance.

---

### use-effect-3

**Q:** What does passing an empty dependency array to useEffect imply?

- It implies that the effect will run only once after the component’s initial render.
- This is ideal for initialization tasks and ensures that the effect does not run on subsequent updates.

---

### use-effect-4

**Q:** How do you manage asynchronous tasks in useEffect and prevent potential race conditions?

- You should define an inner asynchronous function inside or outside the useEffect callback rather than making the callback async.
- Use an AbortController or a flag variable to cancel ongoing asynchronous tasks if the component unmounts or if new effects begin before previous ones complete.
- Return a cleanup function from useEffect to cancel pending requests or timers, ensuring that stale responses do not update state.
- Carefully check that the component is still mounted or that the current request is valid before updating state.
- This approach prevents race conditions when multiple asynchronous operations might overlap.

---

### use-effect-5

**Q:** How does the dependency array affect useEffect behavior, and what common pitfalls should developers be aware of?

- The dependency array tells React when the effect should re-run by specifying the variables the effect depends on.
- Omitting a dependency may lead to stale closures, where the effect uses outdated values.
- Including variables that change frequently may cause the effect to re-run unnecessarily, leading to performance issues or infinite loops.
- Providing an empty dependency array means the effect behaves like componentDidMount, running only once.

---

### use-effect-6

**Q:** How can you optimize performance when using multiple useEffect hooks with overlapping dependencies?

- Consider combining related effects into a single useEffect if they share the same dependency array and logic.
- Split the component logically if the overlapping dependencies indicate different responsibilities that can be isolated in separate components.
- Ensure that each useEffect has a precise dependency array to avoid redundant work and to improve code readability and maintainability.
- Properly implement cleanup functions to release resources that may be shared across these effects.
- Use useMemo or useCallback for values or functions used within useEffect to ensure referential stability, minimizing unnecessary re-renders or re-executions.

## Context

### context-1

**Q:** What is React Context, and why is it used?

- React Context provides a way to pass data through the component tree without having to pass props manually at every level.
- It is useful for sharing global data such as themes, user information, or localization data that multiple components need to access.
- By using context, you can avoid "prop drilling," which makes your code cleaner and easier to maintain.
- This design is especially beneficial for large-scale applications with deeply nested components.

---

### context-2

**Q:** How do you create and use a context with the useContext hook?

- You create a context by calling React.createContext(), which returns a context object that includes both a Provider and a Consumer.
- Wrap your component tree with the Provider, passing the necessary value via the value prop.
- In a child component, call useContext(MyContext) to access the context value directly, without the need for a Consumer component.
- This approach simplifies the way components get their data and avoids extra nesting in your JSX.

---

### context-3

**Q:** What are some potential drawbacks or limitations of using React Context, and how can they be mitigated?

- When the context value changes, all consuming components will re-render, which might lead to performance issues if the context holds frequently changing data.
- Overuse of context for managing local state or excessive nesting of Providers can make your code harder to understand and maintain.
- To mitigate these issues, keep the context values as simple as possible and consider using memoization (e.g., React.memo or useMemo) to limit unnecessary re-renders.
- In scenarios where many independent pieces of data are managed, splitting the context into multiple providers might be a better approach.

---

### context-4

**Q:** How can you implement dependency injection in React?

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

# React Component

## React Element

### react-elements-1

**Q:** How do React Elements differ from React Components, and what role does each play in the rendering process?

- React Elements: Plain objects representing UI; immutable blueprints used during reconciliation.
- React Components: Functions or classes that manage logic and state; they return React Elements.
- Overall: Components generate elements, and React uses these elements to update the DOM efficiently.

---

### react-elements-2

**Q:** In the context of reconciliation, how do React Elements facilitate performance optimizations in React applications?

- Their immutability lets React perform quick shallow comparisons between renders.
- They help identify exactly which parts of the UI need updates.
- Keys in lists further optimize diffing and updating processes.

---

### react-elements-3

**Q:** Explain how creating a React Element via JSX or React.createElement contributes to modularity and maintainability.

- JSX provides a clear, declarative syntax for creating elements, enhancing readability.
- It allows components to be broken into small, reusable pieces.
- This separation leads to more modular, easier-to-maintain code.

---

## Presentational Component

### presentational-component-1

**Q:** Compare and contrast presentational and container components in a React application. What are the benefits of this separation, and what issues might arise in complex projects?

Presentational Components:
• Focus solely on rendering UI and styling.
• Receive data and callbacks via props with minimal or no internal logic.

Container Components:
• Handle business logic, state management, and data fetching.
• Pass necessary data to presentational components as props.

Benefits:
• Separation of concerns enhances reusability, testability, and maintainability.
• Clear distinction makes it easier to isolate UI from logic.

Potential Issues:
• Over-separation may lead to excessive nesting and increased complexity in data flow.
• Prop drilling can occur if data must be passed through many layers.

---

### presentational-component-2

**Q:** How do container components manage state and business logic differently from presentational components, and what pitfalls might you encounter if one pattern is overused?

Container Components:
• Manage state changes, side effects, and communicate with APIs or Redux.
• Encapsulate logic that drives the behavior of presentational components.

Presentational Components:
• Remain stateless (or only manage UI-related state) and focus on rendering.
• Depend on props for data, reducing internal complexity.

Pitfalls:
• Overloading container components can make them hard to maintain and debug.
• Mixing logic in presentational components reduces their reusability and clarity.
• An imbalance may lead to convoluted state management or redundant code.

---

## Fragment

### fragment-1

**Q:** Discuss the role of React Fragments in optimizing the UI of presentational components. What advantages do they offer compared to traditional DOM wrappers, and what considerations should be kept in mind?

Role and Advantages:
• Fragments let components return multiple children without adding an extra DOM node.
• They result in cleaner markup and prevent unnecessary DOM nesting.
• This can improve performance and reduce styling issues often caused by extra wrapper elements.

Considerations:
• Fragments do not support props (except for keys when using the explicit <Fragment key={...}> syntax).
• In some cases, a single container element might be required for CSS layouts or event handling.
• Misuse of fragments can lead to unexpected behavior if layout expectations rely on a specific DOM structure.


---

## React Form

### react-form-1

**Q:** What are the key differences between controlled and uncontrolled components in React, and what are the benefits and trade-offs of each approach?

Controlled Components:
• Form data is stored in React state and updated via onChange events.
• Provides tight control over form behavior, making validation and dynamic updates easier.
• Can lead to more code complexity and potentially slower performance for large or complex forms.

Uncontrolled Components:
• Form data is managed by the DOM, typically accessed via refs.
• Simpler to implement for basic use cases and can be more performant when immediate state tracking isn’t required.
• Harder to implement real-time validation and synchronization with the rest of the application state.

---

### react-form-2

**Q:** How do you decide whether to use controlled or uncontrolled components in a real-world application, and what factors influence this decision?

Nature of the Form:
• Use controlled components when form inputs require immediate validation or dynamic interaction with other parts of the application.
• Consider uncontrolled components for simple or less interactive forms where complex validation isn’t critical.

Performance Considerations:
• Controlled components update state on every keystroke, which might impact performance in highly dynamic or large forms.
• Uncontrolled components keep state in the DOM, reducing the number of state updates and potential re-renders.

Code Maintenance and Consistency:
• Controlled components promote a single source of truth (React state), resulting in predictable data flows.
• Uncontrolled components can reduce boilerplate in simpler scenarios but may diverge from React’s unidirectional data flow pattern.

---

### react-form-3

**Q:** Explain how to implement an uncontrolled form component in React using refs, and discuss the limitations of this approach.

Implementation Using Refs:
• Create a ref using const inputRef = useRef(null).
• Attach the ref to the desired input element via the ref prop (e.g., `<input ref={inputRef} defaultValue="initial value" />`).
• Access the input’s current value using inputRef.current.value when needed (for example, on form submit).

Limitations:
• Data is not managed by React state, making real-time validation or dynamic UI updates more challenging.
• May lead to less predictable behavior since it relies on direct DOM manipulation, which can break the unidirectional data flow of React.
• Harder to integrate with other state-driven parts of the application, potentially resulting in inconsistent form behavior.

---

## React Props

### react-props-1

**Q:** How do you ensure proper validation and type safety of props in a large-scale functional React application, and what are the limitations of using PropTypes compared to solutions like TypeScript?

Using PropTypes:
• Import the "prop-types" package and assign a propTypes object to your component.
• Validate the expected type and structure of each prop at runtime.

Limitations:
• Runtime checking only; errors aren’t caught during compilation.
• Warnings appear in development but are stripped in production builds.

Comparison with TypeScript:
• TypeScript provides static type-checking during development.
• It catches type mismatches at compile-time, improving robustness.
• However, TypeScript requires additional setup and learning curve.

---

### react-props-2

**Q:** How can functional components effectively access and utilize props.children for dynamic content rendering, and what potential pitfalls should be considered?

Effective Usage:
• Use props.children to render nested elements or pass functions as children for dynamic UIs.
• Leverage React.Children utilities to safely iterate and manipulate children elements.

Pitfalls:
• Managing single versus multiple children can lead to unexpected behaviors.
• Forgetting to assign unique keys to children in lists may result in reconciliation issues.
• Over-reliance on children can complicate component APIs if not well documented.

---

### react-props-3

**Q:** How do you optimize functional components with props to prevent unnecessary re-renders, particularly when passing functions or objects as props, and what strategies can be employed?

Identify Re-render Triggers:
• Passing new functions or object literals on every render can trigger re-renders due to changed references.

Optimization Strategies:
• Use React.memo to memoize the component and avoid re-rendering when props remain the same.
• Apply useCallback to memoize functions passed as props.
• Utilize useMemo to cache object values, ensuring referential stability.

Best Practices:
• Carefully structure prop dependencies to minimize changes.
• Profile the component’s performance to identify and address frequent re-renders.

---

### react-props-4

**Q:** How do you handle complex prop structures in functional components to ensure type safety and maintainability?

Prop Validation:
• Use PropTypes to define the expected shape and types of complex props, ensuring runtime validation during development.
• For example, specifying shapes with PropTypes.shape({ key: PropTypes.string }) helps document the structure.

Static Typing with TypeScript:
• Define interfaces or type aliases to enforce the prop structure at compile-time, improving code safety and readability.
• This also helps IDEs provide better autocompletion and error detection.

Destructuring and Default Values:
• Destructure nested props within the component to access only the required data, and provide default values where applicable.
• This reduces clutter and makes the component logic more focused on the necessary details.

Maintainability:
• Clear definitions of prop shapes help other developers understand the component API, reducing bugs and making future refactoring easier.

# Redux Basic

## Redux Concept

### redux-concept-1

**Q:** What is Redux and what problem does it solve?

Single Source of Truth:
• Redux uses one central store that holds the entire state of the application.
• This centralization makes it easier to track state changes over time and simplifies debugging.

Predictable Data Flow:
• With a unidirectional flow (action → reducer → state update), state mutations are predictable.
• It prevents side effects by enforcing state changes only via dispatched actions.

---

### redux-concept-2

**Q:** What are the three core principles of Redux and how do they improve application architecture?

State Immutability:
• Redux expects state to be read-only; changes are made by returning a new state object.
• Immutability ensures that previous states remain unmodified, allowing reliable state snapshots and time travel debugging.

Pure Functions in Reducers:
• Reducers must be pure functions that depend only on their input (current state and action) and produce new state without side effects.
• This guarantees that state transitions are predictable and testable.

Overall Impact:
• These principles lead to consistent application behavior, simplify debugging, and enable performance optimizations such as shallow comparison for update detection.

---

### redux-concept-3

**Q:** How does Redux ensure predictable state management in complex applications?

Actions as Payloads:
• Actions are plain JavaScript objects that must include a type property to indicate the action type.
• They can also include a payload containing additional data.

Reducer Responsibilities:
• Reducers listen for specific action types and return a new state based on the action provided.
• They must be pure functions, ensuring that given the same inputs, the output is always predictable.

Key Requirements for Actions:
• Consistency: Every action should have a clearly defined type.
• Predictability: Actions must not contain side effects; they just signal what change should occur.

Interplay:
• When an action is dispatched, all reducers receive it; each determines if and how the state should change, resulting in a coherent state update.

---

## Redux Async

### redux-async-1

**Q:** How does Redux handle asynchronous actions using middleware such as redux-thunk?

Redux Thunk:
• Redux Thunk is a specific middleware that lets action creators return functions (thunks) instead of plain action objects.
• Thunks receive dispatch (and optionally getState), enabling asynchronous operations.
• After async work is completed (such as waiting for an API response), thunks can dispatch new actions to update the state.

Overall Benefit:
• This pattern bridges the gap between Redux’s synchronous data flow and the asynchronous nature of real-world operations.

---

### redux-async-2

**Q:** What are the advantages and trade-offs of using redux-thunk compared to redux-saga?

Advantages:
• Simplicity: Thunks allow writing async action creators in a familiar function format.
• Flexibility: You have direct access to dispatch and getState, enabling complex conditional logic.
• Integration: Thunks easily integrate with existing Redux data flow without additional libraries.

Potential Pitfalls:
• Overuse: Relying too heavily on thunks can lead to bloated action creators with mixed logic.
• Testing Complexity: Debugging and testing functions that contain asynchronous code may become more challenging.
• Readability: Complex async flows inside thunks can reduce code clarity if not well organized.

---

### redux-async-3

**Q:** Can you walk through the flow of dispatching an async action and how Redux processes it using middleware?

Middleware Role:
• Middleware functions intercept actions before they reach the reducers, allowing for pre-processing or side-effect management.

Handling Asynchronous Actions:
• Middleware, such as Redux Thunk, allows action creators to return functions (thunks) instead of plain objects.
• These functions can perform async operations (like API calls) and then dispatch further actions based on promise resolutions.

Problems Solved:
• It enables asynchronous workflows in a synchronous Redux data flow.
• Middleware also supports logging, error handling, and transformation of actions, enhancing overall flexibility and debugging capabilities.

## Redux Toolkit

### redux-toolkit-1

**Q:** How does Redux Toolkit's `configureStore()` simplify store setup compared to Redux’s traditional createStore()?

- It automatically sets up Redux DevTools for easier debugging.
- It includes commonly used middleware (e.g., redux-thunk) by default, reducing manual configuration.
- It accepts a single configuration object (e.g., the reducer), which cuts down on boilerplate code.
- It standardizes middleware integration and enhances overall developer experience.

---

### redux-toolkit-2

**Q:** What are the advantages of using `createReducer()` over writing reducers manually, and how does it leverage Immer?

- It allows writing code that appears mutative while ensuring state immutability under the hood.
- It simplifies reducer logic by eliminating explicit switch-case statements.
- Immer is used internally to track changes and produce immutable updates automatically.
- This leads to more concise, easier-to-read, and maintainable reducer functions.

---

### redux-toolkit-3

**Q:** How does `createAction()` simplify the process of action creation, and what is the significance of its `toString()` method?

- It creates action creator functions that automatically include the specified action type.
- It removes the need for manually defining and managing action type constants.
- The `toString()` method returns the action type, which can be used in reducers for matching actions.
- This improves consistency and simplifies debugging across your Redux code.

---

### redux-toolkit-4

**Q:** Explain the purpose of `createSlice()` in Redux Toolkit. What key properties does it provide, and how does it integrate actions and reducers?

- It combines related action creators and reducers into a single slice object.
- Returns a reducer function for the slice, an object with auto-generated action creators, and case reducers.
- Supports “prepare” functions to customize how action payloads are formed.
- This integration reduces boilerplate by consolidating action type definitions, action creators, and reducer logic in one place.

---

### redux-toolkit-5

**Q:** How does Redux Toolkit address the traditional pain points of Redux, such as complex store configuration, multiple packages, and boilerplate code?

- It streamlines store setup with configureStore(), requiring less manual configuration and fewer external packages.
- It reduces boilerplate by combining actions and reducers through createSlice().
- It provides built-in support for middleware like redux-thunk, avoiding the need for additional setup.
- Overall, RTK presents an opinionated and simplified API that encourages best practices while improving developer productivity.
