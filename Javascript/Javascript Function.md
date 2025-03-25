# Javascript Function

Category: Javascript
First Refrence: How%20can%20I%20define%20a%20function%20in%20Javascript%20fc9727a412d3434586c283cad2e9fe4a.md, What%20is%20Anonymous%20Function%20When%20is%20it%20used%20c59844a82a6e4110aadef687bc859ea7.md, Are%20Anonymous%20Function%20and%20Closure%20are%20different%20E%204c312e5b5d9a41f99f05aa6dc18eba48.md, What%20is%20the%20difference%20between%20Call,%20Apply%20and%20Bin%20bb4649ce6f814f52a67f7280d2438c8a.md, What%20are%20Lambda%20or%20Arrow%20functions%208dec80f15b934e429bcd47d8d8f20e97.md, Different%20between%20Arrow%20function%20and%20Normal%20functi%2071306ce482254873acb913fc7ab9aa27.md, When%20should%20not%20use%20arrow%20function%20e5a47f7cbad14b4fb08ca14d0838620b.md, What%20is%20Strict%20Mode%20in%20JS%20b64fe24ce85143af9b38df5baface7b6.md, Javascript%20Callback%2079c991ad7fc04f759f177737760962e3.md
Tags: Basic, Concept

- Không cho khai báo biến mà không có var
- Functional reference datatype trong js

```jsx
function a() {}
var b = a;
console.log(typeof b); //function
```

## Define function

### Function regular declaration

```jsx
function foo() {...}
```

### Function expression

<aside>
💡 Function is a Reference Data Type

</aside>

- **Anonymous Function** is a function that does not have any name associated with it.
    - Normally we use the `function` keyword before the function name to define a function in JavaScript.
    - However, in anonymous functions, we use only the `function` keyword without the function name.
- An anonymous function is not accessible after its initial creation.
    - It can only be accessed by a variable it is stored in as a functional value.
    - An anonymous function can also have multiple arguments, but only one expression.
- If binding the method directly to a variable, it will be easier to find the implementation and will stop issues with global scope where function names could conflict.

```jsx
var foo = function() {...}
```

### Immediately Invoked Function Expression (IIFE)

- Self-invoking function expression.
- Function that runs as soon as it is defined.

```jsx
(function() {...})()
```

## Function prototype

### a**pply**

- Invokes the function with a given `this` value and allows you to pass arguments as an array.

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

### call

- The `call()` method invokes a function with a given `this` value and arguments provided one by one

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

### **bind**

- Returns a new function, allowing to pass arguments like original function.
- Doesn’t execute it immediately.
- Allow to define `this` object actively.

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
```

## ****Arrow function (ES6)****

- An arrow function is a shorter syntax for a function expression.
- It does not have its own `this` object, `arguments` array, `super`, or `new.target` like normal function.
    - It take the closest `this` object as its `this`.

```jsx
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

- strict mode: chế độ nghiêm ngặt

---

- Strict context prevents certain actions from being taken and throws more exceptions.
- Strict mode eliminates some JavaScript silent errors by changing them to throw errors.
- Strict mode fixes mistakes that make it difficult for JavaScript engines to perform optimizations
    - Strict mode code can sometimes be made to run faster than identical code that’s not strict mode.
- Strict mode prohibits some syntax likely to be defined in future versions of ECMAScript.
- It prevents, or throws errors, when relatively “unsafe” actions are taken (such as gaining access to the global object).
- It disables features that are confusing or poorly thought out.
- Strict mode makes it easier to write “secure” JavaScript.
- strict mode is disallowing the implicit auto-global variable declaration from omitting the var.

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

---

- **Vocabulary**
    - Essential : thiết yếu

# Javascript Callback

<aside>
⚠️ Sự mất kiểm soát ở 1 step ⇒ mất kiểm soát các steps sau

</aside>

- Nếu không có cách kiểm soát hoàn toàn ⇒ bugs

# Concept

- Callback là function mà truyền vào function khác như tham chiếu

---

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

## Use of Callback

- Callback có rất nhiều tác dụng
- Nhưng có 2 cái được biết đến nhiều nhất

### Đăng kí 1 hành động trừu tượng - 1 abstract action

- 1 hành động trừu tượng, linh hoạt theo hoàn cảnh
- Trừu tượng là mình biết nó tồn tại nhưng nội dung bên trong của nó sẽ thay đổi tùy hoàn cảnh

### Đăng kí 1 hành động sẽ được gọi trong tương lai

- Hành động sẽ được gọi cụ thể tại 1 thời điểm trong tương lai
- Hành động phải đợi hành động phía trước không biết bao giờ xong
- Cái hành động cụ thể trong tương lai có thể do `setTimeout`, `setInterval`
- Hành động phải đợi hành động phía trước không biết bao giờ xong thì trong Jquery có ajax để gọi api

---

- It means `registering` a `pending action` will be executed at the `right time in future`.

# Continuations

## Sequential Brain

- When we `fake multitasking` ⇒  we switch back and `forth between two or more tasks` in rapid succession ⇒ simultaneously progressing on each task in `tiny, fast little chunks`
- We do it so `fast` that to the `outside world` it appears as if we're `doing these things in parallel`.

## Callback Hell

- Callback Hell là 1 lỗi coding với việc để callbacks lồng nhau nhiều quá khiến code khó đọc và debug
    - Nhất là khi sử dụng trong logic bất đồng bộ
- Callback Hell khiến khó biết rõ được thứ tự chạy của callback và thời điểm callback được gọi

---

- Callback Hell is an anti-pattern with multiple nested callbacks which makes code hard to read and debug when dealing with asynchronous logic.
- Callback Hell is that executing order of different callbacks cannot be determined.
    - Easily occurs with nested callbacks or nested async actions.
    - Can’t determine when callback is executed.
- The difficulty of control callback-driven design is the worst (and yet most subtle) problems.
- The most troublesome problem with callbacks is inversion of control leading to a complete breakdown along all those trust lines.

## Trying to Save Callbacks

- Split callbacks = break into clearly steps in same level, sequence ⇒ pass multiple callback arguments lead to each step.
- Error-first style =  thinking about catching error first then implement case success.
- Call the callback too early
    - Callback is executed before sequential code.
- Call the callback too late (or never)
    - Set timeout = create 1 flag + 1 timeout to make sure not awaiting forever
- Call the callback too few or too many times
- Fail to pass along any necessary environment/parameters
- Swallow any errors/exceptions that may happen

---

- **Vocabulary**
    - inversion: đảo ngược