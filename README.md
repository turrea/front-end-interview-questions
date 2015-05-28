# front-end-interview-questions
Questions that I've either been asked, have asked, or would ask in an interview for front-end developer position.

## Javascript

### What is the differnce between null and undefined?
Null is a specific value meant to represent "empty" whereas undefined usually signifies a variable that has not been set.

### What is the difference between == and ===?
=== compares both type and value, == will perform the same check but also attempt to perform type coercion

### What is prototypical inheritance?

### Show an example of prototypical inheritance.

## Angular.js
### What are some of Angular's strengths?
Angular provides the tools for having a more structured single page application. Angular's module system allows us to seperate an application into more manageable and maintainable components. We can also easily separate the concerns of handling user interaction, implementing business logic, and manipulating DOM elements by using controllers, services, and directives, respectively. Angular's dependency injection feature not only allows us to easily call upon services as needed, but it also makes unit testing much easier. Its two-way data binding also reduces the need for the developer to manually sync the view and the model. Or put another way, two-way data binding makes it easier for us to have a separate model instead of using the DOM as a model.

### What are some of Angular's weaknesses?
Angular is a layer that runs on top of Javascript, and thus can suffer from a noticeable performance hit in certain situations. One has to be careful not to create too many watch function for example as they are checked every single digest loop, and often multiple times. Angular filters should not be used on very large collections, especially within an ngRepeat directive, as both the filtering and DOM rendering will cause considerable slowdown in some cases.

Angular's module system currently does not support loading modules asynchronously (although it can be done via a workaround). Therefore you must explicitly specify the modules that will be needed up front.

Sometimes the scope prototypical inheritance can through people for a loop and cause variables to be available where maybe they shouldn't be.

One also has to take extra care to tell Angular when changes have occurred outside of it, for example calling scope.$apply() inside a Javascript event handler if that handler modifies an Angular variable.

A common error is not using the dot operator inside of ngModel to ensure that it does not end up masking the parent scope's variable.

### What are some features of ES6 that you're looking forward to?

## CSS

## LESS/SASS

## Grunt and Builds
