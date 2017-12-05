## 编写你的第一个视图 {#yiyi-142}

我们来写第一个视图。打开文件`polls/views.py`，并在其中放入以下Python代码：

polls/views.py

```py
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello, world. You're at the polls index.")
```

这是Django中最简单的视图。要调用视图，我们需要将其映射到URL — 为此我们需要一个URLconf。

要在polls目录中创建一个URLconf，请创建一个名为`urls.py`的文件。你的应用的目录应该如下所示：

```
polls/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    urls.py
    views.py
```

在`polls/urls.py`文件中包含以下代码：

polls/urls.py

```py
from django.conf.urls import url

from . import views

urlpatterns = [
    url(r'^$', views.index, name='index'),
]
```

下一步是将根URLconf指向`polls.urls`模块。在`mysite/urls.py`中，添加一个`django.conf.urls.include`导入并且插入[`include()`](http://usyiyi.cn/documents/Django_111/ref/urls.html#django.conf.urls.include)到`urlpatterns`列表, 这样你就有了：

mysite/urls.py

```py
from django.conf.urls import include, url
from django.contrib import admin

urlpatterns = [
    url(r'^polls/', include('polls.urls')),
    url(r'^admin/', admin.site.urls),
]
```

[`include()`](http://usyiyi.cn/documents/Django_111/ref/urls.html#django.conf.urls.include)函数允许引用其他URLconfs。请注意，[`include()`](http://usyiyi.cn/documents/Django_111/ref/urls.html#django.conf.urls.include)函数的正则表达式不具有`$`（字符串结束匹配符），而是尾部斜线。每当Django遇到[`include()`](http://usyiyi.cn/documents/Django_111/ref/urls.html#django.conf.urls.include)时，它将删除与此相匹配的URL部分，并将剩余的字符串发送到包含的URLconf进行进一步处理。

[`include()`](http://usyiyi.cn/documents/Django_111/ref/urls.html#django.conf.urls.include)背后的想法是即插即用使网址变得容易。由于投票应用是在自己的URLconf（`polls/urls.py`）中，它们可以放在“/polls/”下或“/fun\_polls/”下或“/content/polls/”下，或任何其他路径根，并且应用程序仍然可以工作。



