# React Component

- The `main responsibility` of a `Component` is to `translate raw data` into rich `HTML`.
- Component is a `template`. One `blueprint`. A global definition.
    - This can be a `function` or a `class` that defined by developer.
    - When application `running`, it `creates` `instances` of `components` to prevent UI and actions.
- `Instance` is object that React `automatically creates` from `Component` while `running`, `each` with its `own properties` and `local state`.

## React Elements

### Questions

[1. How do React Elements differ from React Components, and what role does each play in the rendering process?](./React_Questions.md#react-elements-1)

[2. In the context of reconciliation, how do React Elements facilitate performance optimizations in React applications?](./React_Questions.md#react-elements-2)

[3. Explain how creating a React Element via JSX or React.createElement contributes to modularity and maintainability.](./React_Questions.md#react-elements-3)

---

- An `element` is a plain object describing a `component instance` or `DOM node` and its desired properties.
    - A React element is an object `representation` of a `DOM node`.
    - An element describing a component is also an element.
        - Just like an element describing the DOM node. They `can` be `nested` and `mixed` with each other.
    - It `created` by React while application is `running`.
    - With a function component, this element is the object that the function returns.
    - With a class component, the element is the object that the component’s `render` function returns.
    - React element is `return` of `React.createElement` function when `compiling JSX`.

## Presentational Component

### Questions

[1. Compare and contrast presentational and container components in a React application. What are the benefits of this separation, and what issues might arise in complex projects?](./React_Questions.md#presentational-component-1)

[2. How do container components manage state and business logic differently from presentational components, and what pitfalls might you encounter if one pattern is overused?](./React_Questions.md#presentational-component-2)

---

- Presentational components are mostly concerned with generating some markup to be outputted.
    - Presentational components are concerned with the look.
    - They just manage state related to the presentation.
- Container components are mostly concerned with operations.
    - Container components are concerned with making things work.
    - They might handle the state of various sub-components.
    - They might wrap several presentational components or container components.
    - They might interface with Redux.

## Fragment

### Questions

[1. Discuss the role of React Fragments in optimizing the UI of presentational components. What advantages do they offer compared to traditional DOM wrappers, and what considerations should be kept in mind?](./React_Questions.md#fragment-1)

---

- Fragments are syntax that allow us to add multiple elements to a React component without wrapping them in an extra DOM node.
- A common pattern is for a component to return a list of children.

## Error Boundaries

- A JavaScript error in a part of the UI shouldn’t break the whole app.
- Error boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of the component tree that crashed.
- Error boundaries catch errors during rendering, in lifecycle methods, and in constructors of the whole tree below them.
- Error boundaries do not catch errors for:
    - Event handlers
    - Asynchronous code
    - Server side rendering
    - Errors thrown in the error boundary itself.
- Error Boundary works only in
    - Class component
    - It must implement `static getDerivedStateFromError()` or `componentDidCatch()`
- Functional Component use package `react-error-boundary`

## Form

- `Uncontrolled component` and `Controlled component` are terms used to describe React components that render HTML form elements.

### Questions

[1. What are the key differences between controlled and uncontrolled components in React, and what are the benefits and trade-offs of each approach?](./React_Questions.md#react-form-1)

[2. How do you decide whether to use controlled or uncontrolled components in a real-world application, and what factors influence this decision?](./React_Questions.md#react-form-2)

[3. Explain how to implement an uncontrolled form component in React using refs, and discuss the limitations of this approach.](./React_Questions.md#react-form-3)

### Controlled Components

- A controlled component is a component that renders form elements and controls them by keeping the form data in the component's state.

```jsx
const { useState } from 'react';

function Controlled () {
  const [email, setEmail] = useState();

  const handleInput = (e) => setEmail(e.target.value);

  return <input type="text" value={email} onChange={handleInput} />;
}
```

### Uncontrolled Components

- An uncontrolled component is a component that renders form elements, where the form element's data is handled by the DOM (default DOM behavior).
- To access the input's DOM node and extract its value you can use a ref.

```jsx
const { useRef } from 'react';

function Example () {
  const inputRef = useRef(null);
  return <input type="text" defaultValue="bar" ref={inputRef} />
}
```

## Props

### Questions

[1. How do you ensure proper validation and type safety of props in a large-scale functional React application, and what are the limitations of using PropTypes compared to solutions like TypeScript?](./React_Questions.md#react-props-1)

[2. How can functional components effectively access and utilize props.children for dynamic content rendering, and what potential pitfalls should be considered?](./React_Questions.md#react-props-2)

[3. How do you optimize functional components with props to prevent unnecessary re-renders, particularly when passing functions or objects as props, and what strategies can be employed?](./React_Questions.md#react-props-3)

[4. How do you handle complex prop structures in functional components to ensure type safety and maintainability?](./React_Questions.md#react-props-4)

### contructor

- `super()` function needs to access some variables of the parent class. It is used to call the constructor of its parent class to access variables.
- `React.Component` will create props based on arguments from its contructor.
- `props` property of class component is inheritance from `React.Component` .
    - If not call `super(props)` ⇒ `React.Component` won’t create `props` property
    - Class component’s `props` will be `undefinded`.

### Children

- `props.children` is a special prop, automatically passed to every component, that can be used to render the content included between the opening and closing tags when invoking a component.
- Can pass any JavaScript expression as children, by enclosing it within `{}`
- Functions as Children.

```jsx
// Calls the children callback numTimes to produce a repeated component
function Repeat(props) {
  let items = [];
  for (let i = 0; i < props.numTimes; i++) {
    items.push(props.children(i));
  }
  return <div>{items}</div>;
}

function ListOfTenThings() {
  return (
    <Repeat numTimes={10}>
      {(index) => <div key={index}>This is item {index} in the list</div>}
    </Repeat>
  );
}
```

### PropTypes

- `React.PropTypes`has moved into a different package since React v15.5.
- Is a library of React to define data type of each props.
- `MyComponent.propTypes` is used for setting up the type checking.
    - The props are checked against the configured type definitions whenever the props are pass to a React Component.
    - A warning pops up on the JavaScript console whenever an invalid value is passed.

```jsx
MyComponent.propTypes = {
  // You can declare that a prop is a specific JS type. By default, these
  // are all optional.
  optionalArray: PropTypes.array,
  optionalBool: PropTypes.bool,
  optionalFunc: PropTypes.func,
  optionalNumber: PropTypes.number,
  optionalObject: PropTypes.object,
  optionalString: PropTypes.string,
  optionalSymbol: PropTypes.symbol,

  // Anything that can be rendered: numbers, strings, elements or an array
  // (or fragment) containing these types.
  optionalNode: PropTypes.node,

  // A React element.
  optionalElement: PropTypes.element,

  // A React element type (ie. MyComponent).
  optionalElementType: PropTypes.elementType,

  // You can also declare that a prop is an instance of a class. This uses
  // JS's instanceof operator.
  optionalMessage: PropTypes.instanceOf(Message),

  // You can ensure that your prop is limited to specific values by treating
  // it as an enum.
  optionalEnum: PropTypes.oneOf(['News', 'Photos']),

  // An object that could be one of many types
  optionalUnion: PropTypes.oneOfType([
    PropTypes.string,
    PropTypes.number,
    PropTypes.instanceOf(Message)
  ]),

  // An array of a certain type
  optionalArrayOf: PropTypes.arrayOf(PropTypes.number),

  // An object with property values of a certain type
  optionalObjectOf: PropTypes.objectOf(PropTypes.number),

  // An object taking on a particular shape
  optionalObjectWithShape: PropTypes.shape({
    color: PropTypes.string,
    fontSize: PropTypes.number
  }),

  // An object with warnings on extra properties
  optionalObjectWithStrictShape: PropTypes.exact({
    name: PropTypes.string,
    quantity: PropTypes.number
  }),   

  // You can chain any of the above with `isRequired` to make sure a warning
  // is shown if the prop isn't provided.
  requiredFunc: PropTypes.func.isRequired,

  // A required value of any data type
  requiredAny: PropTypes.any.isRequired,

  // You can also specify a custom validator. It should return an Error
  // object if the validation fails. Don't `console.warn` or throw, as this
  // won't work inside `oneOfType`.
  customProp: function(props, propName, componentName) {
    if (!/matchme/.test(props[propName])) {
      return new Error(
        'Invalid prop `' + propName + '` supplied to' +
        ' `' + componentName + '`. Validation failed.'
      );
    }
  },

  // You can also supply a custom validator to `arrayOf` and `objectOf`.
  // It should return an Error object if the validation fails. The validator
  // will be called for each key in the array or object. The first two
  // arguments of the validator are the array or object itself, and the
  // current item's key.
  customArrayProp: PropTypes.arrayOf(function(propValue, key, componentName, location, propFullName) {
    if (!/matchme/.test(propValue[key])) {
      return new Error(
        'Invalid prop `' + propFullName + '` supplied to' +
        ' `' + componentName + '`. Validation failed.'
      );
    }
  })
};
```

- Requiring Single Child

```jsx
import PropTypes from 'prop-types';

class MyComponent extends React.Component {
  render() {
    // This must be exactly one element or it will warn.
    const children = this.props.children;
    return (
      <div>
        {children}
      </div>
    );
  }
}

MyComponent.propTypes = {
  children: PropTypes.element.isRequired
};
```

### Default Prop Values

- You can define default values for your `props` by assigning to the special  `defaultProps`  property.

```jsx
class Greeting extends React.Component {
  render() {
    return (
      <h1>Hello, {this.props.name}</h1>
    );
  }
}

// Specifies the default values for props:
Greeting.defaultProps = {
  name: 'Stranger'
};
```

### Render Prop

- Technique for sharing code between React components using a functional props.
- A component with a render prop takes a function that returns React elements and calls it instead of implementing its own render logic.
- Similar to children props with functional type.

```jsx
class Mouse extends React.Component {
  constructor(props) {
    super(props);
    this.handleMouseMove = this.handleMouseMove.bind(this);
    this.state = { x: 0, y: 0 };
  }

  handleMouseMove(event) {
    this.setState({
      x: event.clientX,
      y: event.clientY
    });
  }

  render() {
    return (
      <div style={{ height: '100vh' }} onMouseMove={this.handleMouseMove}>

        {/*
          Instead of providing a static representation of what <Mouse> renders,
          use the `render` prop to dynamically determine what to render.
        */}
				{/* similar to "children" prop that is functional type */}
        {this.props.render(this.state)}
      </div>);
  }
}
```

## Pure Component

### shallowCompare (SC)

- `shallowCompare` performs a shallow equality check on the current `props` and `nextProps` objects as well as the current `state` and `nextState` objects.
- Similar to strict equality operator (===)
- Primitive types
    - A [SC] B returns true if A and B have the same value and are of the same type.
- Complex types
    - A [SC] B returns true if A and B reference the exact same object.

### Concept

- `React.PureComponent` is similar to `React.Component`.
- `React.Component` doesn’t implement `shouldComponentUpdate`
    - A regular component will run rendering whenever props or state is updated. (Even new value is same as old value).
    - A regular component does not implement the `shouldComponentUpdate` method. It always returns true by default, so always trigger re-render.
- `React.PureComponent` implements `shouldComponentUpdate` with a shallow prop and state comparison.
    - Pure Component will (shallowly) compares new value with old value first. If there are different, so component run re-rendering.
- Use `React.PureComponent` when `render()` function renders the same result given the same props and state many times.
- `React.PureComponent`’s `shouldComponentUpdate()` also shallowly compares the objects.
- If these contain complex data structures, it may produce false-negatives for deeper differences.
    - Only extend Pure Component when expect to have simple props and state
    - Or using `forceUpdate()` when know deep data structures have changed.
    - Or using immutable objects to facilitate fast comparisons of nested data.
- Children of Pure Component should be also “pure”.

## Higher-order component

- A higher-order component is a function that takes a component and returns a new component.
- HOCs are common in third-party React libraries.
    - Redux’s `connect`
    - Relay’s `createFragmentContainer`
- A HOC doesn’t modify the input component.
    - Doesn’t use inheritance to copy its behavior.
- Don’t mutate the Original Component.
    - Use its as composition.
    - Return transform of original component.
- A HOC composes the original component by wrapping it in a container component
    - A HOC is a pure function with zero side-effects.
- Don’t Use HOCs inside the `render()` method
- Pass Unrelated Props Through to the Wrapped Component

```jsx
render() {
  // Filter out extra props that are specific to this HOC and shouldn't be
  // passed through
  const { extraProp, ...passThroughProps } = this.props;

  // Inject props into the wrapped component. These are usually state values or
  // instance methods.
  const injectedProp = someStateOrInstanceMethod;

  // Pass props to wrapped component
  return (
    <WrappedComponent
      injectedProp={injectedProp}
      {...passThroughProps}
    />
  );
}
```

```jsx
function getDisplayName(WrappedComponent) {
  return WrappedComponent.displayName || WrappedComponent.name || 'Component';
}
```

### Reuse logic

- A higher-order component (HOC) is an advanced technique in React for reusing component logic.
- We can reuse additional logic like middleware for component.
- Loading component

### Class component

- Don’t Use HOCs inside the `render()` method
- Refs aren’t passed through

```jsx
// This function takes a component...
function withSubscription(WrappedComponent, selectData) {
  // ...and returns another component...
	// Don't extend WrappedComponent => Need to override
  return class extends React.Component {
    constructor(props) {
      super(props);
      this.handleChange = this.handleChange.bind(this);
      this.state = {
        data: selectData(DataSource, props)
      };
    }

    componentDidMount() {
      // ... that takes care of the subscription...
      DataSource.addChangeListener(this.handleChange);
    }

    componentWillUnmount() {
      DataSource.removeChangeListener(this.handleChange);
    }

    handleChange() {
      this.setState({
        data: selectData(DataSource, this.props)
      });
    }

    render() {
      // ... and renders the wrapped component with the fresh data!
      // Notice that we pass through any additional props
			// Just return WrappedComponent with props
			// No need to override any things
      return <WrappedComponent data={this.state.data} {...this.props} />;
    }
  };
}
```

### Functional Component

- With functional component, use `forwardRef` to create wrapper component to forward ref from wrapper component to original component.

```jsx
function highOrderComponent(wrappedComponent, ...otherArgs) {
	// do smt
	return React.forwardRef((props, ref) => <wrappedComponent {...props} ref={ref} />
}
```