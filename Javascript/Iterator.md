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