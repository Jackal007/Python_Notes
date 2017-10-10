调用tag的`find_all()`方法时,Beautiful Soup会检索当前tag的所有子孙节点,如果只想搜索tag的直接子节点,可以使用参数`recursive=False`.

一段简单的文档:

```
<html>
 <head>
  <title>
   The Dormouse's story
  </title>
 </head>
...
```

是否使用`recursive`参数的搜索结果:

```
soup.html.find_all("title")
# [<title>The Dormouse's story</title>]

soup.html.find_all("title", recursive=False)
# []
```

这是文档片段

```
<html>
        <head>
        <title>
        The Dormouse's story
    </title>
        </head>
        ...
```

&lt;title&gt;标签在 &lt;html&gt; 标签下, 但并不是直接子节点, &lt;head&gt; 标签才是直接子节点. 在允许查询所有后代节点时 Beautiful Soup 能够查找到 &lt;title&gt; 标签. 但是使用了`recursive=False`参数之后,只能查找直接子节点,这样就查不到 &lt;title&gt; 标签了.

Beautiful Soup 提供了多种DOM树搜索方法. 这些方法都使用了类似的参数定义. 比如这些方法:`find_all()`:`name`,`attrs`,`text`,`limit`. 但是只有`find_all()`和`find()`支持`recursive`参数.

