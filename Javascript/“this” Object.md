# “this” Object

Category: Javascript
First Refrence: What%20is%20keyword%20%E2%80%9Cthis%E2%80%9D%20in%20Javacript%201f65f50d21c7419a81b65d12ce34ead7.md, What%20is%20call%20stack%206f38a80b5462420795452c90c5eadc57.md, What%20is%20call-site%20ef730e171e354be6a5a33e7e7d978496.md
Tags: Basic, Concept

**Recall**

- state = values in properties
- Function là 1 reference
- `this` không ref trực tiếp tới function
- Invoke: gọi function
- Implicit: ngầm; ẩn tàng
- Call-site chỉ để đánh dấu để call function, không phải là function 100%
- Call-site thực thi ⇒ call-stack = lục trong stack lấy function tương tứng ⇒ reference
- Khi khởi tạo ⇒ function đã gán context cho this rồi

⇒ Khi gán function vào context khác vẫn không nhận

- Implicit binding = object reference on itself to the function

## Concept

- Function isn’t 1 object.
- `this` is execution context = an activation record created when a function is invoked.
- `this` refers to an object
    - Object method, `this` refers to the object.
    - Alone, `this` refers to the global object (window)
    - In a gloabl function, `this` refers to the global object, but in strict mode, `this` is `undefined`.
    - In an event, `this` refers to the element that received the event.
    - Methods like `call()`, `apply()`, and `bind()` are used to assign `this` object to a function.

```jsx
function foo(num) {
	console.log( "foo: " + num );
	// keep track of how many times `foo` is called
	this.count++;
}

foo.count = 0;

var i;
for (i=0; i<10; i++) {
	if (i > 5) {
		foo( i );
	}
}
// foo: 6
// foo: 7
// foo: 8
// foo: 9
// how many times was `foo` called?
console.log( foo.count ); // 0 -- WTF?
```

## Call stack

- Call Stack is a data structure for Javascript interpreters to keep track of function calls (creates execution context) in the program.
- It follows Last-in First-out.

### Call-Site

The location in code where a function is called.

```jsx
function baz() {
	// call-stack is: `baz`
	// so, our call-site is in the global scope
	console.log( "baz" );
	bar(); // <-- call-site for `bar`
}
function bar() {
	// call-stack is: `baz` -> `bar`
	// so, our call-site is in `baz`
	console.log( "bar" );
	foo(); // <-- call-site for `foo`
}
function foo() {
	// call-stack is: `baz` -> `bar` -> `foo`
	// so, our call-site is in `bar`
	console.log( "foo" );
}
baz(); // <-- call-site for `baz`
```

## Implicit Binding

Whether the call-site has a context object

- An owning or containing object

```jsx
function foo() {
	console.log( this.a );
}
var obj = {
	a: 2,
	foo: foo
};
var a = "oops, global"; // `a` also property on global object
setTimeout( obj.foo, 100 ); // "oops, global"
```

## Explicit Binding

= Use `func.call`, `func.apply` to assign `this` for call-site

- `new` Binding

```jsx
function A(b) {
	this.c = b;
}

// var d = a(1);
// var e = a(2);
// console.log(d, e);

var d = new A(1);

var e = {}
A.apply(e, [2]);
console.log(d, e);
```