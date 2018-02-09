如果要把一个类的实例变成** str**，就需要实现特殊方法\_\_str\_\_\(\)：

[![](https://common.cnblogs.com/images/copycode.gif "复制代码")](javascript:void%280%29;)

```
>
>
>
class
 Person(object):
    
def
__init__
(self,name,gender):
        self.name 
=
 name
        self.gender 
=
gender
    
def
__str__
(self):
        
return
'
(Person:%s,%s)
'
%
(self.name,self.gender)

    

>
>
>
 p = Person(
'
Bob
'
,
'
male
'
)

>
>
>
print
 (p)
(Person:Bob,male)
```

[![](https://common.cnblogs.com/images/copycode.gif "复制代码")](javascript:void%280%29;)

但是当我们输入p的时候我们并不能显示出字符串

```
>
>
>
 p

<
__main__
.Person object at 0x035FC950
>
```

好像是\_\_str\_\_并没有调用

因为 Python 定义了**\_\_str\_\_\(\)**和**\_\_repr\_\_\(\)**两种方法，\_\_str\_\_\(\)用于显示给用户，而**\_\_repr\_\_\(\)**用于显示给开发人员。

有一个偷懒的定义\_\_repr\_\_的方法：

[![](https://common.cnblogs.com/images/copycode.gif "复制代码")](javascript:void%280%29;)

```
>
>
>
class
 Person(object):
    
def
__init__
(self,name,gender):
        self.name 
=
 name
        self.gender 
=
gender
    
def
__str__
(self):
        
return
'
(Person:%s,%s)
'
%
(self.name,self.gender)
    
__repr__
 = 
__str__
>
>
>
 p = Person(
'
Bob
'
,
'
Male
'
)

>
>
>
 p
(Person:Bob,Male)
```

[![](https://common.cnblogs.com/images/copycode.gif "复制代码")](javascript:void%280%29;)

这里我们在输入P的时候就不会显示出地址了。

