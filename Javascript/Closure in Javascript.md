# Closure in Javascript

Category: Javascript
First Refrence: What%20are%20closures%20e8582c50bf884360bbad74b62c55daa2.md
Tags: Basic, Concept

**Recall**

## Concept

- A closure is a function having access to the parent scope, even after the parent function has closed.
- It is an inner function that has access to the outer or enclosing function’s variables.
- When a function returns another function, the returned function can use any variable inside scope of parent function.
    - When parent function is finish execution, all variables accessed in returned function aren’t collected by garbage.
    - When execute returned function, those variables aren’t re-declared.
- 1 (nested) child function accesses into a variable belonged to parent function.
    - When scope parent function is cleaned, that variable still closure reference into parent function isn’t collected by garbage.

### ****Builder Pattern****

```jsx
function buildAdder(x) {
    var accumlator = x;

    return function(y) {
        return accumlator += y;
    }
}

var adder = buildAdder(1);
adder(2);   //  3
adder(3);   //  6
adder(4);   //  10
```

### ****Stimulate Class****

```jsx
var newPerson = function(name) {
    var _name = name;
    return {
        setName: function(name) {
            _name = name;
        },
        getName: function() {
            return _name;
        },
        sayHi: function() {
            console.log('Hi, I\'m ' + _name);
        }
    }
}

var person1 = newPerson('Person 1');
person1.sayHi();

var person2 = newPerson('Person 2');
person2.sayHi();
```

### ****Singleton Pattern****

```jsx
const singleton = (function() {
    var _incrementor = 0;
    return {
        get: function() {
            return "Incrementor = " + _incrementor;
        },
        increment: function() {
            _incrementor++;
        }
    };
}());
console.log(singleton.get());
singleton.increment();
console.log(singleton.get());
```

### ****Pitfall Closure****

```jsx
var newPerson = function(name) {
    var _name = name;
    var methods = {
        getName() {                 //mỗi lần gọi newPerson() lại khởi tạo function 
            return _name;           //tốn bộ nhớ
        },
        setName(name) {
            _name = name;
        },
        sayHello() {
            console.log('Hello, I\'m ' + _name);
        }
    }

    return methods
}
```