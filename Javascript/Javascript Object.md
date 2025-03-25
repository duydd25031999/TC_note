# Prototype

- Khi `new` ⇒ tạo 1 bject inherit tới propotype của contructor
- strict equality operator (`===`)
- abstract equality operator (`==`)

## ****Class****

- Javascript in old version doesn’t have `class` concept
- It just `stimulates class`.
- When function is declared <== JS engine add Prototype to it
    - Prototype is constructor of function
    - Prototype inherits from Prototype of object

```jsx
var Human = function(name) {
    this.name = name;
}

Human.prototype.sayHello = function() {
    console.log("Hello, I'm " + this.name);
}

Human.prototype.goRage = function() {
    console.log("goRage");
}

var p1 = new Human('p1');   // new =call=> Prototype.constructor()
                            // add __proto__ =refer=> function.prototype
                            // không mất công tạo những gì có trong prototype
var p2 = new Human('p2');

p1.sayHello();
p2.sayHello();
p1.goRage();

console.log(p1.hasOwnProperty('name'));
console.log(p1.hasOwnProperty('goRage'));
console.log(p1.hasOwnProperty('hasOwnProperty'));

console.log(Object.getPrototypeOf(p1));
console.log(p1);

// Inheritance
var SuperHero = function(name, alias, power) {
    Human.call(this, name);
    this.alias = alias;
    this.power = power;
}

SuperHero.prototype = Object.create(Human.prototype);
SuperHero.prototype.constructor = SuperHero;

var s1 = new SuperHero('p1', 'a1', 'pow1');
console.log(s1 instanceof SuperHero);
console.log(s1 instanceof Human);
s1.sayHello();

// Polymorphism
SuperHero.prototype.sayHello = function() {
    console.log("Hello, I'm " + this.alias);
}
// Khi gọi 1 attribute trong prototype
// engine =find=> this.__proto__ =dont_has=> super.__proto__ =dont_has=> Object.__proto__
```

### Constructor

- Prototype is 1 default object of constructor (class) that instance inherited
- `Object.prototype` = root prototype

```jsx
function Foo() {
    // ...
}

Foo.prototype.constructor === Foo; // true
var a = new Foo();
a.constructor === Foo; // true
```

# Object Prototype

### getPrototypeOf

```jsx
Object.getPrototypeOf(obj) // get Prototype of obj
```

### assign

- The `assign()` method copies all enumerable own properties from one or more source objects to a target object.

```jsx
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };

const returnedTarget = Object.assign(target, source);

console.log(target);
// expected output: Object { a: 1, b: 4, c: 5 }

console.log(returnedTarget);
// expected output: Object { a: 1, b: 4, c: 5 }
```

### create

- Clone value from original object to new object.
- New object isn’t reference to original object.

```jsx
var obj2 = Object.create(obj) // return clone of original obj
```

### hasOwnProperty

```jsx
obj.hasOwnProperty('nameOfProperty') // return boolean
nameOfProperty in obj //use "in" keyword
```

### defineProperty

```jsx
Object.defineProperty(obj, prop, option); // create new property for object
```

- option is a object
    - `configurable`: is able to change config of property again.
    - `value` : default value.
    - `writable` : is changable
    - `get` : function get value
    - `set` : function change value

### instanceof

- Check that is object instance of a class.

### Shallow clone, deep clone

- Shallow clone thì khi clone, biến mới hoặc các thành phần của biến mới vẫn còn quan hệ với biến ban đầu  
- Shallow clone chỉ clone giá trị nông, nếu có giá trị lồng nhau, như biến lồng trong biến, thì property là object vẫn tham chiếu tới property của đối tượng cũ  
- Nếu property object đó thay đổi trong 1 đối tượng thì đối tượng còn lại vẫn nhận được  
- Deep clone là tạo mới một biến có cùng giá trị và được cắt đứt quan hệ hoàn toàn với biến được clone.  
- Nếu có propesrty là object thì bới deep clone sẽ không tham chiếu tới property object cũ

# Javascript Callback

Category: Javascript
First Refrence: What%20is%20a%20Callback%20function%203af9077ab4da484e9ad530f59b990486.md, What%20is%20Callback%20in%20Callback%20acade1233918421ca64796a736c3aa7a.md, What%20is%20a%20Callback%20Hell%20a13fad3a6123496c9c0d2a3188735587.md, What%20is%20aware%20of%20Callback%20726de997a549438f8da6683d1ece8928.md, What%20is%20Use%20of%20Callback%202e471dc4b5bf496fb7b04ffe65db9398.md
First Source: Javascript%20Function%2024d903792bfd4ce0876afb08e96fea70.md
Tags: Basic, Concept

<aside>
⚠️ Sự mất kiểm soát ở 1 step ⇒ mất kiểm soát các steps sau

</aside>

- Nếu không có cách kiểm soát hoàn toàn ⇒ bugs

# Concept

- Callback là function mà truyền vào function khác như tham chiếu

---

- A callback is a function passed into another function as an argument.

```jsx
function consoleLogFrom(getMessageCallback) {
  const message = getMessageCallback();
	console.log(message);
}

function sayHelloWorld() {
	return 'hello world';
}

consoleLogFrom(sayHelloWorld); //hello world
```

- This function is `invoked inside the outer function` to complete an action.
    - The other function can call the callback function inside its scope

## Use of Callback

- Callback có rất nhiều tác dụng
- Nhưng có 2 cái được biết đến nhiều nhất

### Đăng kí 1 hành động trừu tượng - 1 abstract action

- 1 hành động trừu tượng, linh hoạt theo hoàn cảnh
- Trừu tượng là mình biết nó tồn tại nhưng nội dung bên trong của nó sẽ thay đổi tùy hoàn cảnh

### Đăng kí 1 hành động sẽ được gọi trong tương lai

- Hành động sẽ được gọi cụ thể tại 1 thời điểm trong tương lai
- Hành động phải đợi hành động phía trước không biết bao giờ xong
- Cái hành động cụ thể trong tương lai có thể do `setTimeout`, `setInterval`
- Hành động phải đợi hành động phía trước không biết bao giờ xong thì trong Jquery có ajax để gọi api

---

- It means `registering` a `pending action` will be executed at the `right time in future`.

# Continuations

## Sequential Brain

- When we `fake multitasking` ⇒  we switch back and `forth between two or more tasks` in rapid succession ⇒ simultaneously progressing on each task in `tiny, fast little chunks`
- We do it so `fast` that to the `outside world` it appears as if we're `doing these things in parallel`.

## Callback Hell

- Callback Hell là 1 lỗi coding với việc để callbacks lồng nhau nhiều quá khiến code khó đọc và debug
    - Nhất là khi sử dụng trong logic bất đồng bộ
- Callback Hell khiến khó biết rõ được thứ tự chạy của callback và thời điểm callback được gọi

---

- Callback Hell is an anti-pattern with multiple nested callbacks which makes code hard to read and debug when dealing with asynchronous logic.
- Callback Hell is that executing order of different callbacks cannot be determined.
    - Easily occurs with nested callbacks or nested async actions.
    - Can’t determine when callback is executed.
- The difficulty of control callback-driven design is the worst (and yet most subtle) problems.
- The most troublesome problem with callbacks is inversion of control leading to a complete breakdown along all those trust lines.

## Trying to Save Callbacks

- Split callbacks = break into clearly steps in same level, sequence ⇒ pass multiple callback arguments lead to each step.
- Error-first style =  thinking about catching error first then implement case success.
- Call the callback too early
    - Callback is executed before sequential code.
- Call the callback too late (or never)
    - Set timeout = create 1 flag + 1 timeout to make sure not awaiting forever
- Call the callback too few or too many times
- Fail to pass along any necessary environment/parameters
- Swallow any errors/exceptions that may happen

---

- **Vocabulary**
    - inversion: đảo ngược

# Javascript Map

Category: Javascript
Tags: Concept, Low

```abap
var m = new Map();

var x = { id: 1 }, y = { id: 2 };

m.set( x, "foo" );
m.set( y, "bar" );

m.get( x ); // "foo"
m.get( y ); // "bar"

m.delete( y );
m.size; // 2
```

# Javascript Proxy

Category: Javascript
Tags: Concept, Low

**Recall**

- Proxy chỉ tạo 1 get, set duy nhất
- Có thể tạo ra 1 getter 1 property mới không có trong object

## Concept

- Proxy là class để wrapper 1 object
- Proxy tạo get, set ⇒ lấy properties của object

```jsx
let products = new Proxy([
  { name: 'Firefox', type: 'browser' },
  { name: 'SeaMonkey', type: 'browser' },
  { name: 'Thunderbird', type: 'mailer' }
],
{
  get(obj, prop) {
    // The default behavior to return the value; prop is usually an integer
    if (prop in obj) {
      return obj[prop];
    }

    // Get the number of products; an alias of products.length
    if (prop === 'number') {
      return obj.length;
    }

    let result, types = {};

    for (let product of obj) {
      if (product.name === prop) {
        result = product;
      }
      if (types[product.type]) {
        types[product.type].push(product);
      } else {
        types[product.type] = [product];
      }
    }

    // Get a product by name
    if (result) {
      return result;
    }

    // Get products by type
    if (prop in types) {
      return types[prop];
    }

    // Get product types
    if (prop === 'types') {
      return Object.keys(types);
    }

    return undefined;
  }
});

console.log(products[0]);          // { name: 'Firefox', type: 'browser' }
console.log(products['Firefox']);  // { name: 'Firefox', type: 'browser' }
console.log(products['Chrome']);   // undefined
console.log(products.browser);     // [{ name: 'Firefox', type: 'browser' }, { name: 'SeaMonkey', type: 'browser' }]
console.log(products.types);       // ['browser', 'mailer']
console.log(products.number);      // 3
```