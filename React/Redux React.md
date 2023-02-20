# Redux React

Category: React
First Refrence: What%20is%20the%20difference%20between%20React%20Context%20and%20R%20d7e4543a574143d5ae6283e10c6fdad6.md, What%20is%20connect%20function%20a90ce8603b524be58f5c8e878f9d963a.md, What%20is%20mapStateToProps%20and%20mapDispatchToProps%201cd63b1ebfd94e30870dea3aa20f903f.md, Redux%20Toolkit%2079b07e3a234f4a6bb62fe45bdfc3a687.md
Tags: Basic, Concept

![redux_saga_flow.gif](Redux%20React%20d737fd6dc5754826bd59180585a688b7/redux_saga_flow.gif)

## Redux & Context

- Redux actually uses React Context to store its state.
    - It does a lot more than simply storing state with a set/get interface as Contexts do.
    - It additionally forces to change state via actions.

| Context | Redux |
| --- | --- |
| It is used to share data. | It is used to manage state. |
| Specifically designed for static data, that is not often refreshed or updated | Works like a charm with both static and dynamic data |
| Changes are made with the Context value. | Changes are made with pure functions i.e. reducers. |
| It is better to use with small applications. | It is perfect for larger applications.  |

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