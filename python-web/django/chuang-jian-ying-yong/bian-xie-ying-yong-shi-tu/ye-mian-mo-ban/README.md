# 页面模板

作为Web 框架，Django 需要一种很便利的方法以动态地生成HTML。最常见的做法是使用模板。模板包含所需HTML 输出的静态部分，以及一些特殊的语法，描述如何将动态内容插入。创建HTML 页面模板的一个示例，参见[Tutorial 3](http://usyiyi.cn/documents/Django_111/intro/tutorial03.html)。

Django 项目可以配置一个或多个模板引擎（甚至是零，如果你不需要使用模板）。Django 的模板系统自带内建的后台 —— 称为Django 模板语言（DTL），以及另外一种流行的[Jinja2](http://jinja.pocoo.org/)。其他的模板语言的后端，可查找第三方库。

Django 为加载和渲染模板定义了一套标准的API，与具体的后台无关。加载包括根据给定的标识找到模板然后预处理，通常会将它编译好放在内存中。渲染表示使用Context 数据对模板插值并返回生成的字符串。

[Django template language](http://usyiyi.cn/documents/Django_111/ref/templates/language.html)是Django 原生的模板系统。直到Django 1.8，这是唯一可用的内置选项。尽管，它闭门造车，并且偏重某些方面，但是它仍然是一个优秀的模版库。如果没有特别紧急的理由选择另外一种后台，你应该使用DTL，特别是你编写可插拔的应用并打算发布其模板的时候。Django 中包含模板的标准应用，例如[django.contrib.admin](http://usyiyi.cn/documents/Django_111/ref/contrib/admin/index.html)，都使用DTL。

又由于历史遗留原因,通用支持的模板引擎和Django实现的模板语言都在`django.template`命名空间中。

## 配置 {#yiyi-25}

模板引擎通过[`TEMPLATES`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-TEMPLATES)设置来配置。它是一个设置选项列表，与引擎一一对应。默认的值为空。由[`startproject`](http://usyiyi.cn/documents/Django_111/ref/django-admin.html#django-admin-startproject)命令生成的`settings.py`定义了一些有用的值：

```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [],
        'APP_DIRS': True,
        'OPTIONS': {
            # ... some options here ...
        },
    },
]
```

[`BACKEND`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-TEMPLATES-BACKEND)是一个指向实现了Django模板后端API的模板引擎类的带点的Python路径。内置的后端有[`django.template.backends.django.DjangoTemplates`](http://usyiyi.cn/documents/Django_111/topics/templates.html#django.template.backends.django.DjangoTemplates)和[`django.template.backends.jinja2.Jinja2`](http://usyiyi.cn/documents/Django_111/topics/templates.html#django.template.backends.jinja2.Jinja2)。

由于绝大多数引擎都是从文件加载模板的，所以每种模板引擎都包含两项通用设置：

* [`DIRS`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-TEMPLATES-DIRS)

  定义了一个目录列表，模板引擎按列表顺序搜索这些目录以查找模板源文件。

* [`APP_DIRS`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-TEMPLATES-APP_DIRS)

  告诉模板引擎是否应该进入每个已安装的应用中查找模板。

  每种模板引擎后端都定义了一个惯用的名称作为应用内部存放模板的子目录名称。（译者注：例如django为它自己的模板引擎指定的是 ‘templates’ ，为jinja2指定的名字是‘jinja2’）

特别的是，django允许你有多个模板引擎后台实例，且每个实例有不同的配置选项。在这种情况下你必须为每个配置指定一个唯一的[`NAME`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-TEMPLATES-NAME).

[`OPTIONS`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-TEMPLATES-OPTIONS)中包含了具体的backend设置

