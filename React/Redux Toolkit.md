# Redux Toolkit

Category: React
First Source: Redux%20React%20d737fd6dc5754826bd59180585a688b7.md
Tags: Common, Concept

## Concept

- RTK is a library that helps me write Redux better, easier and simpler.
- The three problems that underlie RTK:
1. Configuring a Redux store is too complicated.
2. I have to add a lot of packages to get Redux to do anything useful.
3. Redux requires too much boilerplate code.

## configureStore()

- `Redux DevTools` is available
- `redux-thunk` is available to execute asynchronous actions

```jsx
// store.js
import { configureStore } from '@reduxjs/toolkit'
import rootReducer from './reducers'
const store = configureStore({ reducer: rootReducer })
```

## createReducer()

```jsx
const counterReducer = createReducer(
	0, // default state 
	{ // actions map
		increment: (state, action) => state + action.payload,
		decrement: (state, action) => state - action.payload
	}
);
```

## createAction()

```jsx
// No redux toolkit
const INCREMENT = 'counter/increment'
function increment(amount) {
	return {
		type: INCREMENT,
		payload: amount
	}
}
const action = increment(3)
// { type: 'counter/increment', payload: 3 }

// redux toolkit

// Có redux toolkit
const increment = createAction('counter/increment')
const action = increment(3)
// returns { type: 'counter/increment', payload: 3 }

console.log(increment.toString())
	// 'counter/increment'
```

## createSlice()

```jsx
function createSlice({
    // A name, used in action types
    name: string,
    // The initial state for the reducer
    initialState: any,
    // An object of "case reducers". Key names will be used to generate actions.
    reducers: Object<string, ReducerFunction | ReducerAndPrepareObject>
    // A "builder callback" function used to add more reducers, or
    // an additional object of "case reducers", where the keys should be other
    // action types
    extraReducers?:
    | Object<string, ReducerFunction>
    | ((builder: ActionReducerMapBuilder<State>) => void)
})
```

- Create object to manage reducer

```jsx
{
    name : string,
    reducer : ReducerFunction,
    actions : Record<string, ActionCreator>,
    caseReducers: Record<string, CaseReducer>.
    getInitialState: () => State
}
```

Example

```jsx
// example.js
import { createSlice, nanoid } from '@reduxjs/toolkit'

const todosSlice = createSlice({
  name: 'todos',
  initialState: [],
  reducers: {
    addTodo: {
      reducer: (state, action) => {
        state.push(action.payload)
      },
      prepare: (text) => {
        const id = nanoid()
        return { payload: { id, text } }
      },
    },
  },
})
```

---

# Vocabulary

- is available = có sẵn