## BeautifulSoup

`BeautifulSoup`对象表示的是一个文档的全部内容.大部分时候,可以把它当作`Tag`对象,它支持[遍历文档树](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id18)和[搜索文档树](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id27)中描述的大部分的方法.

因为`BeautifulSoup`对象并不是真正的HTML或XML的tag,所以它没有name和attribute属性.但有时查看它的`.name`属性是很方便的,所以`BeautifulSoup`对象包含了一个值为 “\[document\]” 的特殊属性`.name`

```
soup.name
# u'[document]'
```



