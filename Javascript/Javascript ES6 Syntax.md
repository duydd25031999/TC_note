# Javascript ES6 Syntax

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