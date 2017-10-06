通过`.parent`属性来获取某个元素的父节点.在例子“爱丽丝”的文档中,&lt;head&gt;标签是&lt;title&gt;标签的父节点:

```
title_tag = soup.title
title_tag
# <title>The Dormouse's story</title>
title_tag.parent
# <head><title>The Dormouse's story</title></head>
```

文档title的字符串也有父节点:&lt;title&gt;标签

```
title_tag.string.parent
# <title>The Dormouse's story</title>
```

文档的顶层节点比如&lt;html&gt;的父节点是`BeautifulSoup`对象:

```
html_tag = soup.html
type(html_tag.parent)
# <class 'bs4.BeautifulSoup'>
```

`BeautifulSoup`对象的`.parent`是None:

```
print(soup.parent)
# None
```



