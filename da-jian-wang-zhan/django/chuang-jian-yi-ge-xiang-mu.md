## 项目

```py
$ django-admin startproject mysite
```

让我们看一下[startproject](http://python.usyiyi.cn/documents/django_182/ref/django-admin.html#django-admin-startproject)生成了什么：

```
mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        wsgi.py
```

* 外层的mysite/根目录仅仅是项目的一个容器。它的命名对Django无关紧要；你可以把它重新命名为任何你喜欢的名字。
* manage.py：一个命令行工具，可以使你用多种方式对Django项目进行交互。你可以在[_django-admin和manage.py_](http://python.usyiyi.cn/documents/django_182/ref/django-admin.html)中读到关于manage.py的所有细节。
* 内层的mysite/目录是你的项目的真正的Python包。它是你导入任何东西时将需要使用的Python包的名字（例如mysite.urls）。
* mysite/\_\_init\_\_.py：一个空文件，它告诉Python这个目录应该被看做一个Python包。
  （如果你是一个Python初学者，[关于包的更多内容](https://docs.python.org/tutorial/modules.html#packages)请阅读Python的官方文档）。
* mysite/settings.py：该Django 项目的设置/配置。[_Django 设置_](http://python.usyiyi.cn/documents/django_182/topics/settings.html)将告诉你这些设置如何工作。
* mysite/urls.py：该Django项目的URL声明；你的Django站点的“目录”。你可以在[_URL 转发器_](http://python.usyiyi.cn/documents/django_182/topics/http/urls.html)中阅读到更多关于URL的内容。
* mysite/wsgi.py：用于你的项目的与WSGI兼容的Web服务器入口。更多细节请参见[_如何利用WSGI进行部署_](http://python.usyiyi.cn/documents/django_182/howto/deployment/wsgi/index.html)。



