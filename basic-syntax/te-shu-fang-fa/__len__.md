# \_\_len\_\_

```text
class
```

```text
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

![&#x590D;&#x5236;&#x4EE3;&#x7801;](https://common.cnblogs.com/images/copycode.gif)

要让 **len\(\) **函数工作正常，类必须提供一个特殊方法\_\_len\_\_\(\)，它返回元素的个数。

