# Prototype

Category: Javascript
First Refrence: Object%20Protoype%20db1924dfb9e747b69d3f05997c6e4310.md
Tags: Common, Concept

**Recall**

- Khi `new` ⇒ tạo 1 bject inherit tới propotype của contructor
- strict equality operator (`===`)
- abstract equality operator (`==`)

## Questions

[What is the difference when using square brackets and dot to access Object?](What%20is%20the%20difference%20when%20using%20square%20brackets%20%20b256fd06471145ed90cc04c58e59fd04.md)

[Why does any object not define the function toString but still use it?](Why%20does%20any%20object%20not%20define%20the%20function%20toStri%20155ea160d3164e6ca046ef87095ab910.md)

[How to compare 2 objects](How%20to%20compare%202%20objects%20097b899fd3e844c991c042bcd04ce8a1.md)

[Do you know what is deep copy and shallow copy in Javascript?](Do%20you%20know%20what%20is%20deep%20copy%20and%20shallow%20copy%20in%20%20ce502de2d7df4c658c28e0eaaef07260.md)

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