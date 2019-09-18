---
title: "Python: First Contact"
date: 2019-05-06T09:08:18+01:00
draft: false
---

I am very excited to learn Python because this language
**builds a bridge** between science and software development, opening
doors for working side-by-side between us.

# 🐍 ➡ ⚗️👩🏾‍🔬🤝🏻‍👨🏿‍💻📚

In this post I will highlight the things I consider the most important and
surprising for a person like me, more used to **JavaScript** and
**TypeScript**.

### Functions
Functions are defined as below and the arguments can have a `default` value, just
like in JavaScript:
```
def sum(x, y=1, z):
  return x+y+z
```
But you can call a function **without specifying** the value of **any** argument:
```
# Not informing a value for `y`:
my_function(z=2, x=3) # => 6
```
This means the function learns the name of their arguments. That's something
you can't do in JavaScript:
```
# In JavaScript we can't miss an argument before
# another argument that we want to inform.
>> function sum(x, y=1, z) { return x+y+z; }
<=undefined
>>sum(x=1, y=1, z=1)
<=3
>>sum(x=1, z=1)
<=NaN
```
**Is that helpful?**: I would say this helps in cases we need method overloading that is usually
allowed in other languages but not in Python.

**DANGER**: It is dangerous to set an empty list as a default value for a function argument
because, when using the argument, the list reference will be shared accross all the method calls.
In other words; the list is initialized only *once* when the method is defined.
```
# Don't do this:
def append_element_to_list(element, list=[])
    list.append(element)

# Do this instead:
def append_element_to_list(element, list=None):
  if list is None:
    list = []
  list.append(element)
  return list
```

In my repository [python-welcome-party](https://github.com/RosanaRufer/python-welcome-party)
you will be able to do a test-driven exercise to experiment this by running the
`test_python_functions.py` tests.
