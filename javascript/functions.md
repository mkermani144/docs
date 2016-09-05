Useful Javascript functions
====


### `some`
##### From: `Array.prototype`
Returns `true` if at least one of the elements of the array passes the test in the callback, and `false` otherwise.
```js
[2, 4, 12].some(element => element > 10); // Returns true
['Ali', 'Reza', 'Mohsen'].some(element => element.length === 2); // Returns false
