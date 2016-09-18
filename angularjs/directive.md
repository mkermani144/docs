Directives
====


Basics
----

`app.js`:
```js
var module = angular.module('MainApp', []);

/**
 * Directive as element
 */
module.directive('sample-element', () => {
  return {
    restrict: 'E', // E for element
    template: '<p>Sample element</p>'
  }
});

/**
 * Directive as attribute
 */
module.directive('sample-attr', () => {
  return {
    restrict: 'A', // A for attribute
    link: () => {
      console.log('sample-attr was used.');
    }
  }
});
```
`index.html`:
```html
<!-- Using new element -->
<div>
  <sample-element></sample-element>
  <!-- Equivalent for:
  <p>Sample element</p>
  -->
</div>

<!-- Using new attribute -->
<div>
  <h1 sample-attr></h1>
  <!-- String will be logged in console -->
</div>
```
