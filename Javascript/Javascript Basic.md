# Javascript Language

- JavaScript là ngôn ngữ lập trình được sử dụng để tạo trang web tương tác.  
  - Sau này do sự phát triển của NodeJS thì Javascript có thể dùng cho multiplatform như backend, mobile, window app, etc  
- Loosely typing  
  - Không khai báo cụ thể kiểu biến  
  - javascript  
  - php  
  - ruby  
  - python  
- Dynamically typed  
  - Ngôn ngữ có kiểu dữ liệu được nhận biết trong quá trình runtime.  
  - 1 biến có thể được gán cho bất kì loại kiểu biến nào  
- Weakly typed  
  - Kiểu dữ liệu có thể được suy ra từ một kiểu dữ liệu khác.

# Javascript Datatype

Category: Javascript
First Refrence: Different%20between%20Primary%20&%20Reference%20type%20800b0aed297b4c89873e764cd8953764.md, What%20is%20pass%20by%20reference%20and%20pass%20by%20value%207ac10e8d06494e56b677dd3b12a80f89.md, Are%20primary%20types%20passed%20by%20reference%20or%20passed%20by%202d963303e28a45d2a416129b6c968304.md, How%20to%20check%20a%20variable%20or%20a%20value%20is%20number%20or%20no%202cf987c799d04001b5b250af9ccf4b37.md, Different%20between%20++number%20and%20number++%2094b1d133e52143c280873b9b0322c3f6.md, What%20is%20the%20split%20function%20of%20the%20string%20for%20c3ed6820412f4e20ba47904caf5394d7.md, What%20is%20the%20indexOf%20function%20of%20the%20string%20used%20fo%20d10d66bfd8ad4c0eb51746f1710cdde1.md, Given%20a%20string%20called%20symmetry,%20the%20reverse%20of%20the%208f0fcb54be87414db40569a98cc941a5.md
Tags: Basic, Concept

# ****Primary - Kiểu nguyên thủy****

- Tuân theo tham trị

---

- string
- number
- boolean
- bigint
- symbol

---

<aside>
💡 Mỗi lần gán giá trị tham trị sẽ được vào 1 ô nhớ mới

</aside>

- Nếu gán biến A với biến B có giá trị tham trị

```jsx
A = B
```

- Copy giá trị của B ra ô nhớ mới
- Gán ô nhớ mới đó cho A
- A và B không liên kết với nhau
- A thay đổi thì B không đổi và ngược lại

# ****Reference - Tham chiếu****

- Tuân theo tham chiếu

---

- object
- array
- function
- null
- undefined

---

<aside>
💡 Giá trị tham chiếu sẽ cùng tham chiếu tới cùng 1 ô nhớ với mỗi lần gán

</aside>

- Gán giá trị tham chiếu lần đầu, tạo ô nhớ mới
- Từ lần gán thứ 2, chỉ là gán địa chỉ ô nhớ tới biến đó
- Nếu gán biến A với biến B có giá trị tham chiếu

```jsx
A = B
```

- A được gán địa chỉ ô nhớ của B
- Giá trị bên trong B thay đổi thì A cũng thay đổi và ngược lại

---

**Recall**

- Built-in: cài sẵn

# Built-in Types

JavaScript defines seven built-in types:

- null
- undefined
- boolean
- number
- string
- object
- symbol—added in ES6!

## Number

- toFixed
    - Làm tròn số thập phân

```jsx
var a = 42.59;
a.toFixed( 0 ); // "43"
a.toFixed( 1 ); // "42.6"
a.toFixed( 2 ); // "42.59"
a.toFixed( 3 ); // "42.590"
a.toFixed( 4 ); // "42.5900"
```

## Natives

**String()**

```jsx
var a = new String( "abc" );
typeof a; // "object" ... not "String"
a instanceof String; // true
Object.prototype.toString.call( a ); // "[object String]"
```

- Object Wrapper Gotchas

```jsx
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

- toString

**Number()**

- toNumber

**Boolean()**

**Array()**

- Array contructor

```jsx
var a = new Array( 1, 2, 3 );
a; // [1, 2, 3]
var b = [1, 2, 3];
b; // [1, 2, 3]
```

```jsx
var a = new Array( 3 );  // empty x 3
var b = [ undefined, undefined, undefined ]; // undefind x 3
var c = []; 
c.length = 3; // empty x 3
```

**Object()**

**Function()**

**RegExp()**

**Date()**

**Error()**

**Symbol()—added in ES6!**

- Symbols are special “unique”

### Hoisting & Block-scoped

- Phân biệt let, var, const  
- Hoisting di chuyển tất cả các biến và hàm khi khai báo lên đầu scope trước khi chúng được thực thi.  
  - Nó chỉ di chuyển khai báo, còn việc gán giá trị thì giữ nguyên.  
  - Có thể sử dụng biến trước khi khai báo trong code  
- var là kiểu khai báo biến theo cơ chế hoisting  
- Let, const là khai báo biến theo cơ chế Block-scoped  
  - Vị trí khai báo của biến được giữ nguyên  
  - Không được sử dụng biến trước khi khai báo

# Falsy & Truthy in Javascript

Category: Javascript
First Source: Comparison%20operator%20of%20Javascript%20c6d2ea2b78a74139af60fcc3a63b9221.md
Tags: Basic, Concept

# ****Falsy****

<aside>
💡 Giá trị mà `if` nhận là sai

</aside>

- 0
- - 0
- false
- null
- undefined
- “" (length = 0)
- NaN

# ****Truthy****

<aside>
💡 Giá trị mà `if` nhận là đúng

</aside>

- Tất cả không phải falsy

# Comparison operator of Javascript

Category: Javascript
First Refrence: What%20is%20the%20difference%20between%20==%20and%20===%20operator%20fb9528b22ead48bb9f4bd9228fc415c8.md, Operator%20!!%20used%20for%20what%205d43efcf1fb648a29b9b508da37e4097.md, and%20&&%204af002d7b3194ccbaafdd54f75772170.md, Falsy%20&%20Truthy%20in%20Javascript%20d5d0981199e54a348cb5c19f1c5d1a0a.md
Tags: Basic, Concept

== là so sánh bằng nhưng có ép type

- không bằng là !=

=== là so sánh bằng nhưng ko ép kiểu

- không bằng là !==

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

- > là lớn hơn
- >= là lớn hơn hoặc bằng
- < là nhỏ hơn
- <= là nhỏ hơn hoặc bằng

<aside>
💡 return **boolean**

</aside>

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