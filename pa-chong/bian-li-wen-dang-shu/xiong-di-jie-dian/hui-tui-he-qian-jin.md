看一下“爱丽丝” 文档:

```
<html><head><title>The Dormouse's story</title></head>
<p class="title"><b>The Dormouse's story</b></p>
```

HTML解析器把这段字符串转换成一连串的事件: “打开&lt;html&gt;标签”,”打开一个&lt;head&gt;标签”,”打开一个&lt;title&gt;标签”,”添加一段字符串”,”关闭&lt;title&gt;标签”,”打开&lt;p&gt;标签”,等等.Beautiful Soup提供了重现解析器初始化过程的方法.

