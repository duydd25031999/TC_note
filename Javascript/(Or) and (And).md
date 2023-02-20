# || and &&

Category: Javascript
First Source: Comparison%20operator%20of%20Javascript%20c6d2ea2b78a74139af60fcc3a63b9221.md
Tags: Basic, Concept

- The result of a `||` or `&&` expression is always the underlying value of one of the operands, not the (possibly coerced) result of the test

```jsx
var a = 42;
var b = "abc";
var c = null;

a || b; // 42
a && b; // "abc"
c || b; // "abc"
c && b; // null
```

- `||` operator (ES6: default value)

```jsx
var a = b || c
// same
if (b) a = b 
else a = c 

function foo(a,b) {
	a = a || "hello";
	b = b || "world";
	console.log( a + " " + b );
}
foo(); // "hello world"
foo( "yeah", "yeah!" ); // "yeah yeah!"
```

- `&&` operator

```jsx
// get the first value in chain

function foo() {
	console.log( a );
}
var a = false;
a && foo(); // false
```