# Javascript Basic

## Javascript Language

### javascript-language-1

**Q:** What does it mean that JavaScript is loosely-typed, dynamically-typed, and weakly-typed?

- Vietnamese outline:
	- Question: Giải thích ba khái niệm type (loose / dynamic / weak)
	- Answer:
		- Không khai báo kiểu khi tạo biến
	- Nhận kiểu tại runtime, có thể gán lại
	- Tự ép kiểu khi so sánh ➜ cần ===
- English sample answer:
	- Loosely-typed: variables are declared without an explicit type; the engine infers it.
	- Dynamically-typed: the type is decided at runtime, so a variable can hold a number now and a string later.
	- Weakly-typed: mixed-type operations trigger implicit coercion (e.g., 0 == false → true), which is why seasoned developers prefer the strict operators === and !==.

## Javascript datatype

### javascript-datatype-1

**Q:** Differentiate between primitive (primary) types and reference types.

- Vietnamese outline:
	- Question: So sánh primitive vs reference
	- Answer:
		- Primitive: sao chép giá trị, độc lập
		- Reference: sao chép địa chỉ, cùng dữ liệu
- English sample answer:
	- Primitives (string, number, boolean, bigint, symbol, undefined, null) are copied by value—each assignment creates a new slot in memory, so mutating a never changes b.
	- Reference types (object, arrays, functions, etc.) are copied by reference—assigning b = a just copies the pointer; edits through either alias affect the same object.
	- This distinction drives everyday bugs in state management and equality checks.

### javascript-datatype-2

**Q:** List JavaScript’s built-in types and say which are primitives versus the sole reference type.

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

**Q:** Why should you avoid using object wrappers like new String() or new Boolean()?

- Vietnamese outline:
	- Question:	Setback of wrapper objects
	- Answer:
		- Tạo object ➜ typeof “object”
		- So sánh sai, hiệu suất kém
- English sample answer:
	- Wrappers produce objects, not primitives (typeof new String('a') → "object").
	- That breaks strict equality (new Boolean(false) === false // false) and adds unnecessary memory overhead.
	- Use literals ("a", true, 42); reserve wrappers only when you explicitly need boxed behavior—rare in modern code.

## Variable Declaration

### variable-declaration-1

**Q:** Explain hoisting for var and function declarations, and contrast it with let/const block scope.

- Vietnamese outline:
	- Question: Hoisting vs block-scoped
	- Answer:
		- var/function: khai báo nâng lên đầu
		- let/const: TDZ, chỉ trong block
- English sample answer:
	- Hoisting moves the declaration of var variables and named functions to the top of their containing scope, so they exist from line 1 with the value undefined (functions are fully callable).
	- In ES6, let, const, and class are block-scoped
	- They live in a Temporal Dead Zone from the start of the block until the declaration executes—accessing them early throws ReferenceError.
	- Adopting let/const makes lifetimes explicit and avoids subtle bugs from hoisting.

### variable-declaration-2

**Q:** What is the Temporal Dead Zone (TDZ)?

- Vietnamese outline:
	- Question:	TDZ là gì?
	- Answer:
		- Khoảng từ đầu block ➜ dòng khai báo
		- Truy cập ➜ ReferenceError
- English sample answer:
	- The TDZ is the period between entering a block and executing a let / const declaration where the identifier exists syntactically but is inaccessible.
	- Any read/write inside the TDZ triggers an immediate ReferenceError, enforcing “declare-before-use” discipline.

## Javascript Comparison

### javascript-comparison-1

**Q:** Compare == and === in JavaScript. When should each be used?

- Vietnamese outline:
	- Question: So sánh == vs ===
	- Answer:
		- == ép kiểu ➜ tiện nhưng nguy hiểm
		- === so sánh giá trị + kiểu ➜ khuyên dùng
- English sample answer:
	- == performs abstract equality: if the operands differ in type, it applies coercion rules ("1" == 1 → true).
	- === is strict equality: no coercion—both value and type must match.
	- Best practice:
		- Default to ===
		- Reach for == only when you intentionally want coercion, e.g., value == null to match both null and undefined.

### javascript-comparison-2

**Q:** Demonstrate how || and && short-circuit and return operand values, not Booleans.

- Vietnamese outline:
	- Question: Giải thích short-circuit value
	- Answer:
		- || trả về giá trị truthy đầu tiên
		- && trả về giá trị falsy đầu tiên
- English sample answer:
	- In A || B, if A is truthy, JavaScript returns A itself; otherwise it evaluates and returns B.
	- In A && B, if A is falsy, it returns A; otherwise it returns B.

### javascript-comparison-3

**Q:** List all falsy values in JavaScript and explain truthy/falsy evaluation.

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
	- Everything else—including empty object `{}`, empty array `[]`, string "0", and string "false" — is truthy, so conditionals evaluate based on this internal ToBoolean conversion.

### javascript-comparison-4

**Q:** Why do floating-point numbers like 0.1 + 0.2 yield 0.30000000000000004, and how can you round safely?

- Vietnamese outline:
	- Question: Lý do lỗi float & cách xử lý
	- Answer: 
		- IEEE-754 ➜ lưu nhị phân không chính xác
		- Dùng toFixed, Math.round, hoặc libs
- English sample answer:
	- JavaScript numbers follow IEEE-754 double-precision
	- many decimals lack an exact binary representation, so 0.1 + 0.2 stores a tiny error.
	- When you need a clean decimal for UI or finance, round explicitly with Number((0.1+0.2).toFixed(2)), Math.round(x * 100)/100, or a decimal library.

