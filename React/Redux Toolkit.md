# Redux Toolkit

### Questions

1. How does Redux Toolkit's `configureStore()` simplify store setup compared to Redux’s traditional createStore()?

- It automatically sets up Redux DevTools for easier debugging.
- It includes commonly used middleware (e.g., redux-thunk) by default, reducing manual configuration.
- It accepts a single configuration object (e.g., the reducer), which cuts down on boilerplate code.
- It standardizes middleware integration and enhances overall developer experience.

2. What are the advantages of using `createReducer()` over writing reducers manually, and how does it leverage Immer?

- It allows writing code that appears mutative while ensuring state immutability under the hood.
- It simplifies reducer logic by eliminating explicit switch-case statements.
- Immer is used internally to track changes and produce immutable updates automatically.
- This leads to more concise, easier-to-read, and maintainable reducer functions.

3. How does `createAction()` simplify the process of action creation, and what is the significance of its `toString()` method?

- It creates action creator functions that automatically include the specified action type.
- It removes the need for manually defining and managing action type constants.
- The `toString()` method returns the action type, which can be used in reducers for matching actions.
- This improves consistency and simplifies debugging across your Redux code.

4. Explain the purpose of `createSlice()` in Redux Toolkit. What key properties does it provide, and how does it integrate actions and reducers?

- It combines related action creators and reducers into a single slice object.
- Returns a reducer function for the slice, an object with auto-generated action creators, and case reducers.
- Supports “prepare” functions to customize how action payloads are formed.
- This integration reduces boilerplate by consolidating action type definitions, action creators, and reducer logic in one place.

5. How does Redux Toolkit address the traditional pain points of Redux, such as complex store configuration, multiple packages, and boilerplate code?

- It streamlines store setup with configureStore(), requiring less manual configuration and fewer external packages.
- It reduces boilerplate by combining actions and reducers through createSlice().
- It provides built-in support for middleware like redux-thunk, avoiding the need for additional setup.
- Overall, RTK presents an opinionated and simplified API that encourages best practices while improving developer productivity.

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

## createAsyncThunk()

- A function that accepts a Redux action type string and a callback function that should return a promise. 
- It generates promise lifecycle action types based on the action type prefix that you pass in
- Returns a thunk action creator that will run the promise callback and dispatch the lifecycle actions based on the returned promise.

```ts
// First, create the thunk
const fetchUserById = createAsyncThunk(
  'users/fetchByIdStatus',
  async (userId: number, thunkAPI) => {
    const response = await userAPI.fetchById(userId)
    return response.data
  },
)

interface UsersState {
  entities: User[]
  loading: 'idle' | 'pending' | 'succeeded' | 'failed'
}

const initialState = {
  entities: [],
  loading: 'idle',
} satisfies UserState as UsersState

// Then, handle actions in your reducers:
const usersSlice = createSlice({
  name: 'users',
  initialState,
  reducers: {
    // standard reducer logic, with auto-generated action types per reducer
  },
  extraReducers: (builder) => {
    // Add reducers for additional action types here, and handle loading state as needed
    builder.addCase(fetchUserById.fulfilled, (state, action) => {
      // Add user to the state array
      state.entities.push(action.payload)
    })
  },
})

// Later, dispatch the thunk as needed in the app
dispatch(fetchUserById(123))
```