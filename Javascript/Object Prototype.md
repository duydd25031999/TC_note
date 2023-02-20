# Object Prototype

Category: Javascript
First Refrence: Do%20you%20know%20what%20is%20deep%20copy%20and%20shallow%20copy%20in%20%20ce502de2d7df4c658c28e0eaaef07260.md, How%20to%20compare%202%20objects%20097b899fd3e844c991c042bcd04ce8a1.md, Why%20does%20any%20object%20not%20define%20the%20function%20toStri%20155ea160d3164e6ca046ef87095ab910.md, What%20is%20the%20difference%20when%20using%20square%20brackets%20%20b256fd06471145ed90cc04c58e59fd04.md
First Source: Prototype%20c4e16c43eaca41e791b8d485a73fa6ad.md
Tags: Common, Concept

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