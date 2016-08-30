Dependency injection
====
```js
// Implicit injection of $http
angular.module('MainApp', [])
    .service('aService', function($http){
      // Some code
    });
// Explicit injection of $http
angular.module('MainApp', [])
    .service('aService', ['$http', function($http){
      // Some code
    }]);
```
__What is the benefit of Explicit DI over implicit DI?__

It's about minifying, that is:
```js
// Implicit injection of $http
angular.module('MainApp', [])
    .service('aService', function(a){ // <-- Error happens because
                                      // angular does not know a
      // Some code
    });
// Explicit injection of $http
angular.module('MainApp', [])
    .service('aService', ['$http', function(a){ // <-- No error occurs.
                                                // Angular knows a is $http
      // Some code
    }]);
```

To-do
----
- [ ] `$inject`
