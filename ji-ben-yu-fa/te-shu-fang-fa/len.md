```
class
```

```
 Student(object):
    
def
__init__
(self,*
args):
        self.names 
=
 args
    
def
__len__
(self):
        
return
 len(self.names)

    

>
>
>
 L = Student(
'
Bob
'
,
'
Alice
'
,
'
Tim
'
)

>
>
>
print
 (len(L))

3
```

[![](https://common.cnblogs.com/images/copycode.gif "复制代码")](javascript:void%280%29;)

要让 **len\(\) **函数工作正常，类必须提供一个特殊方法\_\_len\_\_\(\)，它返回元素的个数。

