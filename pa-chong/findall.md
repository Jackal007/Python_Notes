find\_all\([name](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id35),[attrs](http://beautifulsoup.readthedocs.io/zh_CN/latest/#css),[recursive](http://beautifulsoup.readthedocs.io/zh_CN/latest/#recursive),[string](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id36),[\*\*kwargs](http://beautifulsoup.readthedocs.io/zh_CN/latest/#keyword)\)

`find_all()`方法搜索当前tag的所有tag子节点,并判断是否符合过滤器的条件.这里有几个例子:

```
soup.find_all("title")
# [<title>The Dormouse's story</title>]

soup.find_all("p", "title")
# [<p class="title"><b>The Dormouse's story</b></p>]

soup.find_all("a")
# [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
#  <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,
#  <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]

soup.find_all(id="link2")
# [<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>]

import re
soup.find(string=re.compile("sisters"))
# u'Once upon a time there were three little sisters; and their names were\n'
```

有几个方法很相似,还有几个方法是新的,参数中的`string`和`id`是什么含义? 为什么`find_all("p","title")`返回的是CSS Class为”title”的&lt;p&gt;标签? 我们来仔细看一下`find_all()`的参数

