# Javascript notes

## This

This in a (not arrow) function always referes to the object who is calling that function
## Object creation 

For plain Javascript (before ES2015 and so on...)

In javascript we can create objects in different ways.

In general constructors are a way to initialize a new created 'genereric' object. In javascript we have several ways to do it.

With New that allows us to construct from a function / class in a OOP fashion.
Object.create() allows to construct from literal object (initializing with initalize pattern).
Factory functions use a function to return an object initialized through the function params.

Operator 'new' do the following: 

- Creates a plain object {}
- set on object's prototype the prototypes constructor. 
- call the constructor with apply passing the object created as parameter.
- returns the constructor from step 3 or if empty the empty object.

```
function Person(saying) {
  this.saying = saying
}

Person.prototype.talk = function() {
  console.log('I say:', this.saying)
}


function spawn(constructor) {
  var obj = {a: '1'}
  console.log(constructor.prototype);
  // Object.setPrototypeOf(obj, constructor.prototype)
  var argsArray = Array.prototype.slice.apply(arguments)
  constructor.apply(obj, argsArray.slice(1)) 
  console.log(obj);
  console.log(constructor);
  return obj
}

var crockford = spawn(Person, 'SEMICOLANS!!!1one1')
crockford.talk()
```

We can create an object using object literal notation.
 
New use some "magic" for mimic classical OOP. (In the way how this is handled). But it masks prototype inheritance. 

NOTE: If a factory function is prepended with new keyword it is not handled as a normal constructor function. The object is return instead. In other words a function, if factory function, is not affected by new keyword.




