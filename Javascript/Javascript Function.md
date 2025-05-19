# Function Concept

## Define function

```jsx
function a() {}
var b = a;
console.log(typeof b); //function
```

[1. {Scan} How many way to define a function in Javascript?](./Javascript_Questions.md/#function-concept-1)

### Function regular declaration

```jsx
function foo() {...}
```

### Function expression

- 💡Function is a reference datatype of Javascript
- Function expression = declare a function as a variable
  - Normally we use the `function` keyword before the function name to define a function in JavaScript.
- **Anonymous Function** is a function that does not have any name associated with it.
  - In anonymous functions, we use only the `function` keyword without the function name.
- An anonymous function is not accessible after its initial creation.
  - It can only be accessed by a variable it is stored in as a functional value.
  - An anonymous function can also have multiple arguments, but only one expression.
- If binding the method directly to a variable, it will be easier to find the implementation and will stop issues with global scope where function names could conflict.

```jsx
var foo = function() {...}
```

### Immediately Invoked Function Expression (IIFE)

[2. {Scan} How to private call a single function?](./Javascript_Questions.md/#function-concept-2)

- Self-invoking function expression.
- Function that runs as soon as it is defined.

```jsx
(function() {...})()
```

## Function prototype

### call()

- The `call()` method invokes a function with a given `this` value and arguments provided one by one
- Return: return of original function

```jsx
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
  console.log(
    greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
  );
}

invite.call(employee1, "Hello", "How are you?"); // Hello John Rodson, How are you?
invite.call(employee2, "Hello", "How are you?"); // Hello Jimmy Baily, How are you?
```

### apply()

[1. {Scan} When to use `apply()` and use `call()`?](./Javascript_Questions.md/#function-concept-3)

- Invokes the function with a given `this` value and allows you to pass arguments as an array.
  - Simmilar with `call()` but arguments as an array
  - Return: return of original function

```jsx
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
  console.log(
    greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
  );
}

invite.apply(employee1, ["Hello", "How are you?"]); // Hello John Rodson, How are you?
invite.apply(employee2, ["Hello", "How are you?"]); // Hello Jimmy Baily, How are you?
```

### bind()

- Bounce a function by a given `this`
  - Returns a new function, allowing to pass arguments like original function.
  - Doesn’t execute it immediately.
- Allow to define `this` object actively.

[2. {Scan} How does the ReactJS framework use `bind()`?](./Javascript_Questions.md/#function-concept-4)

```jsx
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
  console.log(
    greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
  );
}

var inviteEmployee1 = invite.bind(employee1);
var inviteEmployee2 = invite.bind(employee2);
inviteEmployee1("Hello", "How are you?"); // Hello John Rodson, How are you?
inviteEmployee2("Hello", "How are you?"); // Hello Jimmy Baily, How are you?

class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    console.log(this.state);
  }
  render() {
    return <button onClick={this.handleClick}>Click me</button>;
  }
}


class MyComponent extends React.Component {
  handleClick = () => {
    console.log(this.state);
  };
  render() {
    return <button onClick={this.handleClick}>Click me</button>;
  }
}
```

## Arrow function (ES6)

[5. {Scan} How does arrow function replace `bind()`?](./Javascript_Questions.md/#function-concept-5)

- An arrow function is a shorter syntax for a function expression.
- It does not have its own `this` object, `arguments` array, `super`, or `new.target` like normal function.
  - It take the closest `this` object as its `this`.

```jsx
var person = {
  name: "Duy",
  sayHi: function() {
    var self = this;
    setTimeout(function() {
      console.log("Hi, I'm " + self.name);
    }, 1000);
  }
};

person.sayHi(); // Output: Hi, I'm Duy

var person = {
  name: "Duy",
  sayHi: function() {
    setTimeout(() => {
      console.log("Hi, I'm " + this.name);
    }, 1000);
  }
};

person.sayHi(); // Output: Hi, I'm Duy

var a = function(...arg) {...}
var a = (...arg) => {...}

var a = function(...arg) {
    return result
}
var a = (...arg) => result

var adder = {
  base: 1,

  add: function(a) {
    var f = v => v + this.base; // the closest this is adder
    return f(a);
  }
};
console.log(adder.add(1));
```

## Strict mode

[6. {Scan} How to apply block-scope in ES5?](./Javascript_Questions.md/#function-concept-6)

- Strict context prevents certain actions from being taken and throws more exceptions.
- Strict mode eliminates some JavaScript silent errors by changing them to throw errors.
- Strict mode fixes mistakes that make it difficult for JavaScript engines to perform optimizations
  - Strict mode code can sometimes be made to run faster than identical code that’s not strict mode.
- Strict mode prohibits some syntax likely to be defined in future versions of ECMAScript.
- It prevents, or throws errors, when relatively “unsafe” actions are taken (such as gaining access to the global object).
- It disables features that are confusing or poorly thought out.
- Strict mode makes it easier to write “secure” JavaScript.
- strict mode is disallowing the implicit auto-global variable declaration from omitting the var.

----

- strict mode: chế độ nghiêm ngặt
- Sử dụng cho ES5 để biến 1 scope từ hoisting sang block-scope

```jsx
function foo() {
	"use strict";
	// this code is strict mode
	function bar() {
		// this code is strict mode
	}
}
// this code isn't strict mode
```

# Javascript Callback

## Concept

[1. {Scan} What is callback?](./Javascript_Questions.md/#javascript-callback-1)

- A callback is a function passed into another function as an argument.

```jsx
function consoleLogFrom(getMessageCallback) {
  const message = getMessageCallback();
	console.log(message);
}

function sayHelloWorld() {
	return 'hello world';
}

consoleLogFrom(sayHelloWorld); //hello world
```

- This function is `invoked inside the outer function` to complete an action.
  - The other function can call the callback function inside its scope

----

- Callback là function mà truyền vào function khác như tham chiếu
- ⚠️ Sự mất kiểm soát ở 1 step ⇒ mất kiểm soát các steps sau
- Nếu không có cách kiểm soát hoàn toàn ⇒ bugs

## Use of Callback

[2. {Scan} Is callback only used for assigning future action?](./Javascript_Questions.md/#javascript-callback-2)

- Callback có rất nhiều tác dụng
- Nhưng có 2 cái được biết đến nhiều nhất

### Assign 1 abstract method - Đăng kí 1 hành động trừu tượng

- Sometimes, we don’t know exactly what the function will do.
  - We just want to say: “do something here.”
  - For example, we pass a callback to a loop or event handler.
- This makes the code flexible for different situations.

----

- 1 hành động trừu tượng, linh hoạt theo hoàn cảnh
- Trừu tượng là mình biết nó tồn tại nhưng nội dung bên trong của nó sẽ thay đổi tùy hoàn cảnh

### Assign 1 future action - Đăng kí 1 hành động sẽ được gọi trong tương lai

- It means `registering` a `pending action` will be executed at the `right time in future`.
- Sometimes we want something to happen later, not now.
  - For example, after waiting for an API or after 3 seconds.
  - We use `setTimeout()` or AJAX, and give it a callback.
- This function will run when the right time comes.

----

- Hành động sẽ được gọi cụ thể tại 1 thời điểm trong tương lai
- Hành động phải phụ thuộc vào 1 hành động khác mà không biết bao giờ xong
- Cái hành động cụ thể trong tương lai có thể do `setTimeout`, `setInterval`
- Hành động phải đợi hành động phía trước không biết bao giờ xong thì trong Jquery có ajax để gọi api

# Continuations

## Sequential Brain

[3. {Scan} How can we run multiple threads in Javascript?](./Javascript_Questions.md/#javascript-callback-3)

- JavaScript runs in one thread, so it cannot do many things at the same time.
- To simulate multitasking, JavaScript switches between small tasks very fast. We `fake multitasking`
  1. we switch back and `forth between two or more tasks` in rapid succession
  2. Simultaneously progressing on each task in `tiny, fast little chunks`
- We do it so `fast` that to the `outside world` it appears as if we're `doing these things in parallel`.

## Callback Hell

[4. {Scan} What is the harm of Callback hell?](./Javascript_Questions.md/#javascript-callback-4)

- Callback Hell is an anti-pattern with multiple nested callbacks which makes code hard to read and debug when dealing with asynchronous logic.
- Callback Hell is that executing order of different callbacks cannot be determined.
  - Easily occurs with nested callbacks or nested async actions.
  - Can’t determine when callback is executed.
- The difficulty of control callback-driven design is the worst (and yet most subtle) problems.
- The most troublesome problem with callbacks is inversion of control leading to a complete breakdown along all those trust lines.

----

- Callback Hell là 1 lỗi coding với việc để callbacks lồng nhau nhiều quá khiến code khó đọc và debug
  - Nhất là khi sử dụng trong logic bất đồng bộ
- Callback Hell khiến khó biết rõ được thứ tự chạy của callback và thời điểm callback được gọi

## Trying to Save Callbacks

[5. {Scan} How to use Callback effectively?](./Javascript_Questions.md/#javascript-callback-5)

- Split callbacks = break into clearly steps in same level, sequence ⇒ pass multiple callback arguments lead to each step.
- Error-first style =  thinking about catching error first then implement case success.
- Call the callback too early
    - Callback is executed before sequential code.
- Call the callback too late (or never)
    - Set timeout = create 1 flag + 1 timeout to make sure not awaiting forever
- Call the callback too few or too many times
- Fail to pass along any necessary environment/parameters
- Swallow any errors/exceptions that may happen
