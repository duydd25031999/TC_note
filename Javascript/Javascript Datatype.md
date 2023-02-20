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