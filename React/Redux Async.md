# Redux Async

Category: React
First Refrence: What%20is%20Redux%20Middlewares%208aac6a5369354ee69331febdb79544ce.md, What%20Is%20Redux%20Thunk%20used%20for%20595e1587fa79458f87c6c47fee942072.md, Redux%20Saga%2000b3c8a66d764125847edede170e6603.md
Tags: Basic, Concept

# Redux Middleware

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

# Thunk

- `Thunk` là 1 async middleware để tạo hàm action creator thay vì trả về 1 action
- Action creator này sẽ dispatch action khác khi hoàn thành

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