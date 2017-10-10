通过`string`参数可以搜搜文档中的字符串内容.与`name`参数的可选值一样,`string`参数接受[字符串](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id30),[正则表达式](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id31),[列表](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id32),[True](http://beautifulsoup.readthedocs.io/zh_CN/latest/#true). 看例子:

```
soup.find_all(string="Elsie")
# [u'Elsie']

soup.find_all(string=["Tillie", "Elsie", "Lacie"])
# [u'Elsie', u'Lacie', u'Tillie']

soup.find_all(string=re.compile("Dormouse"))
[u"The Dormouse's story", u"The Dormouse's story"]

def is_the_only_string_within_a_tag(s):
    ""Return True if this string is the only child of its parent tag.""
    return (s == s.parent.string)

soup.find_all(string=is_the_only_string_within_a_tag)
# [u"The Dormouse's story", u"The Dormouse's story", u'Elsie', u'Lacie', u'Tillie', u'...']
```

虽然`string`参数用于搜索字符串,还可以与其它参数混合使用来过滤tag.Beautiful Soup会找到`.string`方法与`string`参数值相符的tag.下面代码用来搜索内容里面包含“Elsie”的&lt;a&gt;标签:

```
soup.find_all("a", string="Elsie")
# [<a href="http://example.com/elsie" class="sister" id="link1">Elsie</a>]
```



