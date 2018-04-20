# 模型字段类型

模型中的每个字段都是[Field](http://python.usyiyi.cn/documents/django_182/ref/models/fields.html#django.db.models.Field)子类的某个实例。Django 根据字段类的类型确定以下信息：

* 数据库当中的列类型 \(比如: INTEGER,VARCHAR\)。
* 渲染表单时使用的默认HTML[_部件_](http://python.usyiyi.cn/documents/django_182/ref/forms/widgets.html)（例如，&lt;inputtype="text"&gt;,&lt;select&gt;）。
* 最低限度的验证需求，它被用在 Django 管理站点和自动生成的表单中。

Django 自带数十种内置的字段类型；完整字段类型列表可以在[_模型字段参考_](http://python.usyiyi.cn/documents/django_182/ref/models/fields.html#model-field-types)中找到。如果内置类型仍不能满足你的要求，你可以自由地编写符合你要求的字段类型；详见[_编写自定义的模型字段_](http://python.usyiyi.cn/documents/django_182/howto/custom-model-fields.html)。

