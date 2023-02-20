# Redux Basic

Category: React
First Refrence: What%20is%20Flux%20be0c7496a5b74185a00d18e158b16585.md, Why%20Redux%20(Flux)%20is%20unidirectional%20flow%2066f1abf0d72f41cbbb4d7893334f5df0.md, What%20is%20Redux%20and%20how%20it%20work%206264a1e5c5824fc1aea97490e5d2e1f1.md, What%20are%20the%20core%20principles%20of%20Redux%209705c4911bff47ed8ff8797320dc5891.md, What%20are%20reducers%20in%20Redux%20d2c06321c48140279b0c2ecb8c18cfbb.md, What%20is%20Selector%20in%20Redux%20d2be79d1842448958c9a60e2f7756549.md, What%20is%20Reselect%20and%20how%20does%20it%20work%20223a710264e74f3da47b759829859454.md, How%20many%20components%20are%20in%20Redux%204447162fd7b6469f9402ccd21121f73b.md
Tags: Basic, Concept

## Flux design pattern

![https://facebook.github.io/flux/img/overview/flux-simple-f8-diagram-with-client-action-1300w.png](https://facebook.github.io/flux/img/overview/flux-simple-f8-diagram-with-client-action-1300w.png)

- Flux complements composable view components by utilizing a unidirectional data flow.
- Flux has three major parts: the dispatcher, the stores, and the views.
    - These should not be confused with Model-View-Controller.
1. Assign action a type + provide it to the dispatcher.
    - Action creators are helper methods.
    - Collected into a library that create an action from paramesters.
2. Every action is sent to all stores via the callbacks (reducers) the store register with the dispatcher.
    - The view propagates an action through a central dispatcher, to the various stores that hold the application's data and business logic, which updates all of the views that are affected.
3. After stores update themselves in response to an action, they emit a change event.
4. Controller-views, listen for change events, retrieve the new data from stores and provide the new data to entire of their child views.
    - Controllers in a Flux application are controller-views.

## Concept

![Untitled](Redux%20Basic%2014e53d787a36474fb4a51e579cb09f9c/Untitled.png)

- Redux is a predictable state container for JavaScript apps that behave consistently across environments: client, server, and native environments.
- It is based on the Flux design pattern.
- There is a central store that holds the entire state of the application. Each component can access the stored state without having to send down props from one component to another.
- There are 3 major components of Redux: Action, Reducer, Store.

```jsx
import { createStore } from 'redux';

// Step 1: Define a reducer
// A pure js function
// that transform the old state to the new one
// based on the action.type
function counter(state = 0, action) {
	switch (action.type) {
		case 'INCREMENT':
			return state + 1
		case 'DECREMENT':
			return state - 1
		default:
			return state
	}
}

// Step 2: Init your store with the reducer
let store = createStore(counter)

// store API is { subscribe, dispatch, getState }.

// Step 3: Subscribe to state changes to update UI
store.subscribe(() => console.log(store.getState()));

// Step 4: Dispatch action to update redux state
// The only way to mutate the internal state is to dispatch an action.
store.dispatch({ type: 'INCREMENT' }) // 1
store.dispatch({ type: 'INCREMENT' }) // 2
store.dispatch({ type: 'DECREMENT' }) // 1
```

### Actions

- Way to send data from application to Redux store.
- The data can be from user interactions, API calls, or even form submissions.
- Actions are sent using the `store.dispatch()` method.
- Actions are plain JavaScript objects
    - They must have a type property to indicate the type of action to be carried out.
    - They must also have a payload that contains the information that should be worked on by the action.

### ****Reducers****

- Reducers are pure functions that take the current state of an application, perform an action, and return a new state.
- They specify how the state of an application changes in response to an action sent to the store.
- It is based on the `reduce` function in JavaScript, where a single value is calculated from multiple values after a callback function has been carried out.

```jsx
import store from "..."

function reducerA(state, action) {
	switch (action.type) {
		case "STATE_FROM_ANOTHER_REDUCER":
			const rootState = store.getState();
			// access any state from rootState
			return ...
		default:
			return ...		
	}
}
```

### ****Store****

- The store holds the application state.
    - It is highly recommended to keep only one store in any Redux application.
- Access the state stored, update the state, and register or unregister listeners via helper methods.

## C****ore principles****

### ****Single source of truth****

- The state of whole application is stored in an object tree within a single store.
- The single state tree makes it easier to keep track of changes over time and debug or inspect the application.

### **State is read-only**

- The only way to change the state is to emit an action, an object describing what happened.
- This ensures that neither the views nor the network callbacks will ever write directly to the state.

### **Changes are made with pure functions**

- To specify how the state tree is transformed by actions, you write reducers.
- Reducers are just pure functions that take the previous state and an action as parameters, and return the next state.

## ****Selector****

- Selectors are functions primarily used to encapsulate logic for looking up specific values from state, logic for actually deriving values, and improving performance by avoiding unnecessary recalculations.
- A selector function is any function that accepts the Redux store state (or part of the state) as an argument, and returns data that is based on that state.
    - Recommend prefixing selector function names with the word select combined with a description of the value being selected.

```jsx
function TodoList() {
  // This anonymous arrow function is a selector!
  const todos = useSelector(state => state.todos)
}
```

### **Reselect**

- The Redux ecosystem has traditionally used a library called Reselect to create memoized selector functions.
    - Memoization is a form of caching.
    - It involves tracking inputs to a function, and storing the inputs and the results for later reference.
    - If a function is called with the same inputs as before, the function can skip doing the actual work, and return the same result it generated the last time it received those input values.
- Reselect provides a function called `createSelector` to generate memoized selectors.
    - `createSelector` accepts one or more "input selector" functions, plus an "output selector" function, and returns a new selector function for you to use.

```jsx
const state = {
  a: {
    first: 5
  },
  b: 10
}

const selectA = state => state.a
const selectB = state => state.b

const selectA1 = createSelector([selectA], a => a.first)

const selectResult = createSelector([selectA1, selectB], (a1, b) => {
  console.log('Output selector running')
  return a1 + b
})

const result = selectResult(state)
// Log: "Output selector running"
console.log(result)
// 15

const secondResult = selectResult(state)
// No log output
console.log(secondResult)
// 15
```

---