# 用法

`django.template.loader`定义了两个函数以加载模板。

* `get_template`（_template\_name_，_using = None_） 该函数使用给定的名称加载模板并返回一个`Template`对象. 真正的返回值类型取决于那个用来加载模版的后台引擎。每个后台都有各自的`Template`类。 `get_template()`尝试获取每个模板直到有一个成功满足。如果模板不能成功找到，将会抛出[`TemplateDoesNotExist`](http://usyiyi.cn/documents/Django_111/topics/templates.html#django.template.TemplateDoesNotExist)。如果能够找到模板但是包含非法值，将会抛出[`TemplateSyntaxError`](http://usyiyi.cn/documents/Django_111/topics/templates.html#django.template.TemplateSyntaxError)。 模板的查找和加载机制取决于每种后台引擎和配置 如果你想使用指定的模板引擎进行查找,请将模板引擎的[`NAME`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-TEMPLATES-NAME)赋给 get\_template的`using`参数
* `select_template`（_template\_name\_list_，_using = None_） `get_template()`和`select_template()`很相似, 只不过它用了一个模板名称的列表作为参数。按顺序搜索模板名称列表内的模板并返回第一个存在的模板。

由`select_template()`和`get_template()`返回的`Template`对象必须要有一个`render()`方法，协议如下：

`Template.render`\(_context=None_,_request=None_\)

通过给定的 context 对该模板进行渲染。

如果提供了`context`，那么它必须是一个[`dict`](https://docs.python.org/3/library/stdtypes.html#dict)对象.如果没有提供，引擎将是用空 context 对模板进行渲染。

如果要提供`request`参数 ，必须使用[`HttpRequest`](http://usyiyi.cn/documents/Django_111/ref/request-response.html#django.http.HttpRequest)对象.之后模板引擎会使它连同CSRF token一起在模板中可用。具体如何实现由相应模板后端决定。

> 如果可能（其实这会更好）—将模版文件，放在包含模版的目录的子目录下。基本思路是，使得每个APP的的模版子目录下都有一个子目录来唯一对应这个APP。
>
> 这样做可以增强你的APP可用性。将所有的模版放在根模版目录下会引发混淆。

另外，为了减少加载模板、渲染模板等重复工作，django提供了处理这些工作的快捷函数。

`render_to_string`\(_template\_name_,_context=None_,_request=None_,_using=None_\)

`render_to_string()`会像[`get_template()`](http://usyiyi.cn/documents/Django_111/topics/templates.html#django.template.loader.get_template)一样加载模板并立即调用`render()`方法。它需要以下参数。

`TEMPLATE_NAME`要加载和呈现的模板的名称。如果是模板名称列表，Django使用[`select_template()`](http://usyiyi.cn/documents/Django_111/topics/templates.html#django.template.loader.select_template)而不是

[`get_template()`](http://usyiyi.cn/documents/Django_111/topics/templates.html#django.template.loader.get_template)来查找模板。`context`要用作模板的上下文进行渲染的[`dict`](https://docs.python.org/3/library/stdtypes.html#dict)。

`request`[`HttpRequest`](http://usyiyi.cn/documents/Django_111/ref/request-response.html#django.http.HttpRequest)是可选的，并且在整个模版渲染期都是可用的。

`using`一个可选的模板引擎[`NAME`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-TEMPLATES-NAME)。

搜索模板将仅限于该引擎。

用法示例：

```python
from django.template.loader import render_to_string
rendered = render_to_string('my_template.html', {'foo': 'bar'})
```

另请参阅调用[`render_to_string()`](http://usyiyi.cn/documents/Django_111/topics/templates.html#django.template.loader.render_to_string)的[`render()`](http://usyiyi.cn/documents/Django_111/topics/http/shortcuts.html#django.shortcuts.render)快捷方式，并将结果馈送到适合从视图返回的[`HttpResponse`](http://usyiyi.cn/documents/Django_111/ref/request-response.html#django.http.HttpResponse)。

最后，您可以直接使用配置的引擎：`engines`

模板引擎可在`django.template.engines`中使用：

```python
from django.template import engines

django_engine = engines['django']
template = django_engine.from_string("Hello {{ name }}!")
```

在此示例中，查找键 -`'django'`是引擎的[`NAME`](http://usyiyi.cn/documents/Django_111/ref/settings.html#std:setting-TEMPLATES-NAME)。

