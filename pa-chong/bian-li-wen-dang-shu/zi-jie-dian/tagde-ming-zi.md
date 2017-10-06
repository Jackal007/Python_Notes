### tag的名字

操作文档树最简单的方法就是告诉它你想获取的tag的name.如果想获取 &lt;head&gt; 标签,只要用`soup.head`:

```
soup.head
# <head><title>The Dormouse's story</title></head>

soup.title
# <title>The Dormouse's story</title>
```

这是个获取tag的小窍门,可以在文档树的tag中多次调用这个方法.下面的代码可以获取&lt;body&gt;标签中的第一个&lt;b&gt;标签:

```
soup.body.b
# <b>The Dormouse's story</b>
```

通过点取属性的方式只能获得当前名字的第一个tag:

```
soup.a
# <a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>
```

如果想要得到所有的&lt;a&gt;标签,或是通过名字得到比一个tag更多的内容的时候,就需要用到Searching the tree中描述的方法,比如: find\_all\(\)

```
soup.find_all('a')
# [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
#  <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,
#  <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]
```



