# front-end-interview-questions
Questions that I've either been asked, have asked, or would ask in an interview for front-end developer position.

## Javascript

### What are the different types in Javascript?
String, Number / Floating Point, Boolean, Null, Undefined, Object

### What is the difference between null and undefined?
Null is a specific value meant to represent "empty" whereas undefined usually signifies a variable that has not been set.

### What is the difference between == and ===?
=== compares both type and value, == will perform the same check but also attempt to perform type coercion

### What does the `var` keyword do?
It creates a new variable on the nearest/closest function scope. It is essentially the keyword used to create local variables in Javascript.

### In the following, what will be logged to the console?
```javascript
var x = 5;
function test(){
  console.log("The value of x is: ", x);
  var x = 10;
}
test();
```

It will log "The value of x is: undefined".

### What is variable hoisting?
In Javascript, all variable and function declarations are automatically moved to the top of the function block.

### What is the difference between `call` and `apply`?
Both are used to call a function and set the value of `this` within that function, but they differ in how arguments are passed to said function. `call` requires that you pass arguments as a comma separated list of values while `apply` accepts an array to be mapped to arguments.

### What is prototypical inheritance?
Inheritance in Javascript is achieved using prototypical/prototypal inheritance. Instead of having classes, Javascript has constructor functions which contain instructions for instantiating a class of object. Each instance of an object contains a reference to its constructor function and to its prototype chain, which it can traverse to access parent class members and methods.

### Demonstrate how to implement private, public and static members in Javascript.
```javascript
//constructor function
function MyClass(){
    //private member
    var myPrivateMember = null;

    //public member
    this.myPublicMember = null;
}

//public method with access to instantiated object "this"
MyClass.prototype.myPublicMethod = function(){ };

//static member
MyClass.myStaticMember = null;

```
### Show an example of prototypical inheritance.
```javascript
function ParentClass(){
    this.parentMember = "parent";
}

function ChildClass(){
}

//inheritance
ChildClass.prototype = new ParentClass();

var childInstance = new ChildClass();
console.log(childInstance.parentMember); //outputs parent

```

### What are some features of ES6 that you're looking forward to?
Of course there is the typical answer of classes and modules, which are both great. But I'm also looking forward to the `let` operator, which allows us to use block scoping for a variable instead of function scoping. Also the `const` operator, which will allow for constants and also be block scoped. Arrow functions are nice too since they will allow us to maintain the value of `this` and do away `var that = this;` kind of code in many places.

## Angular.js
### What are some of Angular's strengths?
Angular provides the tools for having a more structured single page application. Angular's module system allows us to separate an application into more manageable and maintainable components. We can also easily separate the concerns of handling user interaction, implementing business logic, and manipulating DOM elements by using controllers, services, and directives, respectively. Angular's dependency injection feature not only allows us to easily call upon services as needed, but it also makes unit testing much easier. Its two-way data binding also reduces the need for the developer to manually sync the view and the model. Or put another way, two-way data binding makes it easier for us to have a separate model instead of using the DOM as a model.

### What are some of Angular's weaknesses?
Angular is a layer that runs on top of Javascript, and thus can suffer from a noticeable performance hit in certain situations. One has to be careful not to create too many watch function for example as they are checked every single digest loop, and often multiple times. Angular filters should not be used on very large collections, especially within an ngRepeat directive, as both the filtering and DOM rendering will cause considerable slowdown in some cases.

Angular's module system currently does not support loading modules asynchronously (although it can be done via a workaround). Therefore you must explicitly specify the modules that will be needed up front.

Sometimes the prototypical inheritance of scope can cause variables to be available where you thought they might not be, so that's either something to be mindful of or to avoid (possibly through the use of ui-router.

One also has to take extra care to tell Angular when changes have occurred outside of it, for example calling scope.$apply() inside a Javascript event handler if that handler modifies an Angular variable.

A common pitfall is not using the dot operator inside of ngModel. In cases where a new scope is created on that element, if the dot operator is not used the parent scope's value could be masked.

Angular's routing system does not support nested states, which is fine for small projects but can quickly become an issue with larger applications. Thankfully, it is easier to switch to ui-router instead.

### What do you consider some indispensable third-party Angular modules?
Two that immediately come to mind are ui-router and ui-bootstrap.

## CSS

## LESS/SASS

## Grunt and Builds
