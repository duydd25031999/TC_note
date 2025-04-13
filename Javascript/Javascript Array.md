# Javascript Array

## Function

### forEarch

- calls a function for each element in an array.

```jsx
array.forEach(
	function(
		currentValue, // The value of the current element.
		index,        // The index of the current element.
		arr           // The array of the current element.
	), 
	thisValue
);
```

| For Loop | forEach Loop |
| --- | --- |
| It is one of the original ways of iterating over an array. | It is a newer way with lesser code to iterate over an array. |
| It is faster in performance. | It is slower than the traditional loop in performance. |
| The break statement can be used to come out from the loop. | The break statement cannot be used because of the callback function. |
| The parameters are the iterator, counter, and incrementor. | The parameters are the iterator, index of item, and array to iterate. |
| It works with the await keyword. | The await keyword cannot be used due to the callback function. It may lead to incorrect output. |
- `map/filter/reduce` & `forEach`
    - khi thực hiện cùng 1 nhiệm vụ, map/filter/reduce nhanh hơn forEach
    - `forEach` repeat 1 action for each element.
    - `map/filter/reduce` create new item.

### ****map****

- Create a new array from original array that each new item transforms from one original item.

```jsx
const array1 = [1, 4, 9, 16];
// pass a function to map
const map1 = array1.map(x => x * 2);
```

### ****filter****

- Create a new array from original array with all elements that pass the test implemented by the provided function.

```jsx
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
const result = words.filter(word => word.length > 6);
```

### ****reduce****

- It executes a user-supplied reducer callback function on each element of the array, in order, passing in the return value from the calculation on the preceding element.

```jsx
const words = ["Lorem", "Ipsum", "is", "simply", "dummy", "text", "of", "the", "printing", "and", "typesetting", "industry"]
const sentence = words.reduce(function(mergeString, word) {
    return mergeString += word;
}, "");
```

- Use for **normalization**

```jsx
var users = [
    {
        id: 'a1',
        name: 'Duy',
        age: 24
    },
    {
        id: 'a2',
        name: 'Duy',
        age: 24
    },
    {
        id: 'a3',
        name: 'Duy',
        age: 24
    },
    {
        id: 'a4',
        name: 'Duy',
        age: 24
    }
]

var mergeItem = function(obj, item){
    obj[item.id] = item;
    return obj;
}

// normalization
var usersById = users.reduce(mergeItem, {});

console.log('usersById', usersById);

usersById['a2'].name = "Duy 2";
console.log('user a2', users[1]);
```

### join

- Creates and returns a new string by concatenating all of the elements in an array.

```jsx
array.join(
	separator // string to separate each pair of adjacent elements of the array
)
```

### sort

- Sort the original array in ascending order by default
- It effect directly to original array

```jsx
function compare(a, b) {
  if (A is in order before B) { // A is smaller than B in some ways
    return -1;
  }
  if (A is in order after B) { // A is bigger than B in some ways
    return 1;
  }
  // a must be equal to b
  return 0;
}
```

### reserve

- Reverse the elements in an array
- It effect directly to original array

### every

- Tests whether all elements in the array pass the test implemented by the provided function.
- Return true if all elements are pass.

```jsx
function filterFunc(item) {
	return true;
}

array.every(filterFunc);
```

### **concat**

- The **`concat()`** method is used to merge two or more arrays.
- Return new array.

```jsx
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);

console.log(array3);
// expected output: Array ["a", "b", "c", "d", "e", "f"]
```

### **find**

- Returns the first element in the provided array that satisfies the provided testing function.
- If no values satisfy the testing function, `undefined` is returned.

```jsx
const array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10);

console.log(found); // expected output: 12
```

### **findIndex**

- Like `find` but return index number.
- Return `-1` if not found.

### **slice**

- Return sub array of current array.

```jsx
slice(
	start, // index at which to start extraction
	end?   // index of the first element to exclude from the returned array
				 // it is larger than index of the last element of the subarray.
				 // end === undefind ⇒ get from start index to the end of current array
				 // end > array.length ⇒ only get from start index to the end of current array.
)

let fruits = ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango']
let citrus = fruits.slice(1, 3) // ['Orange','Lemon']
```

### splice

- Insert, replace, or delete elements into specific positions in array.
    - No items to insert: delete elements only
    - `deleteCount == 0` : insert element only

```jsx
splice(
	start,       // index at which to start extraction
	deleteCount, // number of deleted elements
	item1,       // items to replace deleted elements
	item2, 
	..., itemN
)
```

# Javascript String

## Concept

- String is a iterator ⇒ access character by index
    
    `char = string[i]`

# Iterator

Category: Javascript
Tags: Concept, Low

## Iterator: trình lặp lại

- An iterator is a well-defined interface for stepping through a series of values from a producer.

```jsx
var something = (function(){
	var nextVal;

	return {
		// needed for `for..of` loops
		// make intertor => intertor => interable
		[Symbol.iterator]: function(){ return this; },

		// standard iterator interface method
		next: function(){
			if (nextVal === undefined) {
					nextVal = 1;
			} else {
				nextVal = (3 * nextVal) + 6;
			} 
			return { done:false, value:nextVal };
		}
	};
})();

something.next().value; // 1
something.next().value; // 9
something.next().value; // 33
something.next().value; // 105

for (var v of something) {
	console.log( v );
	// don't let the loop run forever!
	if (v > 500) {
		break;
	}
} // 1 9 33 105 321 969
```

## Iterable: có thể lặp lại

```jsx
var a = [1,3,5,7,9];
var it = a[Symbol.iterator]();
it.next().value; // 1
it.next().value; // 3
it.next().value; // 5
```

- The for..of loop expects *something* to be an *iterable*.

```jsx
function *something() {
	var nextVal;
	while (true) {
		if (nextVal === undefined) {
			nextVal = 1;
		} else {
			nextVal = (3 * nextVal) + 6;
		} 
	
		yield nextVal;
	}
}

for (var v of something()) {
console.log( v );
// don't let the loop run forever!
if (v > 500) {
break;
}
} // 1 9 33 105 321 969
```