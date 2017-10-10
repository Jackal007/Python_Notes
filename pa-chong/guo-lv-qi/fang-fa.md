如果没有合适过滤器,那么还可以定义一个方法,方法只接受一个元素参数[\[4\]](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id91),如果这个方法返回`True`表示当前元素匹配并且被找到,如果不是则反回`False`

下面方法校验了当前元素,如果包含`class`属性却不包含`id`属性,那么将返回`True`:

```
def has_class_but_no_id(tag):
    return tag.has_attr('class') and not tag.has_attr('id')
```

将这个方法作为参数传入`find_all()`方法,将得到所有&lt;p&gt;标签:

```
soup.find_all(has_class_but_no_id)
# [<p class="title"><b>The Dormouse's story</b></p>,
#  <p class="story">Once upon a time there were...</p>,
#  <p class="story">...</p>]
```

返回结果中只有&lt;p&gt;标签没有&lt;a&gt;标签,因为&lt;a&gt;标签还定义了”id”,没有返回&lt;html&gt;和&lt;head&gt;,因为&lt;html&gt;和&lt;head&gt;中没有定义”class”属性.

通过一个方法来过滤一类标签属性的时候, 这个方法的参数是要被过滤的属性的值, 而不是这个标签. 下面的例子是找出`href`属性不符合指定正则的`a`标签.

```
def not_lacie(href):
        return href and not re.compile("lacie").search(href)
soup.find_all(href=not_lacie)
# [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
#  <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]
```

标签过滤方法可以使用复杂方法. 下面的例子可以过滤出前后都有文字的标签.

```
from bs4 import NavigableString
def surrounded_by_strings(tag):
    return (isinstance(tag.next_element, NavigableString)
            and isinstance(tag.previous_element, NavigableString))

for tag in soup.find_all(surrounded_by_strings):
    print tag.name
# p
# a
# a
# a
# p
```

现在来了解一下搜索方法的细节

