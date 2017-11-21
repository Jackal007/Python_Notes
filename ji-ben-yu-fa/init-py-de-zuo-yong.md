> from：[https://www.cnblogs.com/Lands-ljk/p/5880483.html](https://www.cnblogs.com/Lands-ljk/p/5880483.html)

\_\_init\_\_.py 文件的作用是将文件夹变为一个Python模块,Python 中的每个模块的包中，都有\_\_init\_\_.py 文件。

通常\_\_init\_\_.py 文件为空，但是我们还可以为它增加其他的功能。我们在导入一个包时，实际上是导入了它的\_\_init\_\_.py文件。这样我们可以在\_\_init\_\_.py文件中批量导入我们所需要的模块，而不再需要一个一个的导入。

```
# package
# __init__.py
import re
import urllib
import sys
import os

# a.py
import package 
print(package.re, package.urllib, package.sys, package.os)
```

注意这里访问\_\_init\_\_.py文件中的引用文件，需要加上包名。

\_\_init\_\_.py中还有一个重要的变量，\_\_all\_\_, 它用来将模块全部导入。

```
# __init__.py
__all__ = ['os', 'sys', 're', 'urllib']

# a.py
from package import *
```

这时就会把注册在\_\_init\_\_.py文件中\_\_all\_\_列表中的模块和包导入到当前文件中来。

可以了解到，\_\_init\_\_.py主要控制包的导入行为。要想清楚理解\_\_init\_\_.py文件的作用，还需要详细了解一下import语句引用机制：

可以被import语句导入的对象是以下类型：

* 模块文件（.py文件）
* C或C++扩展（已编译为共享库或DLL文件）
* 包（包含多个模块）
* 内建模块（使用C编写并已链接到Python解释器中）

当导入模块时，解释器按照sys.path列表中的目录顺序来查找导入文件。

```
import sys
>>> print(sys.path)

# Linux:
['', '/usr/local/lib/python3.4',
 '/usr/local/lib/python3.4/plat-sunos5',
 '/usr/local/lib/python3.4/lib-tk',
 '/usr/local/lib/python3.4/lib-dynload',
 '/usr/local/lib/python3.4/site-packages']

# Windows:
['', 'C:\\WINDOWS\\system32\\python34.zip', 'C:\\Documents and Settings\\weizhong', 'C:\\Python34\\DLLs', 'C:\\Python34\\lib', 'C:\\Python34\\lib\\plat-win', 'C:\\Python34\\lib\\lib-tk', 'C:\\Python34\\Lib\\site-packages\\pythonwin', 'C:\\Python34', 'C:\\Python34\\lib\\site-packages', 'C:\\Python34\\lib\\site-packages\\win32', 'C:\\Python34\\lib\\site-packages\\win32\\lib', 'C:\\Python34\\lib\\site-packages\\wx-2.6-msw-unicode']
```

其中list第一个元素空字符串代表当前目录。

**关于.pyc 文件 与 .pyo 文件**

.py文件的汇编,只有在import语句执行时进行，当.py文件第一次被导入时，它会被汇编为字节代码，并将字节码写入同名的.pyc文件中。后来每次导入操作都会直接执行.pyc 文件（当.py文件的修改时间发生改变，这样会生成新的.pyc文件），在解释器使用-O选项时，将使用同名的.pyo文件，这个文件去掉了断言（assert）、断行号以及其他调试信息，体积更小，运行更快。（使用-OO选项，生成的.pyo文件会忽略文档信息）

**导入模块**

模块通常为单独的.py文件，可以用import直接引用，可以作为模块的文件类型有.py、.pyo、.pyc、.pyd、.so、.dll

在导入模块时，解释器做以下工作：

1. 已导入模块的名称创建新的命名空间，通过该命名空间就可以访问导入模块的属性和方法。

2. 在新创建的命名空间中执行源代码文件。

3. 创建一个名为源代码文件的对象，该对象引用模块的名字空间，这样就可以通过这个对象访问模块中的函数及变量

import 语句可以在程序的任何位置使用，你可以在程序中多次导入同一个模块，但模块中的代码仅仅在该模块被首次导入时执行。后面的import语句只是简单的创建一个到模块名字空间的引用而已。

sys.modules字典中保存着所有被导入模块的模块名到模块对象的映射。

**导入包**

多个相关联的模块组成一个包，以便于维护和使用，同时能有限的避免命名空间的冲突。一般来说，包的结构可以是这样的：

```
package

  |- subpackage1
      |- __init__.py
      |- a.py
  |- subpackage2
      |- __init__.py
      |- b.py
```

有以下几种导入方式：

```
import subpackage1.a # 将模块subpackage1.a导入全局命名空间，例如访问a中属性时用subpackage1.a.attr
from subpackage1 import a #　将模块a导入全局命名空间，例如访问a中属性时用a.attr_a
from subpackage.a import attr_a # 将模块a的属性直接导入到命名空间中，例如访问a中属性时直接用attr_a
```

使用from语句可以把模块直接导入当前命名空间，from语句并不引用导入对象的命名空间，而是将被导入对象直接引入当前命名空间。

