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

## Javascript datatype

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

# Javascript Object

## Javascript Prototype

### javascript-prototype-1

**Q:** {Scan} What is javascript prototype?

- Vietnamese outline:
	- Là 1 object lưu methods và static properties của 1 constructor hoặc class
	- Được tham chiếu tới toàn bộ instance của onstructor hoặc class
	- Instance cùng chia sẻ chứ không copy, nên dù thế nào các instance đều dùng chung

### javascript-prototype-2

**Q:** {Scan} What is constructor in javascript?

- Vietnamese outline:
	- Constructor là 1 function để định nghĩa instance
	- Contructor chỉ tạo object với keyword `new`

### javascript-prototype-3

**Q:** {Scan} How does "JS Prototype" replace "Class" in OOP like Java?
- Vietnamese outline:
	- Contructor định nghĩa instance
	- Prototype share chung chứ không copy
	- Contructor và Prototype có thể mô phỏng OOP

### javascript-prototype-4

**Q:** {Scan} How to create "stimulates class" with javascript function

- Vietnamese outline:
	1. Tạo 1 contructor
	2. Define prototype của contructor đó

### javascript-prototype-5

**Q:** {Scan} Is return of "person2.sayHello()" same with "person1.sayHello()"

- Vietnamese outline:
	- `sayHello` thực chất là 1 function duy nhất mà 2 object refer tới
	- Có thể return cùng 1 giá trị với cùng input

### javascript-prototype-6

**Q:** {Scan} What is return of those console.log

- English sample answer:
	1. true
	2. false // this belongs to Protoype
	3. false // this belongs to Protoype

### javascript-prototype-7

**Q:** {Scan} How to check an object is instance of a class / function?

- English sample answer:
	- Use keyword `instanceof`

### javascript-prototype-8

**Q:** {Scan} Why is Object Prototype important?

- Vietnamese outline
	- Question: Tại sao `Object.prototype` quan trọng?
	- Answer:
		- Root lookup chain
		- Chứa methods chung (`toString`, `hasOwnProperty`) 
		- Mọi prototype kế thừa nó 
		- Xóa/sửa ⇒ break instanceof, JSON, property access
- English sample answer
	- Top-level node every prototype chain ends at
	- Holds shared utilities: `toString`, `valueOf`, `hasOwnProperty`, etc.
	- One copy in memory → all objects reuse; saves space
	- Deleting or overwriting its methods breaks `instanceof`, `JSON stringify`, and normal property look-ups
	- Replacing `Object.prototype` completely can crash third-party libraries and make core language features unreliable

### javascript-prototype-9

**Q:** {Scan} What is return of this line?

- English sample answer:
```jsx
{
	constructor: SuperHero(),
	sayHello: ƒ(),
	goRage: ƒ()
}
```

### javascript-prototype-10

**Q:** {Scan} When do we use Shallow clone?

- Vietnamese outline:
	- Khi obj/array chỉ có 1-level
	- Vẫn muốn giữ sự ref của children

### javascript-prototype-11

**Q:** {Scan} When do we use Deep clone?

- English sample answer:
	- Totally clone without any connection

### javascript-prototype-12

**Q:** {Scan} Does `returnedTarget` properties refer with `target` properties

- English sample answer:
	- Common properties of `returnedTarget` with `target` still references to `target`

### javascript-prototype-13

**Q:** {Scan} What is different between `assign()` and `create()`

- Vietnamese outline:
	- `assign()`: merge 2 object
	- `create()`: tạo 1 instance khác chung prototype

### javascript-prototype-14

**Q:** {Scan} `create()` is shallow clone or deep clone

- English sample answer:
	- It isn't clone

### javascript-prototype-15

**Q:** {Scan} How to check object has an property or not

- English sample answer:
	- Use `obj.hasOwnProperty()`

### javascript-prototype-16

**Q:** {Scan} Why we need to define property

- Vietnamese outline:
	- Khi cần 1 object với nhiều control đặc biệt

### javascript-prototype-17

**Q:** {Interrogate} Why is storing methods on the constructor’s prototype more memory-efficient than defining them inside the constructor, and when can the extra lookup hurt performance?

- Vietnamese outline
	- Question: Đặt method ở Prototype tốt hơn?
	- Answer:
		- Một bản duy nhất, share cho mọi instance
	- Giảm memory / GC
	- Lookup qua chain
	- Chain sâu → perf drop (edge case)
- English sample answer
	- Prototype holds one copy of each shared method → thousands of instances keep only a tiny reference
	- Less duplication → lower heap use and fewer garbage-collection pauses
	- Modern JIT engines cache prototype lookups, so extra hop is usually O(1)
	- Performance only degrades if prototype chains are unusually deep or the method is called in a tight micro-loop

Inline methods inside the constructor only make sense when each instance truly needs a unique function body

### javascript-prototype-18

**Q:** {Interrogate} Why do developers often use `Object.create(null)` to build “pure dictionary” objects, and what drawbacks should you watch out for?

- Vietnamese outline
	- Question: Vì sao dùng Object.create(null)?
	- Answer:
		- Không kế thừa `Object.prototype` → tránh collision
		- Bảo mật keys `__proto__`, `constructor`
		- Nhược: mất hasOwnProperty, toString, khó debug
		- Một số API (JSON, libs) giả định prototype ⇒ lỗi
- English sample answer:
	- `Object.create(null)` returns an object with no prototype link-its `[[Prototype]]` is null
	- There are zero inherited keys like `toString` or `__proto__`, so you can store arbitrary user-supplied strings without risking prototype-pollution bugs
	- Building a trusted key-value dictionary where keys come from external input.
	- Implementing guards against prototype pollution attacks in server-side JavaScript.
	- Situations where memory isn’t a concern but key safety is paramount.
	- You lose convenience helpers (`obj.hasOwnProperty`, `toString`, `valueOf`)


## Javascript Callback

### javascript-callback-1

**Q:** {Scan} Why can Callback be passed into another function as an argument?

- Vietnamese outline:
	- Function là 1 data type
	- Mỗi function là 1 variable

### javascript-callback-2

**Q:** {Scan} Callback is used only for calling API, isn't it?

- Vietnamese outline:
	- Callback là 1 abtract function
	- Thực hiện đa hình
	- Đăng kí 1 hành động trong tương lai

### javascript-callback-3

**Q:** {Scan} How can we run multitasking in Javascript?

- English sample answer:
1. - When we `fake multitasking`
2. We switch back and `forth between two or more tasks` in rapid succession
- Simultaneously progressing on each task in `tiny, fast little chunks`
- We do it so `fast` that to the `outside world` it appears as if we're `doing these things in parallel`

### javascript-callback-4

**Q:** {Scan} What is callback hell?

- English sample answer:
	- Callback Hell is an anti-pattern with multiple nested callbacks which makes code hard to read and debug when dealing with asynchronous logic.
	- Callback Hell is that executing order of different callbacks cannot be determined.

### javascript-callback-5

**Q:** {Scan} Why does “callback hell” emerge in deeply nested asynchronous code?

- Vietnamese outline:
	- Question: Vì sao callback hell xảy ra với asynchronous code?
	- Answer:
		- Lồng nhiều levels
		- Mất kiểm soát thứ tự & lỗi
		- Logic phân tán
		- Debug khó
- English sample answer
	- Each nested callback hands control to another API → code path splits and indentation grows
	- Error handling scatters across multiple anonymous functions, making stack traces hard to follow
	- Execution order becomes implicit; race conditions sneak in when callbacks fire earlier/later than expected
	- Refactoring is risky because business logic and timing logic are intertwined

### javascript-callback-6

**Q:** {Scan} How to save callback from Callback hell?

- English sample answer:
	- Split callbacks = break into clearly steps in same level, sequence ⇒ pass multiple callback arguments lead to each step.
	- Error-first style = thinking about catching error first then implement case success.
		- Call the callback too early
		- Call the callback too late (or never)
		- Call the callback too few or too many times
		- Fail to pass along any necessary environment/parameters
		- Swallow any errors/exceptions that may happen

### javascript-callback-7

**Q:** {Interrograte} Why do we register a deferred action as a callback (e.g., via setTimeout, AJAX), and what trade-offs does this non-blocking model introduce?

- Vietnamese outline
	- Question: Đăng ký hành động tương lai để làm gì?
	- Answer:
		- Không block thread
		- I/O song song
		- Trade-off: race, timeout, error path
- English sample answer
	- JavaScript runs on a single thread; blocking I/O would freeze the UI
	- Registering a callback lets the engine park the task and keep the event loop free
	- UI stays responsive while network or timer work happens in the background
	- Trade-offs:
		- Must guard against callbacks firing multiple times or never firing (timeouts)
		- Harder to reason about sequencing and shared state → need locks or promise chains
		- Errors propagate outside normal try/catch; you need explicit error channels

## Javascript Map

### javascript-map-1

**Q:** {Scan} What is advantage of Map with Array?

- Vietnamese outline:
	- Dễ tra cứu phức tạp
	- Không sắp xếp theo thứ tự
	- Bộ nhớ cho tập dữ liệu lớn
	- Tính rõ ràng về code

### javascript-map-2

**Q:** {Interrograte} Why would you choose Map over a plain object for a key-value store, and what real impact does that have on large-scale data handling?

- Vietnamese outline
	- Question: Vì sao chọn Map?
	- Answer:
		- Lookup O(1)
		- Key đa dạng
		- Thứ tự chèn
		- Tiết kiệm bộ nhớ
- English sample answer:
	- Hash-table implementation gives average O(1) get/has even with tens of thousands of entries
	- Accepts any value-including objects-as a key without string coercion or prototype pollution risks
	- Maintains insertion order, useful for predictable iteration (LRU caches, config dumps)
	- Memory footprint per entry is lower than storing [key, value] pairs in an object stuffed with hidden classes

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

### function-concept-2

**Q:** {Scan} How to private call a single function?

### function-concept-3

**Q:** {Scan} When to use `apply()` and use `call()`?

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


### function-concept-6

**Q:** {Scan} How to apply block-scope in ES5?

## Javascript Callback

### javascript-callback-1

**Q:** {Scan} What is callback?

### javascript-callback-2

**Q:** {Scan} Is callback only used for assigning future action?

### javascript-callback-3

**Q:** {Scan} How can we run multiple threads in Javascript?

### javascript-callback-4

**Q:** {Scan} What is the harm of Callback hell?

### javascript-callback-5

**Q:** {Scan} How to use Callback effectively?
