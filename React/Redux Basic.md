# Redux Basic

## Flux design pattern

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

------

- Flux là một mẫu thiết kế (design pattern) được sử dụng để quản lý dữ liệu trong các ứng dụng React. Nó đảm bảo luồng dữ liệu chỉ đi theo một hướng (unidirectional data flow), giúp ứng dụng dễ theo dõi và bảo trì hơn. Flux bao gồm ba thành phần chính:

1. Dispatcher: Là trung tâm điều phối, nhận các hành động (actions) từ ứng dụng và gửi chúng đến các stores. Ví dụ, khi người dùng nhấn nút "Thêm", Dispatcher sẽ nhận action và thông báo cho các stores.
2. Stores: Là nơi lưu trữ trạng thái (state) của ứng dụng và logic xử lý. Khi nhận được action từ Dispatcher, stores sẽ cập nhật trạng thái và thông báo cho các views để hiển thị dữ liệu mới.
3. Views (selector): Là các thành phần giao diện React, hiển thị dữ liệu từ stores. Khi người dùng tương tác (như nhấn nút), views sẽ gửi actions mới đến Dispatcher, tạo thành một vòng tuần hoàn.

- Flux giúp dữ liệu chảy theo một hướng duy nhất: Action → Dispatcher → Stores → Views, giúp việc debug và quản lý trạng thái trở nên dễ dàng.

## Concept

### Questions

[1. What is Redux and what problem does it solve?](../Questions.md#redux-concept-1)

[2. What are the three core principles of Redux and how do they improve application architecture?](../Questions.md#redux-concept-2)

[3. How does Redux ensure predictable state management in complex applications?](../Questions.md#redux-concept-3)

----

![Untitled](Redux%20Basic%2014e53d787a36474fb4a51e579cb09f9c/Untitled.png)

- Redux is a predictable state container for JavaScript apps that behave consistently across environments: client, server, and native environments.
- It is based on the Flux design pattern.
- There is a central store that holds the entire state of the application. Each component can access the stored state without having to send down props from one component to another.
- There are 3 major components of Redux: Action, Reducer, Store.

----

- Redux là một thư viện quản lý trạng thái được xây dựng dựa trên ý tưởng của Flux, nhưng đơn giản hóa hơn. Khác với Flux (có thể có nhiều stores), Redux chỉ có một store duy nhất chứa toàn bộ trạng thái của ứng dụng. Các thành phần trong ứng dụng có thể truy cập trạng thái từ store mà không cần truyền qua nhiều lớp props.
- Redux là 1 thư viện quản lý state (trạng thái) bên thứ 3 để lưu trữ và truyền state giữa các thành phần trong ứng dụng mà không phải qua nhiều lớp props

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

----

- Là các đối tượng JavaScript mô tả những gì đang xảy ra trong ứng dụng. Một action thường có hai phần:
- type: Loại hành động (ví dụ: 'ADD_TODO').
- payload: Dữ liệu đi kèm (ví dụ: 'Học Redux'). Ví dụ: { type: 'ADD_TODO', payload: 'Học Redux' }.

### ****Reducers****

- Reducers are pure functions that take the current state of an application, perform an action, and return a new state.
- They specify how the state of an application changes in response to an action sent to the store.
- It is based on the `reduce` function in JavaScript, where a single value is calculated from multiple values after a callback function has been carried out.

----

- Là các hàm thuần túy (pure functions) nhận trạng thái hiện tại (state) và một action, sau đó trả về state mới. 
- Reducers không thay đổi trạng thái cũ mà tạo ra một bản sao mới. Ví dụ:

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

----

- Là nơi lưu trữ toàn bộ trạng thái của ứng dụng. Store cung cấp các phương thức:
  - dispatch(action): Gửi một action đến reducer để cập nhật trạng thái.
  - getState(): Lấy trạng thái hiện tại.
  - subscribe(listener): Đăng ký một hàm để theo dõi thay đổi trạng thái.

## Core principles

### Single source of truth

- The state of whole application is stored in an object tree within a single store.
- The single state tree makes it easier to keep track of changes over time and debug or inspect the application.

----

- Single source of truth (Nguồn sự thật duy nhất): Toàn bộ trạng thái của ứng dụng được lưu trong một object tree duy nhất trong store. Điều này giúp dễ dàng theo dõi và debug.

### State is read-only

- The only way to change the state is to emit an action, an object describing what happened.
- This ensures that neither the views nor the network callbacks will ever write directly to the state.

----

- State is read-only (Trạng thái chỉ đọc): Trạng thái không thể thay đổi trực tiếp. Muốn cập nhật trạng thái, bạn phải gửi (dispatch) một action để mô tả thay đổi đó.

### Changes are made with pure functions

- To specify how the state tree is transformed by actions, you write reducers.
- Reducers are just pure functions that take the previous state and an action as parameters, and return the next state.

----

- Changes are made with pure functions (Thay đổi bằng hàm thuần túy): Reducers là các hàm thuần túy, không gây tác dụng phụ (side effects), đảm bảo kết quả luôn dự đoán được dựa trên đầu vào.

## Selector

- Selectors are functions primarily used to encapsulate logic for looking up specific values from state, logic for actually deriving values, and improving performance by avoiding unnecessary recalculations.
- A selector function is any function that accepts the Redux store state (or part of the state) as an argument, and returns data that is based on that state.
    - Recommend prefixing selector function names with the word select combined with a description of the value being selected.

----

- Các hàm dùng để lấy dữ liệu từ store một cách hiệu quả. 
- Thay vì lấy toàn bộ trạng thái, selectors cho phép bạn chỉ lấy những phần dữ liệu cần thiết.

```jsx
function TodoList() {
  // This anonymous arrow function is a selector!
  const todos = useSelector(state => state.todos)
}
```

### Reselect

- The Redux ecosystem has traditionally used a library called Reselect to create memoized selector functions.
    - Memoization is a form of caching.
    - It involves tracking inputs to a function, and storing the inputs and the results for later reference.
    - If a function is called with the same inputs as before, the function can skip doing the actual work, and return the same result it generated the last time it received those input values.
- Reselect provides a function called `createSelector` to generate memoized selectors.
    - `createSelector` accepts one or more "input selector" functions, plus an "output selector" function, and returns a new selector function for you to use.

----

- Là một thư viện hỗ trợ tạo selectors memoized (ghi nhớ kết quả). 
- Điều này có nghĩa là selector chỉ tính toán lại khi dữ liệu đầu vào thay đổi, giúp cải thiện hiệu suất, đặc biệt trong các ứng dụng lớn.

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

# Redux React
![redux_saga_flow.gif](Redux%20React%20d737fd6dc5754826bd59180585a688b7/redux_saga_flow.gif)

## Redux & Context

- Redux actually uses React Context to store its state.
    - It does a lot more than simply storing state with a set/get interface as Contexts do.
    - It additionally forces to change state via actions.

- Redux sử dụng React Context để lưu trữ và chia sẻ trạng thái giữa các thành phần trong ứng dụng. Tuy nhiên, Redux không chỉ đơn thuần là Context mà còn cung cấp cơ chế quản lý trạng thái động thông qua actions và reducers.

| Context | Redux |
| --- | --- |
| It is used to share data. | It is used to manage state. |
| Specifically designed for static data, that is not often refreshed or updated | Works like a charm with both static and dynamic data |
| Changes are made with the Context value. | Changes are made with pure functions i.e. reducers. |
| It is better to use with small applications. | It is perfect for larger applications.  |
| Thích hợp để chia sẻ dữ liệu tĩnh (như theme, ngôn ngữ) giữa các thành phần. | Dùng để quản lý trạng thái phức tạp, thay đổi thường xuyên, cần theo dõi lịch sử hoặc xử lý logic bất đồng bộ.|

## Setup

1. Install package `react-redux` and `redux`

```jsx
npm install --save redux react-redux
```

1. Setup reducers và rootReducer

```jsx
// reducers/hobby.js
const initialState = {
    list: ['Listening to music'],
    selectedId: null,
}

const hobbyReducer = (state = initialState, action) => {
    switch (action.type) {
        case 'ADD_HOBBY': {
            const newList = [...state.list, action.payload];
            return {
                ...state,
                list: newList,
            };
        }
        default:
            return state;
    }
};

export default hobbyReducer;

// reducers/index.js (ROOT)
const rootReducer = combineReducers({
    hobby: hobbyReducer,
})
export default rootReducer;
```

1. Setup redux store

```jsx
// src/store.js
const store = createStore(rootReducer);
export default store;
```

1. Setup Store Provider for the whole app  `src/index.js`

```jsx
const Main = () => (
    <Provider store={store}> // useContext
        <App />
    </Provider>
)
```

## Connector

### connect

- `connect` is a function to create connector, a higher order component.
    - Connector can be reuse to many components need same state from Redux.
- `connect` consists of two functions are called sequentially.
- The first function accepts `mapState` and `mapDispatch` as arguments, and returns a second function, connector.
    - 1st function create connector.
- The second function (connector) accepts the component to be wrapped (higher-order component) and returns a new wrapper component that passes down the props from `mapState` and `mapDispatch`

```jsx
import { connect } from 'react-redux'

const mapState = (state) => ({
  isOn: state.isOn,
})

const mapDispatch = {
  toggleOn: () => ({ type: 'TOGGLE_IS_ON' }),
}

const connector = connect(mapState, mapDispatch)

const MyComponent = (props) => (
  <div style={{ backgroundColor: props.backgroundColor }}>
    <button onClick={props.toggleOn}>
      Toggle is {props.isOn ? 'ON' : 'OFF'}
    </button>
  </div>
)

export default connector(MyComponent)
```

### mapStateToProps

- It connects redux state to props of react component.
- Is the first argument passed in to `connect`
- `mapStateToProps` is used for selecting the part of the state from the store that the connected component needs.

```jsx
// Todo.js

function mapStateToProps(
    state, 
    ownProps? // access to own props of input component
) {
  const { visibilityFilter } = state
  // ownProps would look like { "id" : 123 }
  const { id } = ownProps
  const todo = getTodoById(state, id)

  // component receives additionally:
  return { todo, visibilityFilter }
}

// Later, in your application, a parent component renders:
<ConnectedTodo id={123} />
// and your component receives props.id, props.todo, and props.visibilityFilter
```

### mapDispatchToProps

- It connects redux actions to props of react comp.
- Is the second argument passed in to `connect`
- `mapDispatchToProps` specifies which actions component might need to dispatch to provide action dispatching functions as props.

```jsx
render() {
  return <button onClick={() => this.props.toggleTodo()} />
}

const mapDispatchToProps = (
    dispatch, 
    ownProps?
) => {
  return {
        addTodo: todo => dispatch(addTodo(todo))
    toggleTodo: () => dispatch(toggleTodo(ownProps.todoId))
  }
}
```

# Redux Async

### Questions

[1. How does Redux handle asynchronous actions using middleware such as redux-thunk?](../Questions.md#redux-async-1)

[2. What are the advantages and trade-offs of using redux-thunk compared to redux-saga?](../Questions.md#redux-async-2)

[3. Can you walk through the flow of dispatching an async action and how Redux processes it using middleware?](../Questions.md#redux-async-3)

## Redux Middleware

- Middleware allows to intercept all actions dispatched from components before they are passed to the reducer function.
- Middlewares are functions that call the next method received in an argument after processing the current action.

---

- Middleware nắm bắt tất cả các actions trước khi dispatch vào reducer
- Khi 1 action đến Middleware ⇒ Chỉ là thông báo cho Middleware rồi chạy tiếp
- Không đợi middleware hoàn thiện => bất đồng bộ
    - Sau khi middleware hoàn thiện => Middleware có thể dispatch 1 actions `KHÁC`
- Lướt qua để thông báo với all middlewares => đi thẳng tới ReducerEffect: chỉ đơn giản là một javascript object có chứa thông tin để saga middleware biết cần phải làm

```jsx
import { createStore, applyMiddleware } from "redux";

function myMiddleware(store) { //currying function
	return function(next) {
		return function(action) {
			const oldState = store.getState();
			
			/*
				Do smt to check action
				Can change value of action
			*/

			next(action);
			const newState = store.getState();

			// return next(action);
		}
	}
}

createStore(rootReducer, applyMiddleware(myMiddleware))
```

### Async Middleware

- Action (1) => Middleware => không truyền đi đâu nữa
- Middleware xử lý xong -> Dispath 1 action (2) khác để cập nhật state

1. Async Middleware nhận actions phù hợp thì gọi 1 async function
2. Xử lý xong promise thì `dispatch 1 action KHÁC` để cập nhật state mới từ `then` của Promise

```jsx
function fetchAction() {
	return async function(dispatch) {
		const res = await ...some api
		dispatch(updateState(res.data));
	}
}

function asyncMiddleware(store) {
	return function(dispatch) {
		return function(payload) {
			if (typeof payload == "fuction") { // payload is async function
				return payload(dispatch);
			} else { // payload is normal action object
				return next(payload);
			}
		}
	}
}

```

## Thunk

- `Thunk` là 1 async middleware để tạo hàm action creator thay vì trả về 1 action
- Action creator này sẽ dispatch action (2) khác khi hoàn thành

---

- Redux Thunk middleware allows to write action creators that return a function instead of an action.
    - With a plain basic Redux store, you can only do simple synchronous updates by dispatching an action.
- `thunks` are a functional programming technique used to delay computation as asynchronous.

```jsx
// in store instantiation module:
import axios from 'axios'

const store = createStore(
  reducer,
  applyMiddleware(thunk.withExtraArgument(axios))
)

// in action creator module:
const thunkedLogin = () =>
  (dispatch, getState, axios) => // thunk now also receives `axios` dep.
    axios.get('/api/auth/me')
    .then(res => res.data)
    .then(user => {
      dispatch(simpleLogin(user))
    })

// somewhere in component:
store.dispatch(thunkedLogin()) // dispatches the thunk to the store.
```

---