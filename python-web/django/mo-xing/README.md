# 模型

模型是你的数据的唯一的、权威的信息源。它包含你所储存数据的必要字段和行为。通常，每个模型对应数据库中唯一的一张表。

* 每个模型都是[django.db.models.Model](http://python.usyiyi.cn/documents/django_182/ref/models/instances.html#django.db.models.Model)的一个Python 子类。
* 模型的每个属性都表示为数据库中的一个字段。
* Django 提供一套自动生成的用于数据库访问的API；详见[_执行查询_](http://python.usyiyi.cn/documents/django_182/topics/db/queries.html)。

> ### 简短的例子
>
> 这个例子定义一个Person模型，它有first\_name和last\_name两个属性：
>
> ```text
> from django.db import models
>
> class Person(models.Model):
>     first_name = models.CharField(max_length=30)
>     last_name = models.CharField(max_length=30)
> ```
>
> first\_name和last\_name是模型的两个[字段](http://python.usyiyi.cn/documents/django_182/topics/db/models.html#fields)。每个字段都被指定成一个类属性，每个属性映射到一个数据库的列。
>
> 上面的Person模型会在数据库中创建这样一张表：
>
> ```text
> CREATE TABLE myapp_person (
>     "id" serial NOT NULL PRIMARY KEY,
>     "first_name" varchar(30) NOT NULL,
>     "last_name" varchar(30) NOT NULL
> );
> ```
>
> 一些技术上的注意事项：
>
> * 这个表的名称myapp\_person，是根据 模型中的元数据自动生成的，也可以重写为别的名称，详见[_Table names_](http://python.usyiyi.cn/documents/django_182/ref/models/options.html#table-names)。
> * id 字段是自动添加的，但这个行为可以被重写。详见[_自增主键字段_](http://python.usyiyi.cn/documents/django_182/topics/db/models.html#automatic-primary-key-fields)。
> * 这个例子中的CREATE TABLE SQL 语句使用PostgreSQL 语法格式，要注意的是Django 会根据[_设置文件_](http://python.usyiyi.cn/documents/django_182/topics/settings.html)中指定的数据库类型来使用相应的SQL 语句。

## 使用模型

定义好模型之后，接下来你需要告诉Django_使用_这些模型。你要做的就是修改配置文件中的[INSTALLED\_APPS](http://python.usyiyi.cn/documents/django_182/ref/settings.html#std:setting-INSTALLED_APPS) 设置，在其中添加models.py所在应用的名称。

例如，如果你的应用的模型位于myapp.models（由[manage.pystartapp](http://python.usyiyi.cn/documents/django_182/ref/django-admin.html#django-admin-startapp)命令自动创建的结构），[INSTALLED\_APPS](http://python.usyiyi.cn/documents/django_182/ref/settings.html#std:setting-INSTALLED_APPS)部分看上去应该是：

```text
INSTALLED_APPS=(
    #...
    'myapp',
    #...
)
```

当你在[INSTALLED\_APPS](http://python.usyiyi.cn/documents/django_182/ref/settings.html#std:setting-INSTALLED_APPS)中添加新的应用名时，请确保运行命令[manage.py migrate](http://python.usyiyi.cn/documents/django_182/ref/django-admin.html#django-admin-migrate)，可以事先使用[manage.py makemigrations](http://python.usyiyi.cn/documents/django_182/ref/django-admin.html#django-admin-makemigrations)给应用生成迁移脚本。

