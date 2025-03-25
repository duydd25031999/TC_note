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

# “history” Object

Category: Javascript
First Source: %E2%80%9Cwindow%20Object%202fd4a2a949334bd4b9622e623a849116.md
Tags: Common, Concept

## `history.back()`

- Same as clicking back in the browser
- To move backward through history

## `history.forward()`

- Same as clicking forward in the browser
- To move forward through history

## `history.go(number)`

- Moving to a specific point in history

```jsx
window.history.go(-1) // same history.back()
window.history.go(1) // same history.forward()

// refreshing the page
window.history.go(0)
window.history.go()
```

## `history.length`

- The number of pages in the history stack

# “location” Object

Category: Javascript
First Source: %E2%80%9Cwindow%20Object%202fd4a2a949334bd4b9622e623a849116.md
Tags: Common, Concept

- The `window.location` object can be used to get the current page address (URL) and to redirect the browser to a new page.

## `location.href`

![Screenshot 2023-02-12 125642.png](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Screenshot_2023-02-12_125642.png)

- Returns the href (URL) of the current page
- Redirect tab hiện tại qua đổi giá trị của `location.href`

```jsx
window.location.href = "https://ExampleURL.com/";
```

## `location.origin`

![Screenshot 2023-02-12 130236.png](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Screenshot_2023-02-12_130236.png)

- Returns a string containing the canonical form of the origin of the specific location.
- Read only

### `location.protocol`

![Screenshot 2023-02-12 130321.png](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Screenshot_2023-02-12_130321.png)

- Returns the web protocol used (http: or https:)

### `location.host`

![Screenshot 2023-02-12 130544.png](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Screenshot_2023-02-12_130544.png)

- A string containing the host, that is the *hostname*, a `':'`, and the *port* of the URL.

`location.hostname` 

![Screenshot 2023-02-12 130659.png](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Screenshot_2023-02-12_130659.png)

- Returns the domain name of the web host

`location.port`

![Screenshot 2023-02-12 130841.png](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Screenshot_2023-02-12_130841.png)

- A string containing the port number of the URL.

## `location.pathname`

![Untitled](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Untitled.png)

- Returns the path and filename of the current page
- A string containing an initial `'/'` followed by the path of the URL, not including the query string or fragment.

## `location.search`

![Untitled](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Untitled%201.png)

- A string containing a `'?'` followed by the parameters or "querystring" of the URL.

## `location.hash`

![Untitled](%E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c/Untitled%202.png)

- A string containing a `'#'` followed by the fragment identifier of the URL.

## Methods

### `location.assign()`

- Loads the resource at the URL provided in parameter.
- Giống đổi giá trị của `location.href` nhưng an toàn hơn
		- Có thể catch exception

### `location.reload()`

- Reloads the current URL, like the `Refresh` button.

`location.replace()`

- Replaces the current resource with the one at the provided URL (redirects to the provided URL).
- The difference from the `assign()` method and setting the `href` property is that after using `replace()` the current page will not be saved in session History, meaning the user won't be able to use the `back` button to navigate to it.

---

- `replace()` thay thế trang hiện tại = url khác nhưng không lưu vào History ⇒ không back lại

### `location.toString()`

- Returns a string containing the whole URL.
- It is a synonym for `location.href`, though it can't be used to modify the value.

# “navigator” Object

## Browser Cookies

- The `cookieEnabled` property returns true if cookies are enabled

## Browser Application Name

- The `appName` property returns the application name of the browser

# “screen” Object

Category: Javascript
First Source: %E2%80%9Cwindow%20Object%202fd4a2a949334bd4b9622e623a849116.md
Tags: Concept, Low

## `screen.width`

- Window Screen Width
- Chiều rộng của màn hình máy tính

## `screen.height`

- Window Screen Height
- Chiều dài của màn hình máy tính

## `screen.availWidth`

- Window Screen Available Width
- Chiều rộng của màn hình máy tính trừ đi các feature có sẵn như Windows Taskbar

## `screen.availHeight`

- Window Screen Available Height
- Chiều dài của màn hình máy tính trừ đi các feature có sẵn như Windows Taskbar

## `screen.colorDepth`

- Window Screen Color Depth
- Số lượng bits để hiện thị 1 màu
- All modern computers use 24 bit or 32 bit hardware for color resolution:
    - 24 bits = 16,777,216 different "True Colors"
    - 32 bits = 4,294,967,296 different "Deep Colors"

## `screen.pixelDepth`

- Window Screen Pixel Depth

# “window" Object

Category: Javascript
First Refrence: %E2%80%9Cscreen%E2%80%9D%20Object%20c02a7381a39d4252a60ddb1db3a540d6.md, %E2%80%9Chistory%E2%80%9D%20Object%205af7d54684e449998aef39fd2d10f762.md, %E2%80%9Cnavigator%E2%80%9D%20Object%20b0fefab7a8f3490f9971dfae91f6f218.md, %E2%80%9Clocation%E2%80%9D%20Object%20a1a6ae97d1664ca89f41fbfbbc5e730c.md
Tags: Common, Concept

- It represents the browser's window.

## Window Size

### `window.innerHeight`

- The inner height of the browser window (in pixels)

### `window.innerWidth`

- The inner width of the browser window (in pixels)

## `window.open()`

- Open a new window

## `window.close()`

- Close the current window

## `window.moveTo()`

- Move the current window

## `window.resizeTo()`

- Resize the current window

# Event listener

Category: Javascript
Tags: Concept, Low

## **Bubbling & Capturing**

- Bubbling (default): Trigger event của child trước mới tới event của parent
- Capturing: Trigger event của parent trước mới tới event của child

```jsx
addEventListener(event, function, useCapture);
useCapture: bool
```

## Event
****preventDefault****

- Prevent default effect, event of tag
- Prevent default sẽ chặn call event khác của chính element đó

```jsx
$modelThumb.on("touchstart", (e) => {
  e.preventDefault(); // => chặn click của $modelThumb
  e.stopPropagation();
  return true;
});
```

### ****stopPropagation****

- Stop trigger event của parent

### ****stopImmediatePropagation****

- Stop trigger event của parent
- Stop các event listener khác của element đó

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

# URL in Javascript

Category: Javascript
First Refrence: How%20do%20you%20decode%20or%20encode%20a%20URL%20in%20JavaScript%2022455304a77d41918fe6dbc501c9c12e.md
Tags: Concept, Low

## `encodeURI` & `decodeURI`

- `encodeURI()` function is used to encode an URL.
    - This function requires a URL string as a parameter and return that encoded string.
- `decodeURI()`function is used to decode an URL.
    - This function requires an encoded URL string as parameter and return that decoded string.

```jsx
let uri = "employeeDetails?name=john&occupation=manager";
let encoded_uri = encodeURI(uri);
let decoded_uri = decodeURI(encoded_uri);
```

---

# **URLSearchParams**

- The **`URLSearchParams`** interface defines utility methods to work with the query string of a URL.
- An object implementing `URLSearchParams` can directly be used in a `for...of` structure to iterate over key/value pairs.

```jsx
for (const [key, value] of mySearchParams) {}
for (const [key, value] of mySearchParams.entries()) {}
```

## Constructor

```jsx
const paramsString = 'q=URLUtils.searchParams&topic=api';
const searchParams = new URLSearchParams(paramsString);
```

- **`URLSearchParams`** chỉ nhận được `paramsString` mà không nhận cả URL

## Methods

### `URLSearchParams.append()`

- Appends a specified key/value pair as a new search parameter.

### `URLSearchParams.delete()`

- Deletes the given search parameter, and its associated value, from the list of all search parameters.

URLSearchParams.entries()
Returns an iterator allowing iteration through all key/value pairs contained in this object in the same order as they appear in the query string.

URLSearchParams.forEach()
Allows iteration through all values contained in this object via a callback function.

URLSearchParams.get()
Returns the first value associated with the given search parameter.

URLSearchParams.getAll()
Returns all the values associated with a given search parameter.

URLSearchParams.has()
Returns a boolean value indicating if such a given parameter exists.

URLSearchParams.keys()
Returns an iterator allowing iteration through all keys of the key/value pairs contained in this object.

URLSearchParams.set()
Sets the value associated with a given search parameter to the given value. If there are several values, the others are deleted.

URLSearchParams.sort()
Sorts all key/value pairs, if any, by their keys.

URLSearchParams.toString()
Returns a string containing a query string suitable for use in a URL.

URLSearchParams.values()
Returns an iterator allowing iteration through all values of the key/value pairs contained in this object.
