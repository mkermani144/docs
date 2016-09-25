Scope
====


`$watch`
----

#### Types of `$watch`
```js
// By reference
// Only watches for object changes itself
$scope.sample = [1, 2, {name: 'Ali'}];
$scope.$watch('sample', doSomething);
$scope.sample = [2, 3, {name: 'Mohammad'}]; // doSomething gets called
$scope.sample.name = 'Ali'; // doSomething doesn't get called

// By collection contents
// Watches for the object and its direct attributes changes
$scope.$watchCollection('sample', doSomething);
$scope.sample.name = {first: 'Ali', last: 'Mohammad'}; // doSomething gets called
$scope.sample.name.first = 'Mohammad'; // doSomething doesn't get called

// By value
// Watches for the object and its direct or indirect attributes changes
$scope.$watch('sample', doSomething, true);
// doSomething gets called any way sample changes
