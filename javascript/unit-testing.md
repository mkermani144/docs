Unit testing with `mocha`
====


Installation
----
```bash
sudo npm -g install mocha
```


Usage
----
```bash
mocha testFile.js
# Or if the test file is named test.js
mocha
```


Testing basics
----
`test.js`:
```js
var assert = require('assert');
describe('Test spec', () => {
  describe('#indexOf()', () => {
    it('should return -1 when the value is not present', () => {
      assert.equal(-1, [1,2,3].indexOf(4));
    });
  });
});
```
