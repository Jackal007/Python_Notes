# 标记

标签在渲染的过程中提供任意的逻辑。

这个定义是刻意模糊的。例如，一个标签可以输出内容，作为控制结构，例如“if”语句或“for”循环从数据库中提取内容，甚至可以访问其他的模板标签。

Tags是由`%}`和`{%`来定义的，例如：

```text
{% csrf_token %}
```

