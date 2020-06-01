---
layout: post
title: Prototype in Javascript
---

Prototypes are usually seen when a module is exporting some functions, it would sometimes add that function using `module.prototype.newfunc = `. So what is prototype?

Prototype is, at a very high level, the constructor in normal OOP concepts. Every new instance of this Object would have the methods and properties defined in the prototype. Since real constructors are seldom used in JS, the example by [w3schools.com](www.w3schools.com/js/js_object_prototypes.asp) is very useful:

```javascript
function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;
}

var myFather = new Person("John", "Doe", 50, "blue");
var myMother = new Person("Sally", "Rally", 48, "green");
```

As if this meld of constructor and the constructed object is not crazy enough, you can then get the `prototype` property to modify the constructor in runtime:

```javascript
Person.prototype.nationality = "English";
```

Then every (existing) `Person` would also have the `nationality` property. You can even get a reference to the underlying prototype object and replace it:

```javascript
// from javascriptweblog.wordpress.com
var a = {};
a.__proto__ = Array.prototype;
a.length;   //-> 0
```

but there is a difference between `.prototype` and `__proto__`, in that if you assign `.prototype` to a new thing, existing objects won't get updated, whereas `__proto__` would. 

This kinda shows an extremely loose definition of inheritance, but allow for much greater freedom, and confusion.
