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