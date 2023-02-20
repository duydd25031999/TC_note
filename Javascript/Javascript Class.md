# Javascript Class

Category: Javascript
Tags: Concept, Low

## Constructor

```jsx
class Foo {
	 constructor(a,b) {
		 this.x = a;
		 this.y = b;
	 }
 gimmeXY() {
	 return this.x * this.y;
 }
}
```

## extends and super

```jsx
class Bar extends Foo {
 constructor(a,b,c) {
	 super( a, b );
	 this.z = c;
 }
 gimmeXYZ() {
	 return super.gimmeXY() * this.z;
 }
}

var b = new Bar( 5, 15, 25 );
b.x; // 5
b.y; // 15
b.z; // 25
b.gimmeXYZ(); // 1875
```

---