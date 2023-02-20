# Generators

Category: Javascript
First Refrence: What%20is%20Generator%20function%20806a44bdf1c84d8fb5485f63193b5e01.md, Redux%20Saga%2000b3c8a66d764125847edede170e6603.md
Tags: Common, Concept

# Concept

- A `generator` is a function that **can stop midway** and then continue *from where it stopped.*

<aside>
💡 A `generator` is a function which returns an object on which you can call `next()`

</aside>

- Every invocation of `next()` will return an object of shape

```tsx
type NextReturn = { 
  value: Any,
  done: true|false
}

type GeneratorReturn = {
	next: () => NextReturn
}
```

- The `value`property will contain the value. The `done` property is either `true`
 or `false`.
- When the `done` becomes `true`, the generator stops and won’t generate any more values.
1. `it = foo()` operation does not execute the `*foo()` generator yet
    - It = constructs an iterator that will control its execution
2. The first `it.next()` starts the `*foo()` generator
    - Run code before `yield`
3. `*foo()` pauses at the `yield` statement
4. The final `it.next()` call resumes the `*foo()` generator from where it was paused.

- This `yield` statement is basically asking a question: *`What value should I insert here?`*
    - 1st `next()` can't answer the question.
    - 2nd `next()` call must answer the question posed by the first yield.
    - 1st `next()` return value of `yield`.

## Run-to-Completion

- Once a function starts executing, it runs until it completes, and no other code can interrupt and run in between.

<aside>
💡 Generators don’t behave as Run-to-Completion

</aside>

```jsx
function *foo() {
	x++;
	yield; // pause!
	console.log( "x:", x );
} 

function bar() {
	x++;
}

// construct an iterator `it` to control the generator
var it = foo();
	
// start `foo()` here!
it.next();
x; // 2

bar();
x; // 3
it.next(); // x: 3

function *foo(x) {
	var y = x * (yield);
	return y;
} 

var it = foo(6);

// start `foo(..)`
it.next();

var res = it.next(7);
res.value; // 42

function *foo(x) {
	var y = x * (yield "Hello"); // <-- yield a value!
	return y;
} 

var it = foo(6);
var res = it.next(); // first `next()`, don't pass anything
res.value; // "Hello"
res = it.next(7); // pass `7` to waiting `yield`
res.value; // 42
```

### Multiple Iterators

```jsx
function *foo() {
	var x = yield 2;
	z++;
	var y = yield (x * z);
	console.log( x, y, z );
} 
var z = 1;

var it1 = foo();
var it2 = foo();

var val1 = it1.next().value; // 2 <-- yield 2
var val2 = it2.next().value; // 2 <-- yield 2

val1 = it1.next( val2 * 10 ).value; // 40  <-- x:20, z:2
val2 = it2.next( val1 * 5 ).value; //  600 <-- x:200, z:3

it1.next( val2 / 2 ); // y:300
											// x:20, z:3
it2.next( val1 / 4 ); // y:10
											// x:200 z:13
```