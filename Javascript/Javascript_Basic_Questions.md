# Javascript Basic

## Javascript Language

### javascript-language-1

**Q:** {Interrogate} What does it mean that JavaScript is loosely-typed, dynamically-typed, and weakly-typed?

- Vietnamese outline:
	- Question: Giải thích ba khái niệm type (loose / dynamic / weak)
	- Answer:
		- Loosely-typed: Không khai báo kiểu khi tạo biến
		- Dynamically typed: Nhận kiểu tại runtime, có thể gán lại
		- Weakly typed: Tự ép kiểu khi so sánh ➜ cần ===
- English sample answer:
	- Loosely-typed: variables are declared without an explicit type; the engine infers it.
	- Dynamically-typed: the type is decided at runtime, so a variable can hold any type, a number now and a string later.
	- Weakly-typed: mixed-type operations trigger implicit coercion (e.g., 0 == false → true), which is why seasoned developers prefer the strict operators === and !==.

### javascript-language-2

**Q:** {Scan} Why could Javascript not been use for multiplatform?

- English sample answer:
	- Because was designed as the programming language only for interaction on website

### javascript-language-3

**Q:** {Scan} How can developer make sure about Javascript variable datatype?

- Vietnamese outline:
	- 1 biến có thể nhận nhiều kiểu datatype tại mỗi assignment
	- Developer chỉ có thể kiểm tra datatype của variable tại từng thời điểm thông qua 'typeof', 'instanceof'

### javascript-language-4

**Q:** {Scan} What happens when concat numerical value to a string variable?

- English sample answer:
	- Numerical value is coerced to string value then concatted to string variable

### javascript-language-5

**Q:** {Scan} How to compare between string value and numerical value in Javascript?

- English sample answer:
	- Numerical value is coerced to string value then compared to string value

## Javascript Datatype

### javascript-datatype-1

**Q:** {Scan} Differentiate between primitive (primary) types and reference types.

- Vietnamese outline:
	- Question: So sánh primitive vs reference
	- Answer:
		- Primitive: sao chép giá trị, độc lập
		- Reference: sao chép địa chỉ, cùng dữ liệu
- English sample answer:
	- Primitives (string, number, boolean, bigint, symbol, undefined, null) are copied by value-each assignment creates a new slot in memory, so mutating a never changes b.
	- Reference types (object, arrays, functions, etc.) are copied by reference-assigning b = a just copies the pointer; edits through either alias affect the same object.
	- This distinction drives everyday bugs in state management and equality checks.

### javascript-datatype-2

**Q:** {Scan} List JavaScript’s built-in types and say which are primitives versus the sole reference type.

- Vietnamese outline:
	- Question: Liệt kê built-in types
	- Answer:
		- Primitives: 7 + bigint
		- Reference: object
- English sample answer:
	- ECMAScript defines eight built-in types: undefined, null, boolean, number, bigint, string, symbol, and object.
	- The first seven are primitives (passed by value)
	- Object is the only reference type, umbrella for arrays, functions, dates, maps, etc.

### javascript-datatype-3

**Q:** {Interrogate} Why should you avoid using object wrappers like new String() or new Boolean()?

- Vietnamese outline:
	- Question:	Setback of wrapper objects
	- Answer:
		- Tạo object ➜ typeof “object”
		- So sánh sai, hiệu suất kém
- English sample answer:
	- Wrappers produce objects, not primitives (typeof new String('a') → "object").
	- That breaks strict equality (new Boolean(false) === false // false) and adds unnecessary memory overhead.
	- Use literals ("a", true, 42); reserve wrappers only when you explicitly need boxed behavior-rare in modern code.

### javascript-datatype-4

**Q:** {Scan} What are primary datatypes?

- English sample answer: Primary datatypes are
	- string
	- number
	- boolean
	- bigint
	- symbol

### javascript-datatype-5

**Q:** {Scan} What are reference datatypes?

- English sample answer: Reference datatypes are
	- object
	- array
	- function
	- null
	- undefined

### javascript-datatype-6

**Q:** {Scan} Why we need native object wrappers in Javascript?

- Vietnamese outline:
	- Question: Vì sao cần Native Object Wrapper?
	- Answer:
		- Autobox: thêm method cho primitive
		- Kế thừa & mở rộng qua prototype
		- Di sản chuẩn ECMAScript, giữ tương thích
		- Tránh new wrapper ⇢ dễ bug (typeof “object”)
- English sample answer:
	- Primitives have no methods of their own. When you call "abc".toUpperCase(), the engine secretly creates a transient String object wrapper, invokes the method, then discards it. This autoboxing mechanism relies on the built-in constructors String, Number, and Boolean.
	- Wrappers expose a prototype you can extend. If you really must add a cross-cutting helper like String.prototype.repeatSafe, the method lives on the wrapper’s prototype and becomes available to every primitive string through autoboxing.
	- Historical compatibility. Early ECMAScript editions borrowed the idea of object wrappers from Java; removing them now would break legacy code, so the spec continues to keep the constructors.
	- Use with caution. Instantiating wrappers manually (new Boolean(false)) creates an object-typeof returns "object" and strict equality against the corresponding primitive fails, leading to subtle bugs Javascript BasicJavascript Basic. In modern code we rely on implicit boxing for method access and stick to literal primitives for storage and comparison.


## Variable Declaration

### variable-declaration-1

**Q:** {Scan} Explain hoisting for var and function declarations, and contrast it with let/const block scope.

- Vietnamese outline:
	- Question: Hoisting vs block-scoped
	- Answer:
		- var/function: khai báo nâng lên đầu
		- let/const: chỉ trong block, tránh TDZ
- English sample answer:
	- Hoisting moves the declaration of var variables and named functions to the top of their containing scope, so they exist from line 1 with the value undefined (functions are fully callable).
	- In ES6, let, const, and class are block-scoped
	- They live in a Temporal Dead Zone from the start of the block until the declaration executes-accessing them early throws ReferenceError.
	- Adopting let/const makes lifetimes explicit and avoids subtle bugs from hoisting.

### variable-declaration-2

**Q:** {Scan} What is the Temporal Dead Zone (TDZ)?

- Vietnamese outline:
	- Question:	TDZ là gì?
	- Answer:
		- Khoảng từ đầu block ➜ dòng khai báo
		- Truy cập ➜ ReferenceError
- English sample answer:
	- The TDZ is the period between entering a block and executing a let / const declaration where the identifier exists syntactically but is inaccessible.
	- Any read/write inside the TDZ triggers an immediate ReferenceError, enforcing “declare-before-use” discipline.

	
### javascript-declaration-3

**Q:** {Scan} Which JavaScript keywords create block-scoped bindings?

- English sample answer: 
	- `let`, `const`, and `class` are block-scoped

### javascript-declaration-4

**Q:** {Scan} What runtime error do you get a const varaible if you access one before its declaration?

- English sample answer:
	- Any read/write inside the TDZ triggers an immediate ReferenceError, enforcing “declare-before-use” discipline.

## Javascript Comparison

### javascript-comparison-1

**Q:** {Scan} Compare == and === in JavaScript. When should each be used?

- Vietnamese outline:
	- Question: So sánh == vs ===
	- Answer:
		- == ép kiểu ➜ tiện nhưng nguy hiểm
		- === so sánh giá trị + kiểu ➜ khuyên dùng
- English sample answer:
	- == performs abstract equality: if the operands differ in type, it applies coercion rules ("1" == 1 → true).
	- === is strict equality: no coercion-both value and type must match.
	- Best practice:
		- Default to ===
		- Reach for == only when you intentionally want coercion, e.g., value == null to match both null and undefined.

### javascript-comparison-2

**Q:** {Scan} Demonstrate how || and && short-circuit and return operand values, not Booleans.

- Vietnamese outline:
	- Question: Giải thích short-circuit value
	- Answer:
		- || trả về giá trị truthy đầu tiên
		- && trả về giá trị falsy đầu tiên
- English sample answer:
	- In A || B, if A is truthy, JavaScript returns A itself; otherwise it evaluates and returns B.
	- In A && B, if A is falsy, it returns A; otherwise it returns B.

### javascript-comparison-3

**Q:** {Scan} List all falsy values in JavaScript

- Vietnamese outline:
	- Question: Liệt kê falsy
	- Answer: 
		- 0  
		- (- 0)  
		- false  
		- null  
		- undefined  
		- “" (length = 0)  
		- NaN
- English sample answer:
	- JavaScript treats exactly seven values as falsy: false, 0, -0, the empty string "", null, undefined, and NaN.
	- Everything else-including empty object `{}`, empty array `[]`, string "0", and string "false" - is truthy, so conditionals evaluate based on this internal ToBoolean conversion.

### javascript-comparison-4

**Q:** {Interrogate} Why do floating-point numbers like 0.1 + 0.2 yield 0.30000000000000004, and how can you round safely?

- Vietnamese outline:
	- Question: Lý do lỗi float & cách xử lý
	- Answer: 
		- IEEE-754 ➜ lưu nhị phân không chính xác
		- Dùng toFixed, Math.round, hoặc libs
- English sample answer:
	- JavaScript numbers follow IEEE-754 double-precision
	- many decimals lack an exact binary representation, so 0.1 + 0.2 stores a tiny error.
	- When you need a clean decimal for UI or finance, round explicitly with Number((0.1+0.2).toFixed(2)), Math.round(x * 100)/100, or a decimal library.

### javascript-comparison-5

**Q:** {Scan} How can we know a value is truthy

- English sample answer:
	- Every value not falsy is truthy
	- Not seven values as falsy: false, 0, -0, the empty string "", null, undefined, and NaN.

# Javascript Promise

## Promise Concept

### promise-concept-1

**Q:** {Scan} What is promise?

- English sample answer:
	- A promise is an object that may produce a single value some time in the future
	- The future value is either a resolved value or a reason that it’s not resolved
	- Promise is a variable to manage callbacks for asynchronous processing

### promise-concept-2

**Q:** {Scan} How many state does a promise have?

- English sample answer:
	- Promises have three states:
	1. **Pending:** This is an initial state of the Promise while the operation is processing.
	2. **Fulfilled:** This state indicates that the specified operation was completed.
	3. **Rejected:** This state indicates that the operation did not complete. In this case an error value will be thrown.

### promise-concept-3

**Q:** {Scan} What is `p.then()` used for?

- English sample answer:
	- Listen promise response
		- Both resolve & reject of promise
		- 1 promise can assign multiple then
	- Return new promise

### promise-concept-4

**Q:** {Scan} How to execute an action whenever a promise responses?

- English sample answer:
	- `p.finally()` is called whenever promise responses (resolve or reject)

### promise-concept-5

**Q:** {Scan} How to call multiple promises at the same time?

- English sample answer:
	- `Promise.all()`: call multiple promises at the same time then returns a single Promise that resolves to an array of the results of the input promises
	- `Promise.race()`: call multiple promises at the same time then returns a single Promise that resolves to first promise responses
	- `Promise.any()`: call multiple promises at the same time then returns a single Promise that resolves to first promise is fulfilled.
	- Call those promises without `await`: Just call the promise then move to next code line immediately

### promise-concept-6

**Q:** {Scan} How to transform a javascript value into promise?

- English sample answer:
	- `Promise.resolve()` transforms a value to fulfill Promise
	- `Promise.resolve()` transforms a value to rejected Promise

## Async function 

### async-function-1

**Q:** {Scan} How to know a function is async function?

- English sample answer:
	- An async function is a function declared with the `async` keyword
	- The `await` operator is used to wait for a `Promise`.
  	- It can only be used inside an `async` function

### async-function-2

**Q:** {Scan} What is type of async function's return?

- English sample answer:
	- Async function always return Promise

### async-function-3

**Q:** {Scan} What is advantage when using Promise?

- English sample answer:
	- Promise is always asynchrony, romise is to replace `setTimeout(..,0)` hack
	- Nothing (not even a JS error) can prevent a Promise from notifying its resolution (if it's resolved)
	- The Promise will accept only the first resolution

### async-function-4

**Q:** {Interrogate} How does await facilitate working with Promises?

- Vietnamese outline:
	- Question: Cách hoạt động của await
	- Answer:
		- Await dừng execution đến khi Promise settle
		- Cho phép viết code tuần tự, dễ đọc
- English sample answer:
	- The `await` operator pauses execution until the awaited Promise settles (fulfills or rejects), then returns the fulfilled value or throws the rejection reason.
	- This approach transforms Promise chains into linear, try/catch-friendly code, improving readability and maintainability.

# Javascript Function

## Function Concept

### function-concept-1

**Q:** {Scan} How many way to define a function in Javascript?

- Vietnamese Outline:
	- Có 2 cách chính để khai báo function:
	1. Khai báo bình thường với keyword 'function' trước rồi tên hàm
	2. Gán 1 biến với 1 function không tên. Function cũng là 1 datatype của javascript

### function-concept-2

**Q:** {Scan} How to private call a single function?

- English sample answer:
	- Use 'Immediately Invoked Function Expression' approach
	- Call function automatically right after definding it without assigning it to any variable

### function-concept-3

**Q:** {Scan} When to use `apply()` and use `call()`?

- Vietnamese Outline:
	- Cả 2 methods đều dùng được để gán dynamic `this`
	- `call()` dùng cho việc arguments rõ ràng và có thể gọi tuần tự
	- `apply()` chuyên sử dụng với mảng, có thể thay thế cho `forEach` 

### function-concept-4

**Q:** {Scan} How does the ReactJS framework use `bind()`?

- Vietnamese Outline:
	- Question:
		- Tại sao phải dùng `bind()` trong React class components?
		- `bind()` thực hiện gì với this?
	- Answer:
		- Phương thức class không tự động bind this.
		- Gọi `this.method = this.method.bind(this)` trong constructor để gắn this cho instance.
		- Bind trực tiếp trong JSX `(onClick={this.handleClick.bind(this)})` tạo hàm mới mỗi lần render.
		- Dùng arrow-function class fields `(handleClick = () => {})` để tránh phải bind thủ công.
- English sample answer:
	- In React class components, methods do not automatically have their this context bound to the component instance.
	- Calling `.bind(this)` on a method returns a new function whose `this` is permanently set to that component, ensuring you can access `this.props`, `this.state`, and other instance members inside the handler.
	- You can also bind inline in JSX `(<button onClick={this.handleClick.bind(this)}>…</button>)`, but that creates a brand-new function on every render, which can hinder performance.

### function-concept-5

**Q:** {Scan} How does arrow function replace `bind()`?

- Vietnamese Outline:
	- Arrow function dùng dynamic `this` như `bind()`
	- Arrow function cụ thể hơn là tự động lấy `this` gần nhất

### function-concept-6

**Q:** {Scan} How to apply block-scope in ES5?

- English sample answer:
	- Use `Strict mode` inside a scope (a file or {})
	- Scope apply block-scope instead of hoisting

### function-concept-7

**Q:** {Interrogate} What are the key differences between function declaration and function expression in JavaScript?

- Vietnamese Outline:
	- Declaration: có tên, hoisting được
	- Expression: không tên (anonymous), gán vào biến, không hoisting
	- Dùng expression khi cần kiểm soát phạm vi, callback
- English Sample Answer:
	- A function declaration uses the function keyword and is hoisted, meaning it can be called before it is defined.
	- A fuction expression is assigned to a variable and is not hoisted—you can only call it after the line where it is defined.
	- Function expressions can be anonymous and are often used as callbacks or inside closures for better scope control.

## Javascript Callback

### javascript-callback-1

**Q:** {Scan} What is callback?

- English sample answer:
	- A callback is a function passed into another function as an argument.

### javascript-callback-2

**Q:** {Scan} Is callback only used for assigning future action?

- English sample answer:
	- There are many ways to use callback
	- Assigning future action is 1 of them
	- Another way is to Assign 1 abstract method
	- We will know if this method is called but doesn't know exactly logic inside

### javascript-callback-3

**Q:** {Scan} How can we run multiple threads in Javascript?

- English sample answer:
	- To simulate multitasking, JavaScript switches between small tasks very fast.
  1. we switch back and `forth between two or more tasks` in rapid succession
  2. Simultaneously progressing on each task in `tiny, fast little chunks`

### javascript-callback-4

**Q:** {Scan} What is the harm of Callback hell?

- English sample answer:
	- Callback Hell is that executing order of different callbacks cannot be determined.
	- The most troublesome problem with callbacks is inversion of control leading to a complete breakdown along all those trust lines.

### javascript-callback-5

**Q:** {Scan} How to use Callback effectively?

- English sample answer:
	- Split callbacks = break into clearly steps in same level, sequence ⇒ pass multiple callback arguments lead to each step.
	- Error-first style = thinking about catching error first then implement case success.
	- Swallow any errors/exceptions that may happen

### javascript-callback-6

**Q:** {Interrogate} What problems can occur when using nested callbacks, and how do Promises or async/await help fix them?

- Vietnamese Outline:
	- Callback lồng nhau gây khó đọc → callback hell
	- Khó kiểm soát thứ tự chạy & lỗi
	- Promise giúp viết code dạng chain dễ đọc hơn
	- async/await giúp viết giống như code đồng bộ
- English Sample Answer:
	- When we use many nested callbacks, it becomes hard to read and debug. This is called callback hell.
	- We may not know the exact order of execution or where the error happens.
	- Promises let us chain steps more clearly and return new promises for better control.
	- async/await makes asynchronous code look and behave like synchronous code, so it's easier to write and maintain.

# Javascript ES6

## ES6 Basic

### es6-basic-1

**Q:** {Scan} What are new features of ES6 with older version?

- English Sample Answer:
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

### es6-basic-2

**Q:** {Scan} What is Destructuring used for?

- English Sample Answer:
	- Unpack values from arrays, or properties from objects

### es6-basic-3

**Q:** {Scan} What is ellipsis keyword used in ES6?

- English Sample Answer:
	- Ellipsis `...` is used as Spread Syntax or Destructuring

### es6-basic-4

**Q:** {Scan} What is Template literal used for?

- Outline:
	- Multi-line strings
	- Embedded expressions, string interpolation (using ${})

### es6-basic-5

**Q:** {Scan} What is `for ... in` for and `for ... of` for?

- English Sample Answer:
	- `for ... in` is for (Object) values
	- `for ... of` is for (Array) keys

### es6-basic-6

**Q:** {Interrogate} What is advantage of ES6 with ES5?

- Vietnamese Outline:
	- Question: Cải thiện của ES6 với ES5
	- Answers:
		- Cú pháp ngắn gọn, dễ đọc hơn
		- Có block scope (let, const) → an toàn hơn var
		- Hỗ trợ OOP rõ ràng hơn (class, extends)
		- Làm việc với bất đồng bộ dễ hơn (Promise, async/await)
		- Spread / Destructuring giúp code linh hoạt, gọn
		- Hỗ trợ module (import/export) → dễ tổ chức mã nguồn
		- Dễ viết test, maintain, và scale hệ thống
- English Sample Answer:
	- ES6 brings several important advantages compared to ES5.
	1. The syntax is much cleaner and more expressive, making code easier to read and write. For example, arrow functions, template literals, and destructuring help reduce boilerplate.
	2. ES6 introduces block-scoped variables (let and const) which fix many issues caused by var hoisting in ES5.
	3. ES6 adds class syntax and inheritance with extends, making it easier to implement object-oriented design, especially for React components.
	- It also makes asynchronous programming cleaner with Promises and async/await, helping us avoid callback hell.
	- Finally, ES6 supports modules (import / export) so code can be split into reusable files — which is very helpful in large projects.

## ES6 Module

### es6-module-1

**Q:** {Scan} What is `class` in ES6?

- English Sample Answer:
	- `class` is blueprint prototype-based OOP
	- `constructor` is First method called when `new Class()` is used
	- `extends` is for Subclass inherits from parent class
	- `super` calls parent constructor or parent method

### es6-module-2

**Q:** {Scan} What are the keywords about ES6 Module?

- English Sample Answer:
	- `export`: Named exports (can export many per file)
	- `export default`: One default export per file, imported without `{}`
	- `import`: Use to bring in either named or default exports

