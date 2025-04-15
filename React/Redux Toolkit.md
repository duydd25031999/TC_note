# Redux Toolkit

### Questions

[1. How does Redux Toolkit's `configureStore()` simplify store setup compared to Redux’s traditional createStore()?](../Questions.md#redux-toolkit-1)

[2. What are the advantages of using `createReducer()` over writing reducers manually, and how does it leverage Immer?](../Questions.md#redux-toolkit-2)

[3. How does `createAction()` simplify the process of action creation, and what is the significance of its `toString()` method?](../Questions.md#redux-toolkit-3)

[4. Explain the purpose of `createSlice()` in Redux Toolkit. What key properties does it provide, and how does it integrate actions and reducers?](../Questions.md#redux-toolkit-4)

[5. How does Redux Toolkit address the traditional pain points of Redux, such as complex store configuration, multiple packages, and boilerplate code?](../Questions.md#redux-toolkit-5)

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