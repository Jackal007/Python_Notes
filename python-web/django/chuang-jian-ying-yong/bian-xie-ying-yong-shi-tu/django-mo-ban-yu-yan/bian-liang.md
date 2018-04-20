# 变量

变量的值是来自context中的输出, 这类似于字典对象的keys到values的映射关系。

变量是被`}}`和`{{`括起来的部分，例如：

```text
My first name is {{ first_name }}. My last name is {{ last_name }}.
```

有一个上下文`{'名字'：'约翰'，'姓'：“李四”}`，此模板呈现：

```text
My first name is John. My last name is Doe.
```

字典查询，属性查询和列表索引查找都是通过一个点符号来实现：

```text
{{ my_dict.key }}
{{ my_object.attribute }}
{{ my_list.0 }}
```

如果一个变量被解析为一个可调用的，模板系统会调用它不带任何参数，并使用调用它的结果来代替这个可调用对象本身。

