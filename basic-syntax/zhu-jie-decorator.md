---
description: 'https://coolshell.cn/articles/11265.html'
---

# 注解 Decorator

```python
def hello(fn): 
    def wrapper(): 
        print "hello, %s" % fn.__name__ fn() 
        print "goodby, %s" % fn.__name__ 
    return wrapper
    
    @hello
    def foo(): 
        print "i am foo"foo()
```

