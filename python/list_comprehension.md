List comprehensions
====


```python
a = [1, 2, 3]
s = ['a', 'b', 'c']
# Basic
b = [x**2 for x in a] # b = [1, 4, 9]
# Conditional
b = [x**2 for x in a if x > 1] # b = [4, 9]
# Nested
c = [a + b for a in s for b in s] # c = ['aa', 'ab', 'ac', 'ba', 'bb', 'bc', 'ca', 'cb', 'cc']
# Nested, conditional
c = [a + b for a in s if a != 'b' for b in s if a != 'c'] # c = ['aa', 'ab', 'ca', 'cb']
# More nesting
c = [a + b + c for a in s for b in s for c in s] # c = ['aaa', 'aab', ...]
```
