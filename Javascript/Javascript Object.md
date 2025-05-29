# Prototype

[1. {Scan} What is javascript prototype?](./Javascript_Object_Questions.md#javascript-prototype-1)

- In JavaScript, every object carries an internal `[[Prototype]]` link to another object.
- That prototype object stores methods or static properties of  constructor or class
  - It is refered by all instances created with the same constructor or class.
  - It's similar with Java Class holds common properties for every instance of this class
  - Shared, not copied – Only one copy of each method exists on the prototype; all instances reference it.
- Keyword `new` ⇒ create inherited object links to propotype of contructor

## Constructor

[2. {Scan} What is constructor in javascript?](./Javascript_Object_Questions.md#javascript-prototype-2)

- Constructor is a kind of Javascript function to defind an instance object (a blueprint)
  - If the function doesn’t explicitly return an object
  - Called with the `new` keyword to return an instance object
  - Links that object’s internal `[[Prototype]]` to Constructor.prototype.
- Prototype is 1 default object of constructor (class) that instance inherited
  - Every prototype extends from `Object.prototype`

```jsx
function Foo() {
    // ...
}

Foo.prototype.constructor === Foo; // true
var a = new Foo();
a.constructor === Foo; // true
```

## Class stimulator

[3. {Scan} How does "JS Prototype" replace "Class" in OOP like Java?](./Javascript_Object_Questions.md#javascript-prototype-3)

- Javascript in old version doesn’t have `class` concept
- It just `stimulates class` => It stimulates OOP

```jsx
// [4. {Scan} How to create "stimulates class" with javascript function](./Javascript_Object_Questions.md#javascript-prototype-4)
var Human = function(name) { // contructor
  this.name = name;
}

Human.prototype.sayHello = function() { // method in "class"
    console.log("Hello, I'm " + this.name);
}

Human.prototype.goRage = function() {
    console.log("goRage");
}

var person1 = new Human('person1');   // new =call=> Human.prototype.constructor()
                            // add "__proto__" property =refer=> Human.prototype
                            // không mất công tạo những gì có trong prototype
var person2 = new Human('person2');

person1.sayHello();
person2.sayHello(); // [5. {Scan} Is return of "person2.sayHello()" same with "person1.sayHello()"](./Javascript_Object_Questions.md#javascript-prototype-5)
person1.goRage();

// [6. {Scan} What is return of those console.log](./Javascript_Object_Questions.md#javascript-prototype-6)
console.log(person1.hasOwnProperty('name'));
console.log(person1.hasOwnProperty('goRage'));
console.log(person1.hasOwnProperty('hasOwnProperty'));

console.log(Object.getPrototypeOf(person1));
console.log(person1);

// Inheritance
var SuperHero = function(name, alias, power) {
    Human.call(this, name);
    this.alias = alias;
    this.power = power;
}

SuperHero.prototype = Object.create(Human.prototype);
SuperHero.prototype.constructor = SuperHero;

var superHero1 = new SuperHero('person1', 'a1', 'pow1');

superHero1.sayHello();

// Polymorphism
SuperHero.prototype.sayHello = function() {
    console.log("Hello, I'm " + this.alias);
}
// Khi gọi 1 attribute trong prototype
// engine =find=> this.__proto__ =dont_has=> super.__proto__ =dont_has=> Object.__proto__
```

### instanceof

[7. {Scan} How to check an object is instance of a class / function?](./Javascript_Object_Questions.md#javascript-prototype-7)

- Check that is object instance of a class.

```jsx
console.log(superHero1 instanceof SuperHero);
console.log(superHero1 instanceof Human);
```


## Object Prototype

### Questions

[8. {Scan} Why is Object Prototype important?](./Javascript_Object_Questions.md#javascript-prototype-8)

[17. {Interrogate} Why is storing methods on the constructor’s prototype more memory-efficient than defining them inside the constructor, and when can the extra lookup hurt performance?](./Javascript_Object_Questions.md#javascript-prototype-17)

[18. {Interrogate} Why do developers often use `Object.create(null)` to build “pure dictionary” objects, and what drawbacks should you watch out for?](./Javascript_Object_Questions.md#javascript-prototype-18)

----

- Object Prototype is the root prototype
- Every prototype extends from Object Prototype

### getPrototypeOf

```jsx
Object.getPrototypeOf(obj) // get Prototype of obj
Object.getPrototypeOf(superHero1) // [9. {Scan} What is return of this line?](./Javascript_Object_Questions.md#javascript-prototype-9)
```

### Shallow clone, deep clone

[10. {Scan} When do we use Shallow clone?](./Javascript_Object_Questions.md#javascript-prototype-10)
[11. {Scan} When do we use Deep clone?](./Javascript_Object_Questions.md#javascript-prototype-11)

- Shallow clone: Copies the first-level properties of an object/array into a new container
  - Any nested objects/arrays are still shared references
  - Used when object/array has only 1-level properties
  - Intentional sharing – You want children to stay linked (e.g., caching large immutable configs)
- Deep clone: 
  - Recursively duplicates every nested object/array so the clone has no shared references with the original
  - Totally clone without any connection
- Compare between 2 kinds:
  - Shallow cloned object still shares nested references
  - Deep cloned object doesn't share nested references

-----

- Shallow clone thì khi clone, biến mới hoặc các thành phần của biến mới vẫn còn quan hệ với biến ban đầu  
- Shallow clone chỉ clone giá trị nông, nếu có giá trị lồng nhau, như biến lồng trong biến, thì property là object vẫn tham chiếu tới property của đối tượng cũ  
- Nếu property object đó thay đổi trong 1 đối tượng thì đối tượng còn lại vẫn nhận được  
- Deep clone là tạo mới một biến có cùng giá trị và được cắt đứt quan hệ hoàn toàn với biến được clone.  
- Nếu có propesrty là object thì bới deep clone sẽ không tham chiếu tới property object cũ

### assign()

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

[12. {Scan} Does `returnedTarget` properties refer with `target` properties](./Javascript_Object_Questions.md#javascript-prototype-12)

### create()

[13. {Scan} What is different between `assign()` and `create()`](./Javascript_Object_Questions.md#javascript-prototype-13)
[14. {Scan} `create()` is shallow clone or deep clone](./Javascript_Object_Questions.md#javascript-prototype-14)

- `Object.create(proto)` creates a new empty object and sets its `[[Prototype]]` link to point at proto.
- **No data is copied**: properties on proto are accessed only through the prototype chain
  - they remain on `proto`, so changing `proto.shared` is instantly reflected in `obj.shared`

```jsx
var obj2 = Object.create(obj) // return clone of original obj
```

### hasOwnProperty

[15. {Scan} How to check object has an property or not](./Javascript_Object_Questions.md#javascript-prototype-15)

```jsx
obj.hasOwnProperty('nameOfProperty') // return boolean
nameOfProperty in obj //use "in" keyword
```

### defineProperty

[16. {Scan}  Why we need to define property](./Javascript_Object_Questions.md#javascript-prototype-16)

```jsx
Object.defineProperty(obj, prop, option); // create new property for object
```

- option is a object
  - `configurable`: is able to change config of property again.
  - `value` : default value.
  - `writable` : is changable
  - `get` : function get value
  - `set` : function change value

# Javascript Callback

### Questions

[1. {Scan} Why can Callback be passed into another function as an argument?](./Javascript_Object_Questions.md#javascript-callback-1)

[7. {Scan} {Interrograte} Why do we register a deferred action as a callback (e.g., via setTimeout, AJAX), and what trade-offs does this non-blocking model introduce?](./Javascript_Object_Questions.md#javascript-callback-7)

----

- ⚠️ Sự mất kiểm soát ở 1 step ⇒ mất kiểm soát các steps sau
- Nếu không có cách kiểm soát hoàn toàn ⇒ bugs

## Concept



- A callback is a function passed into another function as an argument.
- Callback là function mà truyền vào function khác như tham chiếu

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

[2. {Scan} Callback is used only for calling API, isn't it?](./Javascript_Object_Questions.md#javascript-callback-2)

- Callbacks have numerous applications
- But two of them are the most widely recognized

---

- Callback có rất nhiều tác dụng
- Nhưng có 2 cái được biết đến nhiều nhất

### Registering an abstract, polymorphic action

- An action that is abstract-flexible and context-dependent
- Abstract means we know the action exists, but its internal content will vary with the situation

---

- 1 hành động trừu tượng, linh hoạt theo hoàn cảnh
- Trừu tượng là mình biết nó tồn tại nhưng nội dung bên trong của nó sẽ thay đổi tùy hoàn cảnh

### Registering an action that will run in the future

- The action is executed at a specific point in the future
- It must wait for a preceding task of unknown duration to finish
- The future action might be scheduled by setTimeout or setInterval
- In jQuery, an AJAX call illustrates this pattern: the callback waits until the API request (whose completion time is uncertain) is done
- It means `registering` a `pending action` will be executed at the `right time in future`.

---

- Hành động sẽ được gọi cụ thể tại 1 thời điểm trong tương lai
- Hành động phải đợi hành động phía trước không biết bao giờ xong
- Cái hành động cụ thể trong tương lai có thể do `setTimeout`, `setInterval`
- Hành động phải đợi hành động phía trước không biết bao giờ xong thì trong Jquery có ajax để gọi api

## Continuations

### Sequential Brain

[3. {Scan} How can we run multitasking in Javascript?](./Javascript_Object_Questions.md#javascript-callback-3)

- When we `fake multitasking` ⇒  we switch back and `forth between two or more tasks` in rapid succession ⇒ simultaneously progressing on each task in `tiny, fast little chunks`
- We do it so `fast` that to the `outside world` it appears as if we're `doing these things in parallel`.

### Callback Hell

[4. {Scan} What is callback hell?](./Javascript_Object_Questions.md#javascript-callback-4)
[5. {Scan} Why does “callback hell” emerge in deeply nested asynchronous code, and how does inversion of control hurt maintainability?](./Javascript_Object_Questions.md#javascript-callback-5)

- Callback Hell is an anti-pattern with multiple nested callbacks which makes code hard to read and debug when dealing with asynchronous logic.
- Callback Hell is that executing order of different callbacks cannot be determined.
    - Easily occurs with nested callbacks or nested async actions.
    - Can’t determine when callback is executed.
- The difficulty of control callback-driven design is the worst (and yet most subtle) problems.
- The most troublesome problem with callbacks is inversion of control leading to a complete breakdown along all those trust lines.

---

- Callback Hell là 1 lỗi coding với việc để callbacks lồng nhau nhiều quá khiến code khó đọc và debug
    - Nhất là khi sử dụng trong logic bất đồng bộ
- Callback Hell khiến khó biết rõ được thứ tự chạy của callback và thời điểm callback được gọi



### Trying to Save Callbacks

[6. {Scan} How to save callback from Callback hell?](./Javascript_Object_Questions.md#javascript-callback-6)

- Split callbacks = break into clearly steps in same level, sequence ⇒ pass multiple callback arguments lead to each step.
- Error-first style = thinking about catching error first then implement case success.
- Call the callback too early
    - Callback is executed before sequential code.
- Call the callback too late (or never)
    - Set timeout = create 1 flag + 1 timeout to make sure not awaiting forever
- Call the callback too few or too many times
- Fail to pass along any necessary environment/parameters
- Swallow any errors/exceptions that may happen

# Javascript Map

### Questions

[1. {Scan} What is advantage of Map with Array?](./Javascript_Object_Questions.md#javascript-map-1)

[2. {Interrograte} Why would you choose Map over a plain object for a key-value store, and what real impact does that have on large-scale data handling?](./Javascript_Object_Questions.md#javascript-map-2)

## Concept

- Lookup complexity: Average O(1)-hash-based key table.
- No accidental index clash: Keys live in their own hash table; you can safely use "0" or length as keys without affecting structure.	
- Memory for large sets: Engines store Maps in specialized tables → better memory/layout for tens of thousands of pairs.
- Semantic clarity: Code reads “this is a key-value store”.	

```jsx
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

- Proxy là class để wrapper 1 object
- Proxy tạo get, set ⇒ lấy properties của object
- Proxy chỉ tạo 1 get, set duy nhất
- Có thể tạo ra 1 getter 1 property mới không có trong object

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