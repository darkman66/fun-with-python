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
