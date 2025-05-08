# Javascript Language

- At the beginning, Javascript had been the programming language only for interaction on website
- After NodeJS was released, Javascript have been used for  multiplatform like backend, mobile, window app, etc 

-----

- JavaScript là ngôn ngữ lập trình được sử dụng để tạo trang web tương tác.  
- Sau này do sự phát triển của NodeJS thì Javascript có thể dùng cho multiplatform như backend, mobile, window app, etc 

### Questions

[1. {Interrogate} What does it mean that JavaScript is loosely-typed, dynamically-typed, and weakly-typed?](./Javascript_Questions.md#javascript-language-1)

## Loosely typed (language without declared types)

- Variables are created with `var / let / const` without specifying a type; the engine infers it from the value
- The same variable can later store a value of a different type (e.g., number → string)

----

- Không khai báo cụ thể kiểu biến  
- javascript  
- php  
- ruby  
- python  

## Dynamically typed (runtime typing)

- A variable’s type is determined at runtime, not at compile-time
- You can reassign a variable to any other type during execution

------

- Ngôn ngữ có kiểu dữ liệu được nhận biết trong quá trình runtime.  
- 1 biến có thể được gán cho bất kì loại kiểu biến nào  

## Weakly typed (implicit coercion)

- When an operation mixes types, JavaScript automatically coerces values to a common type
  - Example: `0 == false → true` because 0 is coerced to false
- Use strict operators (===, !==) to avoid unintended coercion effects

------

- Kiểu dữ liệu có thể được suy ra từ một kiểu dữ liệu khác.

# Javascript Datatype

### Questions

[1. {Interrogate} Differentiate between primitive (primary) types and reference types.](./Javascript_Questions.md#javascript-datatype-1)

[2. {Interrogate} List JavaScript’s built-in types and say which are primitives versus the sole reference type.](./Javascript_Questions.md#javascript-datatype-2)

[3. {Interrogate} Why should you avoid using object wrappers like new String() or new Boolean()?](./Javascript_Questions.md#javascript-datatype-3)


## Primary - Kiểu nguyên thủy, tham trị

- Each assignment copies the value into a new memory slot, so the variables are independent.
- Example: When assign variable A to variable B, changing the value of variable A does not affect variable B.
- string
- number
- boolean
- bigint
- symbol

---

- 💡 Mỗi lần gán giá trị tham trị sẽ được vào 1 ô nhớ mới
- Nếu gán biến A với biến B có giá trị tham trị

```jsx
A = B
```

- Copy giá trị của B ra ô nhớ mới
- Gán ô nhớ mới đó cho A
- A và B không liên kết với nhau
- A thay đổi thì B không đổi và ngược lại

## Reference - Tham chiếu

- The first assignment allocates a memory cell for the data.
- Later assignments only copy that memory address, so multiple variables point to the same memory cell.
- Mutating the data through one variable is reflected in every variable that shares the reference.
- object
- array
- function
- null
- undefined

---

- 💡 Giá trị tham chiếu sẽ cùng tham chiếu tới cùng 1 ô nhớ với mỗi lần gán
- Gán giá trị tham chiếu lần đầu, tạo ô nhớ mới
- Từ lần gán thứ 2, chỉ là gán địa chỉ ô nhớ tới biến đó
- Nếu gán biến A với biến B có giá trị tham chiếu

```jsx
A = B
```

- A được gán địa chỉ ô nhớ của B
- Giá trị bên trong B thay đổi thì A cũng thay đổi và ngược lại

### Core differences

- Copy semantics: 
  - Primitive → copies the value; 
  - Reference → copies the address.
- Mutation visibility: 
  - Primitive changes stay local
  - Reference changes propagate to all references
- `typeof` check: 
  - Primitives (except null) return their own type string; 
  - Most reference values return "object". 

## Built-in Types

- Original types are always directly recognized by Javascript engine
  - `undefined` - absence of value; uninitialized variables default to it.
  - `null` - intentional “no object” marker; typeof null is the historic quirk "object".
  - `boolean` - only true / false; anything else is coerced when used in logical context.
  - `number` - IEEE-754 double-precision; watch out for NaN, Infinity, and floating-point rounding
    - toFixed: Làm tròn số thập phân
    ```jsx
    var a = 42.59;
    a.toFixed( 0 ); // "43"
    a.toFixed( 1 ); // "42.6"
    a.toFixed( 2 ); // "42.59"
    a.toFixed( 3 ); // "42.590"
    a.toFixed( 4 ); // "42.5900"
    ```
  - `bigint` - ES 2020 extension for integers larger than 2⁵³-1; can’t mix directly with number without explicit conversion
  - `string` - immutable sequences of UTF-16 code units; length counts code units, not full Unicode code points
  - `symbol` - ES 2015 unique, immutable identifiers; commonly used as non-colliding object keys
  - `object` - Single reference type: objects `{}`, arrays `[]`, functions, dates, regexes, maps, sets, errors, etc.
- Other types are known as 1 of Built-in Types by Javascript engine

### Native object wrappers

- `new String()`, `new Number()`, `new Boolean()` create objects, not primitives
  - `typeof new String('a')` → object

- String()
```jsx
var a = new String( "abc" );
typeof a; // "object" ... not "String"
a instanceof String; // true
Object.prototype.toString.call( a ); // "[object String]"

var a = "abc";
var b = new String( a );
var c = Object( a );
typeof a; // "string"
typeof b; // "object"
typeof c; // "object"
b instanceof String; // true
c instanceof String; // true
Object.prototype.toString.call( b ); // "[object String]"
Object.prototype.toString.call( c ); // "[object String]"
```

- Unboxing

```jsx
var a = new String( "abc" );
var b = new Number( 42 );
var c = new Boolean( true );
a.valueOf(); // "abc"
b.valueOf(); // 42
c.valueOf(); // true
```
- Number()
- Boolean()
- Array(): Array contructor
```jsx
var a = new Array( 1, 2, 3 );
a; // [1, 2, 3]
var b = [1, 2, 3];
b; // [1, 2, 3]

var a = new Array( 3 );  // empty x 3
var b = [ undefined, undefined, undefined ]; // undefind x 3
var c = []; 
c.length = 3; // empty x 3
```
- Symbol(): Symbols are special “unique”
- Utility objects: Date, RegExp, Error, Promise, Function, Object, Proxy, Reflect, JSON, Math.
  - Function()
  - RegExp()
  - Date()
  - Error()
  - Promise()
  - Object()
  - JSON()
  - Math()
  - Reflect()
  - Proxy()

# Variable Declaration

### Questions

[1. {Interrogate} Explain hoisting for var and function declarations, and contrast it with let/const block scope.](./Javascript_Questions.md#variable-declaration-1)

[2. {Interrogate} What is the Temporal Dead Zone (TDZ)?](./Javascript_Questions.md#variable-declaration-2)

## Hoisting — “raise declarations to the top of their scope”

- Applies to var variables and function declarations.
- The declaration is processed first, so code can “see” the identifier anywhere in the same function/global scope.
- The assignment stays where it is, so before that line the identifier holds `undefined`.
- Lets you reference a `var` variable or call a function before its physical declaration.
- Common setback:
  - Unexpected `undefined`
  - Accidental shadowing
  - Harder-to-read control flow.

## Block-scoped bindings (let, const, and class) — “stay exactly where you wrote them”

- Visible only inside the surrounding `{ … }` block (if/for/while, function body, etc.).
- Enter a Temporal Dead Zone (TDZ) from the start of the block until the declaration line
  - Any access inside the TDZ throws a ReferenceError.
- `let` allows reassignment
- `const` doesn't allow reassignment of the binding (the referenced memory address) but the object’s internal state may still mutate.

-----

- Phân biệt let, var, const  
- Hoisting di chuyển tất cả các biến và hàm khi khai báo lên đầu scope trước khi chúng được thực thi.  
  - Nó chỉ di chuyển khai báo, còn việc gán giá trị thì giữ nguyên.  
  - Có thể sử dụng biến trước khi khai báo trong code  
- var là kiểu khai báo biến theo cơ chế hoisting  
- Let, const là khai báo biến theo cơ chế Block-scoped  
  - Vị trí khai báo của biến được giữ nguyên  
  - Không được sử dụng biến trước khi khai báo

# Comparison operator of Javascript

### Questions

[1. {Interrogate} Compare == and === in JavaScript. When should each be used?](./Javascript_Questions.md#javascript-comparison-1)

[2. {Interrogate} Demonstrate how || and && short-circuit and return operand values, not Booleans.](./Javascript_Questions.md#javascript-comparison-2)

[3. {Interrogate} List all falsy values in JavaScript and explain truthy/falsy evaluation.](./Javascript_Questions.md#javascript-comparison-3)

[4. {Interrogate} Why do floating-point numbers like 0.1 + 0.2 yield 0.30000000000000004, and how can you round safely?s](./Javascript_Questions.md#javascript-comparison-4)

## Equal & Non-equal

- `==` là so sánh bằng nhưng có ép type
  - không bằng là `!=`
- `===` là so sánh bằng nhưng ko ép kiểu
  - không bằng là `!==`

```jsx
0 == false   // true
0 === false  // false
1 == "1"     // true
1 === "1"    // false
null == undefined // true
null === undefined // false
'0' == false // true
'0' === false // false
[] == [] or [] === [] //false, refer different objects in memory
{} == {} or {} === {} //false, refer different objects in memory
```

```
- > là lớn hơn
- >= là lớn hơn hoặc bằng
- < là nhỏ hơn
- <= là nhỏ hơn hoặc bằng
```

- 💡 return `boolean`

## Comparing

- nulls to undefineds

```jsx
var a = null;
var b;

a == b; // true
a == null; // true
b == null; // true

a == false; // false
b == false; // false
a == ""; // false
b == ""; // false
a == 0; // false
b == 0; // false
```

- objects to nonobjects

```jsx
var a = 42;
var b = [ 42 ];
a == b; // true

var a = "abc";
var b = Object( a ); // same as `new String( a )`
a === b; // false
a == b; // true
```

## || and &&

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

### Falsy  
- Giá trị mà if nhận là sai  
- 0  
- (- 0)  
- false  
- null  
- undefined  
- “" (length = 0)  
- NaN

### Truthy  
- Giá trị mà if nhận là đúng  
- Tất cả không phải falsy

### `||` operator (ES6: default value)

- `||` return first Truthy

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

### `&&` operator

- `&&` return first Falsy

```jsx
// get the first value in chain

function foo() {
	console.log( a );
}
var a = false;
a && foo(); // false
```

