Directives
====
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
})
```
`index.html`:
```html
<div>
  <sample-element></sample-element>
  <!-- Equivalent for:
  <p>Sample element</p>
  -->
</div>
```
