# Basic

[1. {Scan} What are new features of ES6 with older version?](./Javascript_Basic_Questions.md/#es6-basic-1)

[6. {Interrogate} What is advantage of ES6 with ES5?](./Javascript_Basic_Questions.md/#es6-basic-6W)

- ES6 is the sixth edition of the javascript language and it was released in June 2015.
1. Support for constants or immutable variables
2. Block-scope support for variables, constants and functions
3. Arrow functions
4. Default parameters
5. Rest and Spread Parameters
6. Template Literals
7. Multi-line Strings
8. Destructuring Assignment
9. Enhanced Object Literals
10. Promises
11. Classes
12. Modules

## Block scoping

[3. {Scan} Which JavaScript keywords create block-scoped bindings?](./Javascript_Basic_Questions.md#javascript-declaration-3)

[4. {Scan} What runtime error do you get if you access one before its declaration?](./Javascript_Basic_Questions.md#javascript-declaration-4)

- Visible only inside the surrounding `{ … }` block (if/for/while, function body, etc.).
- Enter a Temporal Dead Zone (TDZ) from the start of the block until the declaration line
  - Any access inside the TDZ throws a ReferenceError.
- `let` allows reassignment
- `const` doesn't allow reassignment of the binding (the referenced memory address) but the object’s internal state may still mutate.

```jsx
const a = 1;
a = 2 //Error
```

- (!) Const = object = refer tới 1 ô nhớ
    - Không refer được tới ô khác
    - Vẫn có thể thay đổi giá trị properties của object đó

```jsx
const cool = { 
    people: ['you', 'me', 'tesla', 'musk'] 
}
cool.people.push('berners-lee')
console.log(cool) // { people: ['you', 'me', 'tesla', 'musk', 'berners-lee'] }
```

## Destructuring

[2. {Scan} What is Destructuring used for?](./Javascript_Basic_Questions.md/#es6-basic-2)

- Unpack values from arrays, or properties from objects
    - Gỡ giá trị từ array hoặc thuộc tính của object sang các  biến khác nhanh chóng

```jsx
var a, b, rest;
[a, b, ...rest] = [10, 20, 30, 40, 50];
/*
    a = 10
    b = 20
    rest = [30, 40, 50]
*/
var person = {name: "Duy", age: 21}; 
var {name, age} = person;
/*
    name = "Duy"
    age = 21
*/
```

## Spread syntax

[3. {Scan} What is ellipsis used in ES6?](./Javascript_Basic_Questions.md/#es6-basic-3)

- Spread syntax `...` allows an iterable or object to be expanded in places where zero or more elements (for arrays) or key-value pairs (for objects) are expected.
- It’s often used for:
    - Copying
    - Merging
    - Expanding


```jsx
var a, b, rest;
[a, b, ...rest] = [10, 20, 30, 40, 50];
/*
    rest = [30, 40, 50]
*/
function demo(a, b, ...rest) {...}
demo(10, 20, 30, 40, 50);
/*
    rest = [30, 40, 50]
*/
```

- Copy an array

```jsx
var x = [1, 2, 3]
var y = [4, 5, ...x] // [4, 5, 1, 2, 3]
```

- Copy an object

```jsx
var person = {name: "Duy", age: 21}; 
var student = {...person, job: 'student'} //{name: "Duy", age: 21, job: "student"}
```

## Template literal

[4. {Scan} What is Template literal used for?](./Javascript_Basic_Questions.md/#es6-basic-4)

- String formatting using the backtick (`) character

```jsx
`string`
```
- Multi-line strings
    - Lưu cả xuống dòng, tab của string trong code

```jsx
var x = `string 1
        string 2`
/*
"string 1
        string 2"
*/
```

- Embedded expressions, string interpolation (using ${})
    - Truyền biến vào string

```jsx
var x = 'world'
var hello = `hello ${x}` //hello world
```

## ES6 "for" Loop

[5. {Scan} What is `for ... in` for and `for ... of` for?](./Javascript_Basic_Questions.md/#es6-basic-5)

### for ... in

- `for ... in` is for (Object) values

```jsx
var a = ["a","b","c","d","e"];

for (var idx in a) { // Object.values
	console.log( idx ); // a b c d e
}
```

- `for ... of` is for (Array) keys

```jsx
// 0 1 2 3 4
for (var val of a) { // Object.keys
	console.log( val );
}
```

# Module

## class

[1. {Scan} What is `class` in ES6?](./Javascript_Basic_Questions.md/#es6-module-1)

### contructor

- A blueprint over prototypal inheritance
- Used to create objects (instances) with shared behavior.
    - `constructor` is the method that runs when using `new`.
- Methods go outside the constructor.
- All methods defined in class are on the prototype.

```jsx
class Person {
  constructor(name) {
    this.name = name;
  }

  sayHi() {
    console.log(`Hi, I'm ${this.name}`);
  }
}
```

### extends

- Allows one class to inherit from another.
- Subclass gets the parent’s properties and methods.

```jsx
class Student extends Person {
  constructor(name, major) {
    super(name); // Call parent's constructor
    this.major = major;
  }

  sayMajor() {
    console.log(`My major is ${this.major}`);
  }
}
```

### super

- Must call `super()` in the constructor of a subclass before using this.
- Can also be used to call parent methods: `super.sayHi()`.

## export

[2. {Scan} What are the keywords about ES6 Module?](./Javascript_Basic_Questions.md/#es6-module-2)

- Share the variable (method) to outside

```jsx
// utils.js
export const add = (a, b) => a + b;
export const PI = 3.14;

// main.js
import { add, PI } from './utils.js';
```

### export default 

```jsx
// greet.js
export default function greet(name) {
  return `Hello, ${name}`;
}

// main.js
import greet from './greet.js'; // No need for curly braces
```

### import

- Get exported variables

```jsx
// config.js
export const port = 3000;
export default 'my-app';

import appName, { port } from './config.js';
```
