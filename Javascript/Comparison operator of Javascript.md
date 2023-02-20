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