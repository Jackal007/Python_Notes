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

现在Django知道要包含polls应用。 让我们运行另外一个命令：

```
$ python manage.py makemigrations polls
```



