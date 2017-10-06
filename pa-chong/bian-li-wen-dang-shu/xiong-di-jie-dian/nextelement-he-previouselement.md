`.next_element`属性指向解析过程中下一个被解析的对象\(字符串或tag\),结果可能与`.next_sibling`相同,但通常是不一样的.

这是“爱丽丝”文档中最后一个&lt;a&gt;标签,它的`.next_sibling`结果是一个字符串,因为当前的解析过程[\[2\]](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id89)因为当前的解析过程因为遇到了&lt;a&gt;标签而中断了:

```
last_a_tag = soup.find("a", id="link3")
last_a_tag
# <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>

last_a_tag.next_sibling
# '; and they lived at the bottom of a well.'
```

但这个&lt;a&gt;标签的`.next_element`属性结果是在&lt;a&gt;标签被解析之后的解析内容,不是&lt;a&gt;标签后的句子部分,应该是字符串”Tillie”:

```
last_a_tag.next_element
# u'Tillie'
```

这是因为在原始文档中,字符串“Tillie” 在分号前出现,解析器先进入&lt;a&gt;标签,然后是字符串“Tillie”,然后关闭&lt;/a&gt;标签,然后是分号和剩余部分.分号与&lt;a&gt;标签在同一层级,但是字符串“Tillie”会被先解析.

`.previous_element`属性刚好与`.next_element`相反,它指向当前被解析的对象的前一个解析对象:

```
last_a_tag.previous_element
# u' and\n'
last_a_tag.previous_element.next_element
# <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>
```



