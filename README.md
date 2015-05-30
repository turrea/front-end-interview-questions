# front-end-interview-questions
Questions that I've either been asked, have asked, or would ask in an interview for front-end developer position.

- [Javascript](#javascript)
- [Angular.js](#angularjs)
- [CSS](#css)
- [Grunt and Builds](#grunt-and-builds)
- [Performance](#performance)

## Javascript

### What are the different types in Javascript?
String, Number / Floating Point, Boolean, Null, Undefined, Object

### What is the difference between null and undefined?
Null is a specific value meant to represent "empty" whereas undefined usually signifies a variable that has not been set.

### What is the difference between `==` and `===`?
`===` compares both type and value, `==` will run the same check but may also attempt to perform type coercion and check again if the initial check didn't produce a satisfactory outcome. `===` is preferred.

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

### What is an anonymous function?
As its name implies, it is an unnamed inline function definition, often used to succinctly set callbacks such as event handlers.

### What is a closure?
It is the concept that a function has access to all the variables defined on the same scope the function itself was defined on.

### What is prototypical inheritance?
Inheritance in Javascript is achieved using prototypical/prototypal inheritance. Instead of having classes, Javascript has constructor functions which contain instructions for instantiating a class of object. Each instance of an object contains a reference to its constructor function and to its prototype chain, which it can traverse to access parent class members and methods.

### Demonstrate how to implement private, public and static members in Javascript.
```javascript
//constructor function
function MyClass() {
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
function ParentClass() {
    this.parentMember = "parent";
}

function ChildClass() {
}

//inheritance
ChildClass.prototype = new ParentClass();

var childInstance = new ChildClass();
console.log(childInstance.parentMember); //logs "parent"

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

### What are the different types of CSS selectors?
The most often used ones are ID, class, element, attribute, pseudo-class, and child selectors. Of course there are descendant and pseudo-element selectors as well.

### How is selector's specificity calculated?
A 3-tuple is constructed using the number of ID, class, and element selectors, respectively. For example, a selector like `ul#reminders > li.item` the 3-tuple would be `(1, 1, 2)` since there is one ID selector, one class selector, and two element selectors. Then a large base such as 10 is used to calculate the specificity number `(1, 1, 2) => 1*100 + 1*10 + 2*1 = 112`. A selector such as `ul > li` would only have specificity of `(0, 0, 2) = > 0*100 + 0*10 + 2*1 = 2`. Of course this can be overridden by using `!important` next to style rules.

## LESS/SASS

## Grunt and Builds

### What is grunt?
Grunt is a task runner that provides an easy way to automate build processes.

## Performance

### What are some things you can do to decrease page load time?
For starters, it's always good to concatenate Javascript and CSS files (separately) so fewer requests to the server need to be made. You can reduce the payload itself through minification of both Javascript and CSS. Put as many Javascript file includes at the end of the `<body>` tag as possible, so they don't hold up the initial load of the page. At the same time, keep the essential CSS in the `<head>` element to avoid a flash of unstyled content. Wherever feasible, try to take advantage of CDNs, more specifically use CDN links that projects such as jQuery provide to their users, to increase the chances it has already been cached. Put all images used by CSS into a sprite file so only one image needs to be downloaded. Alternatively you may want to consider using inline images.
