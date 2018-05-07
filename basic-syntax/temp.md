# temp

首先来看看上述三个魔法方法的定义吧：

（1）\_\_getattr\_\_\(self, item\):

在访问对象的item属性的时候，如果对象并没有这个相应的属性，方法，那么将会调用这个方法来处理。。。这里要注意的时，假如一个对象叫fjs,  他有一个属性：fjs.name = "fjs"，那么在访问fjs.name的时候因为当前对象有这个属性，那么将不会调用\_\_getattr\_\_\(\)方法，而是直接返回了拥有的name属性了

（2）\_\_setattr\_\_\(self, item, value\):

当试图对象的item特性赋值的时候将会被调用。。

（3）\_\_getattribute\_\_\(self, item\):

这个只有在新式类中才有的，对于对象的所有特性的访问，都将会调用这个方法来处理。。。可以理解为在\_\_getattr\_\_之前

嗯。。。有了这几个方法就可以干很多很多的事情了。。。例如拦截器啥的。。。动态代理啥的。。。很方便就能实现了。。。起码比用java实现类似的功能方便多啦。。。。

不过需要注意的时候，在重写这些方法的时候需要特别的小心，因为容易引起循环调用。。。。

这里先来举一个例子，用于实现拦截所有的特性访问，在访问的时候打log啥的：**\[python\]** [view plain](https://blog.csdn.net/fjslovejhl/article/details/40683547#) [copy](https://blog.csdn.net/fjslovejhl/article/details/40683547#)

1. \# -\*- coding: utf-8 -\*-  
2. class Fjs\(object\):  
3.     def \_\_init\_\_\(self, name\):  
4.         self.name = name  
5. 6.     def hello\(self\):  
7.         print "said by : ", self.name  
8. 9.     def \_\_getattribute\_\_\(self, item\):  
10.         print "访问了特性：" + item  
11.         return object.\_\_getattribute\_\_\(self, item\)  
12. 13. 14. fjs = Fjs\("fjs"\)  
15. print fjs.name  
16. fjs.hello\(\)  

上述代码的输出如下：**\[python\]** [view plain](https://blog.csdn.net/fjslovejhl/article/details/40683547#) [copy](https://blog.csdn.net/fjslovejhl/article/details/40683547#)

1. 访问了特性：name  
2. fjs  
3. 访问了特性：hello  
4. said by :  访问了特性：name  
5. fjs  

很简单就实现了拦截的功能吧。。。而且这里可以知道\_\_getattribute\_\_方法拦截了属性和方法的访问。。这里也就是所谓的所有的特性的访问了。。不过要注意的是：\_\_getattribute\_\_只有在新式类中才能用的。。。

嗯。。接下来配合使用\_\_getattr\_\_和\_\_getattribute\_\_来实现一个非切入式的编程：**\[python\]** [view plain](https://blog.csdn.net/fjslovejhl/article/details/40683547#) [copy](https://blog.csdn.net/fjslovejhl/article/details/40683547#)

1. \# -\*- coding: utf-8 -\*-  
2. class Fjs\(object\):  
3.     def \_\_init\_\_\(self, name\):  
4.         self.name = name  
5. 6.     def hello\(self\):  
7.         print "said by : ", self.name  
8. 9.     def fjs\(self, name\):  
10.         if name == self.name:  
11.             print "yes"  
12.         else:  
13.             print "no"  
14. 15. class Wrap\_Fjs\(object\):  
16.     def \_\_init\_\_\(self, fjs\):  
17.         self.\_fjs = fjs  
18. 19.     def \_\_getattr\_\_\(self, item\):  
20.         if item == "hello":  
21.             print "调用hello方法了"  
22.         elif item == "fjs":  
23.             print "调用fjs方法了"  
24.         return getattr\(self.\_fjs, item\)  
25. 26. fjs = Wrap\_Fjs\(Fjs\("fjs"\)\)  
27. fjs.hello\(\)  
28. fjs.fjs\("fjs"\)  

这里通过\_\_getattr\_\_方法，将所有的特性的访问都路由给了内部的fjs对象。。。。。。

最后，关于\_\_setattr\_\_\(\)方法，这个就不细说了。。。不过他的使用还需要特别注意一些。。因为稍不注意就容易陷入循环调用了。。。。

