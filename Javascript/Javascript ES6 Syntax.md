# Javascript ES6 Syntax

Category: Javascript
First Refrence: What%20is%20ES6%20edc58b094f53403d86213d87c845a4cb.md, What%20is%20difference%20betwen%20let,%20const%20with%20var%20bb1b73a029b04ca09659f22a7ef9a794.md, What%20is%20spread%20syntax%203baab138fb1442328164f180fcc0a81e.md, What%20is%20template%20literal%20ebd2b9c43cd3478f92de5c462c88a958.md, When%20I%20declare%20a%20variable%20like%20const%20arr=%5B1,2,3,5%5D%203003ff4a8d5642c195db682405acc4de.md, How%20to%20loop%20value%20of%20Object%20a0d601d33c1b4d018c5419e6e2229807.md, What%20is%20Destructuring%201c5c8b3e1b024ccd90c5fbf0b4bbcbec.md
Tags: Basic, Concept

## Questions

[What is ES6?](What%20is%20ES6%20edc58b094f53403d86213d87c845a4cb.md)

[What is difference betwen let, const with var](What%20is%20difference%20betwen%20let,%20const%20with%20var%20bb1b73a029b04ca09659f22a7ef9a794.md)

[When I declare a variable like const arr=[1,2,3,5], can I change value of any item inside that array](When%20I%20declare%20a%20variable%20like%20const%20arr=%5B1,2,3,5%5D%203003ff4a8d5642c195db682405acc4de.md)

[What is ****Destructuring**** ?](What%20is%20Destructuring%201c5c8b3e1b024ccd90c5fbf0b4bbcbec.md)

[What is spread syntax?](What%20is%20spread%20syntax%203baab138fb1442328164f180fcc0a81e.md)

[What is template literal ?](What%20is%20template%20literal%20ebd2b9c43cd3478f92de5c462c88a958.md)

[How to loop value of Object](How%20to%20loop%20value%20of%20Object%20a0d601d33c1b4d018c5419e6e2229807.md)

## Concept

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

Let & const thì scope đều là block scope

- Biến tuân theo đúng thứ tự: khai báo trước rồi mới sử dụng,
- Nếu khai báo trong 1 {scope} thì không được dùng bên ngoài {scope} đó
- Bản chất của const là nó không làm thay đổi được giá trị reference => Const không reassigned

```jsx
const a = 1;
a = 2 //Error
```

Const = object = refer tới 1 ô nhớ

- Không refer được tới ô khác
- Vẫn có thể thay đổi giá trị properties của object đó

```jsx
const cool = { 
    people: ['you', 'me', 'tesla', 'musk'] 
}
cool.people.push('berners-lee')
console.log(cool) // { people: ['you', 'me', 'tesla', 'musk', 'berners-lee'] }
```

## ****Destructuring****

Unpack values from arrays, or properties from objects

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

## Spread ****syntax****

Gộp các element thành 1 array

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

Trải elements của 1 array vào 1 array khác

```jsx
var x = [1, 2, 3]
var y = [4, 5, ...x] // [4, 5, 1, 2, 3]
```

Trải properties của obj cho 1 obj khác

```jsx
var person = {name: "Duy", age: 21}; 
var student = {...person, job: 'student'} //{name: "Duy", age: 21, job: "student"}
```

## T****emplate literal****

Để string vào backtick

```jsx
`string`
```

Lưu cả xuống dòng, tab của string trong code

```jsx
var x = `string 1
        string 2`
/*
"string 1
        string 2"
*/
```

Truyền biến vào string

```jsx
var x = 'world'
var hello = `hello ${x}` //hello world
```

## ES6 For Loop

```jsx
var a = ["a","b","c","d","e"];

for (var idx in a) { // Object.values
	console.log( idx ); // a b c d e
}

// 0 1 2 3 4
for (var val of a) { // Object.keys
	console.log( val );
}
```

---