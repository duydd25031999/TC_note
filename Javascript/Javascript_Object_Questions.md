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

# Javascript Iterator

## Iterator Concept

### iterator-concept-1

**Q:** {Scan} 

[1. {Scan} ](./Javascript_Object_Questions.md#iterator-concept-1)

### iterator-concept-2

**Q:** {Scan} 

[2. {Scan} ](./Javascript_Object_Questions.md#iterator-concept-2)

### iterator-concept-3

**Q:** {Scan} 

[3. {Scan} ](./Javascript_Object_Questions.md#iterator-concept-3)

### iterator-concept-4

**Q:** {Scan} 

[4. {Scan} ](./Javascript_Object_Questions.md#iterator-concept-4)

### iterator-concept-5

**Q:** {Scan} 

[5. {Scan} ](./Javascript_Object_Questions.md#iterator-concept-5)