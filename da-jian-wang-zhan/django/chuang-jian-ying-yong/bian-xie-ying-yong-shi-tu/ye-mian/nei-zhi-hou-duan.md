# 内置后端

_class_`DjangoTemplates`

设置[`BACKEND`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-TEMPLATES-BACKEND)为`'django.template.backends.django.DjangoTemplates'`来配置Django模板引擎。

当[`APP_DIRS`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-TEMPLATES-APP_DIRS)为`templates`时,`True`引擎会在已安装应用的`DjangoTemplates`子目录中查找模板文件。这个通用名称是保持向后兼容的。

`DjangoTemplates`引擎[`OPTIONS`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-TEMPLATES-OPTIONS)配置项中接受以下参数:

* `'autoescape'`：一个布尔值，用于控制是否启用HTML自动转义。

  它默认为`True`。

* `'context_processors'`: 是一个包含以"."为分隔符的python调用路径的列表，在一个template被request渲染时，它可以被调用以产生context的数据。这些可调用要求一个请求对象作为其参数，并返回要合并到上下文中的项目的[`dict`](https://docs.python.org/3/library/stdtypes.html#dict)。

  它默认是个空的 list。  
  有关详细信息，请参阅[`RequestContext`](http://usyiyi.cn/documents/Django_111/ref/templates/api.html#django.template.RequestContext)。

* `'debug'`：打开/关闭模板调试模式的布尔值。如果它`True`，那么奇怪的错误页面将显示模板渲染期间引发的任何异常的详细报告。此报告包含模板的相关代码段，并突出显示相应的行。

  它默认和setting中的[`DEBUG`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-DEBUG)有相同的值。

* `'loaders'`：模板加载器类的虚拟Python路径列表。每个`Loader`类知道如何从特定源导入模板。你可以选择使用字符串元组来代替字符串。元组的第一项是`Loader`类名，接下来的项在初始化期间会被传递给`Loader`。

  默认值取决于[`DIRS`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-TEMPLATES-DIRS)和[`APP_DIRS`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-TEMPLATES-APP_DIRS)的值。

  有关详细信息，请参见[Loader types](http://usyiyi.cn/documents/Django_111/ref/templates/api.html#template-loaders)。

* `'string_if_invalid'`：作为字符串的输出，模板系统应该用于无效（例如拼写错误的）变量。

  它默认为空字符串。

  有关详细信息，请参见[How invalid variables are handled](http://usyiyi.cn/documents/Django_111/ref/templates/api.html#invalid-template-variables)。

* `'file_charset'`：用于读取磁盘上的模板文件的字符集。

  它默认为[`FILE_CHARSET`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-FILE_CHARSET)的值。

* `'libraries'`：模板标签模块的标签和点缀Python路径的字典，用于注册模板引擎。这可以用于添加新的库或为现有库添加备用标签。像这样：

* ```py
  OPTIONS={
      'libraries': {
          'myapp_tags': 'path.to.myapp.tags',
          'admin.urls': 'django.contrib.admin.templatetags.admin_urls',
      },
  }
  ```
  
可以通过将相应的字典键传递到[`{%load%}`](http://usyiyi.cn/documents/Django_111/ref/templates/builtins.html#std:templatetag-load)标记来加载库。

* `'builtins'`：添加到[built-ins](http://usyiyi.cn/documents/Django_111/ref/templates/builtins.html)的模板标签模块的点缀Python路径列表。像这样：

  ```py
  OPTIONS={
      'builtins': ['myapp.builtins'],
  }
  ```

  标签和内置库的过滤器可以在没有首先调用[`{%load%}`](http://usyiyi.cn/documents/Django_111/ref/templates/builtins.html#std:templatetag-load)标签的情况下使用。



