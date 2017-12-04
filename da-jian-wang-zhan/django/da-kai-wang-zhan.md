让我们验证一下你的Django项目是否工作。如果你不在外层的mysite目录下，那么进入这个目录，然后运行以下命令：

```py
$ python manage.py runserver
```

你将看到命令行下输出了以下内容：

```
Performing system checks...

0 errors found
May 13, 2015 - 15:50:53
Django version 1.8, using settings 'mysite.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

这表明你已经启动了Django开发服务器，一个用纯Python写的轻量级Web服务器。我们在Django中内置了它，这样你就可以在不配置用于生产环境的服务器 —— 例如Apache —— 的情况下快速开发出产品，直到你准备好上线。

请注意：**不要**在任何生产环境使用这个服务器。它仅仅是用于在开发中使用。（我们的重点是编写Web框架，非Web服务器。）

既然服务器已经运行，请用你的浏览器访问[http://127.0.0.1:8000/](http://127.0.0.1:8000/)。在淡蓝色背景下，你将看到一个“Welcome to Django”的页面。它运行成功了！

更改端口

默认情况下，[runserver](http://python.usyiyi.cn/documents/django_182/ref/django-admin.html#django-admin-runserver)命令在内部IP的8000端口启动开发服务器。

如果你需改变服务器的端口，把要使用的端口作为一个命令行参数传递给它。例如，这个命令在8080端口启动服务器：

```
$ python manage.py runserver 8080
```

如果你需改变服务器的IP地址，把IP地址和端口号放到一起。因此若要监听所有的外网IP，请使用（如果你想在另外一台电脑上展示你的工作，会非常有用）：

```
$ python manage.py runserver 0.0.0.0:8000
```

开发服务器的所有文档可以在[runserver](http://python.usyiyi.cn/documents/django_182/ref/django-admin.html#django-admin-runserver)的参考手册中找到。

[runserver](http://python.usyiyi.cn/documents/django_182/ref/django-admin.html#django-admin-runserver)的自动重载

开发服务器会根据需要自动重新载入Python代码。你不必为了使更改的代码生效而重启服务器。然而，一些行为比如添加文件，不会触发服务器的重启，所以在这种情况下你需要手动重启服务器。

