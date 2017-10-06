[http://python.jobbole.com/87702/](http://beautifulsoup.readthedocs.io/zh_CN/latest/)

Beautiful Soup提供一些简单的、python式的函数用来处理导航、搜索、修改分析树等功能。它是一个工具箱，通过解析文档为用户提供需要抓取的数据，因为简单，所以不需要多少代码就可以写出一个完整的应用程序。Beautiful Soup自动将输入文档转换为Unicode编码，输出文档转换为utf-8编码。你不需要考虑编码方式，除非文档没有指定一个编码方式，这时，Beautiful Soup就不能自动识别编码方式了。

## 创建BeautifulSoup对象 {#articleHeader3}

首先应该导入BeautifulSoup类库 from bs4 import BeautifulSoup  
下面开始创建对像，在开始之前为了方便演示，先创建一个html文本，如下：

```
html = """
<html><head><title>The Dormouse's story</title></head>
<body>
<p class="title" name="dromouse"><b>The Dormouse's story</b></p>
<p class="story">Once upon a time there were three little sisters; and their names were
<a href="http://example.com/elsie" class="sister" id="link1"><!-- Elsie --></a>,
<a href="http://example.com/lacie" class="sister" id="link2">Lacie</a> and
<a href="http://example.com/tillie" class="sister" id="link3">Tillie</a>;
and they lived at the bottom of a well.</p>
<p class="story">...</p>
"""
```

## Tag {#articleHeader4}

Tag就是html中的一个标签，用BeautifulSoup就能解析出来Tag的具体内容，具体的格式为soup.name,其中name是html下的标签，具体实例如下：

```
print soup.title  # 输出title标签下的内容，包括此标签，这个将会输出<title>The Dormouse's story</title>
print soup.head
```

### string {#articleHeader7}

得到标签下的文本内容，只有在此标签下没有子标签，或者只有一个子标签的情况下才能返回其中的内容，否则返回的是None具体实例如下：

```
print soup.p.string #在上面的一段文本中p标签没有子标签，因此能够正确返回文本的内容

print soup.html.string  #这里得到的就是None,因为这里的html中有很多的子标签
```

### get\_text\(\) {#articleHeader8}

可以获得一个标签中的所有文本内容，包括子孙节点的内容，这是最常用的方法

