# 配置数据库

> from：[http://blog.csdn.net/it\_dream\_er/article/details/52092262](http://blog.csdn.net/it_dream_er/article/details/52092262)

## 配置MySQL数据库

这是settings文件里面的基础配置，使用的是sqlite,那我们需要连接其他数据库呢？

1. `DATABASES = {`
2. `'default': {`
3. `'ENGINE': 'django.db.backends.sqlite3',`
4. `'NAME': 'mydatabase',`
5. `}`
6. `}` 

下面是**mysql**的配置方法：

1. `DATABASES = {`
2. `'default': {`
3. `'ENGINE': 'django.db.backends.mysql',`
4. `'NAME': 'mydatabase',`
5. `'USER': 'mydatabaseuser',`
6. `'PASSWORD': 'mypassword',`
7. `'HOST': '127.0.0.1',`
8. `'PORT': '3306',`
9. `}`
10. `}`

下面解释一下，里面参数的意思：

ENGINE : 指定数据库驱动，不同的数据库这个字段不同，下面是常见的集中数据库的ENGINE的写法：

1. `django.db.backends.postgresql  # PostgreSQL`
2. `django.db.backends.mysql       # mysql`
3. `django.db.backends.sqlite3     # sqlite`
4. `django.db.backends.oracle      # oracle`

NAME: 指定的数据库名，如果是sqlite的话，就需要填数据库文件的绝对位置

USER: 数据库登录的用户名，mysql一般都是root

PASSWORD：登录数据库的密码，必须是USER用户所对应的密码

HOST: 由于一般的数据库都是C/S结构的，所以得指定数据库服务器的位置，我们一般数据库服务器和客户端都是在一台主机上面，所以一般默认都填127.0.0.1

PORT：数据库服务器端口，mysql默认为3306

HOST和PORT都可以不填，使用默认的配置，但是如果你有更改默认配置的话，就需要填入更改后的

配置完这，只是最简单的一步，下面就需要装python连接mysql数据库的驱动程序（见官网教程）

安装好后，启动django

1. python manager.py runserver  

如果没有出现报错，则表明配置正常，然后在新的shell运行：

1. python manager.py shell  

输入以下命令：

1. from django.db import connection  
2. cursor = connection.cursor\(\)  

如果没有报错，则就表明安装成功，你可以尽情使用django的数据库功能了

