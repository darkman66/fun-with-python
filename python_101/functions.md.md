# standard

```
def foo(arg1, arg2):
    return args1 + arg2

foo(1,2)
```

with more args

```
def foo(*args):
    return sum(args)

foo(1,2,3,4,5,6,7,8)
```

with named args

```
def foo(arg1, arg2):
    return arg1 + arg2

foo(2, arg2=5)
```

with dynamic named args
```
def foo(arg1, arg2, **kwargs):
    return arg1 + arg2 + sum([v for v in kwargs.values()])

foo(2, arg2=5, v1=10, v2=15, v3=5)
```

with mixed args

```
def foo(arg1, arg2, *args, **kwargs):
    result = arg1 + arg2 + sum(args)
    if kwargs and kwargs.get('multi'):
        return result * kwargs['multi']
    return result

foo(2, 5, 1, 2 ,3, multi=10)
foo(2, 5, 1, 2 ,3, ignore_arg=123)
```

With better and cleaner types definition

```
from typing import List, Dict


def foo(arg1: int, arg2: int, *args: List[int], **kwargs: Dict[str, int]):
    result = arg1 + arg2 + sum(args)
    if kwargs and kwargs.get('multi'):
        return result * kwargs['multi']
    return result

value_1 = foo(2, 5, 1, 2 ,3, multi=10)
value_2 = foo(2, 5, 1, 2 ,3, ignore_arg=123)

print(value_1)
print(value_2)
```

# scopes

## global

```Python
# file func1.py
def foo():
    SOME_VAR = "x"
    
# file func2.py
SOME_VAR = "abc"
def foo2():
    global SOME_VAR
    print(SOME_VAR)
    
# file func3.py
from func1 import foo
from func2 import foo2, SOME_VAR


def foo3():
    global SOME_VAR
    SOME_VAR = "here i am"
    
foo2()
foo3()
foo2()
print(SOME_VAR)
```
