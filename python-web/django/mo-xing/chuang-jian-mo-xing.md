# 创建模型

当编写一个数据库驱动的Web应用时，第一步就是定义该应用的模型 —— 本质上，就是定义该模型所对应的数据库设计及其附带的元数据。

模型指出了数据的唯一、明确的真实来源。它包含了正在存储的数据的基本字段和行为。Django遵循[_DRY \(Don't repeat yourself\)原则_](http://python.usyiyi.cn/documents/django_182/misc/design-philosophies.html#dry)。这个原则的目标是在一个地方定义你的数据模型，并自动从它获得需要的信息。

迁移工具也符合以上哲学 —— 这不同于Ruby On Rails中的迁移；例如，迁移完全依照于你的模型文件且本质上只是一个历史记录，Django通过这个历史记录更新你的数据库模式使它与你现在的模型文件保持一致。

在这个简单的投票应用中，我们将创建两个模型：Question和Choice。Question对象具有一个question\_text（问题）属性和一个publish\_date（发布时间）属性。Choice有两个字段：选择的内容和选择的得票统计。每个Choice与一个Question关联。

这些概念通过简单的Python类来表示。编辑polls/models.py文件，并让它看起来像这样：

polls/models.py

```python
from django.db import models

class Question(models.Model):
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

class Choice(models.Model):
    question = models.ForeignKey(Question)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
```

上述代码非常直观。每个模型都用一个类表示，该类继承自[django.db.models.Model](http://python.usyiyi.cn/documents/django_182/ref/models/instances.html#django.db.models.Model)。每个模型都有一些类变量，在模型中每个类变量都代表了数据库中的一个字段。

每个字段通过[Field](http://python.usyiyi.cn/documents/django_182/ref/models/fields.html#django.db.models.Field)类的一个实例表示 —— 例如字符字段[CharField](http://python.usyiyi.cn/documents/django_182/ref/models/fields.html#django.db.models.CharField)和日期字段[DateTimeField](http://python.usyiyi.cn/documents/django_182/ref/models/fields.html#django.db.models.DateTimeField)。这种方法告诉Django，每个字段中保存着什么类型的数据。

每个[Field](http://python.usyiyi.cn/documents/django_182/ref/models/fields.html#django.db.models.Field)实例的名字（例如question\_text或pub\_date）就是字段的名字，并且是机器可读的格式。你将在Python代码中使用到它的值，并且你的数据库将把它用作表的列名。

你可以使用[Field](http://python.usyiyi.cn/documents/django_182/ref/models/fields.html#django.db.models.Field)的第一个参数来指定一个人类可读的名字，这是可选的。它在Django的内省机制中有使用，而且可以兼作文档。如果没有提供这个参数，Django将使用那个机器可读的名字（实例名）。在这个例子中，我们只为Question.pub\_date定义一个人类可读的名字。 对于这个模型中其他的字段，机器可读的名字（实例名）足以充分地表达出它的含义。

某些[Field](http://python.usyiyi.cn/documents/django_182/ref/models/fields.html#django.db.models.Field)类具有必选的参数。例如，CharField要求您给它一个max\_length。这个参数不仅用于数据库模式，而且数据验证中也会用到，我们稍后会看到。

[Field](http://python.usyiyi.cn/documents/django_182/ref/models/fields.html#django.db.models.Field)还具有各种可选参数。在这个例子中，我们设置votes字段的[默认值](http://python.usyiyi.cn/documents/django_182/ref/models/fields.html#django.db.models.Field.default)为0。

最后，注意我们使用[ForeignKey](http://python.usyiyi.cn/documents/django_182/ref/models/fields.html#django.db.models.ForeignKey)定义了一个关联。它告诉Django每个Choice都只关联一个Question。Django支持所有常见的数据库关联：多对一、多对多和一对一。

