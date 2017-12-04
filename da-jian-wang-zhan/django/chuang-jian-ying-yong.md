项目和应用之间有什么不同？应用是一个Web应用程序，它完成具体的事项 —— 比如一个博客系统、一个存储公共档案的数据库或者一个简单的投票应用。项目是一个特定网站中相关配置和应用的集合。一个项目可以包含多个应用。一个应用可以运用到多个项目中去。

Django 应用是可以“热插拔”的，即可以在多个项目中使用同一个应用，也可以分发这些应用， 因为它们不需要与某个特定的Django安装绑定。

你的应用可以放在[Python path](https://docs.python.org/tutorial/modules.html#the-module-search-path)上的任何位置。在本教程中，我们将在你的manage.py文件同级目录创建我们的投票应用，以便可以将它作为顶层模块导入，而不是mysite的子模块。

要创建您的应用程序，请确保您与manage.py在同一目录中，并键入以下命令：

```
$ python manage.py startapp polls
```

这将创建一个目录polls，它的结构如下：

```
polls/
    __init__.py
    migrations/
        __init__.py
    admin.py
    models.py
    tests.py
    views.py
```

我们的polls应用将基于这个目录结构。

### 安装应用

编辑mysite/settings.py文件，并修改[INSTALLED\_APPS](http://python.usyiyi.cn/documents/django_182/ref/settings.html#std:setting-INSTALLED_APPS)设置以包含字符串'polls'。所以它现在是这样的：

mysite/settings.py

```py
INSTALLED_APPS = (
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'polls',
)
```

现在Django知道要包含polls应用。 让我们运行另外一个命令：

```
$ python manage.py makemigrations polls
```



