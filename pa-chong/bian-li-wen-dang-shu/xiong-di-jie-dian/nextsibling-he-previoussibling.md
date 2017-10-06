在文档树中,使用`.next_sibling`和`.previous_sibling`属性来查询兄弟节点:

```
sibling_soup.b.next_sibling
# <c>text2</c>

sibling_soup.c.previous_sibling
# <b>text1</b>
```

&lt;b&gt;标签有`.next_sibling`属性,但是没有`.previous_sibling`属性,因为&lt;b&gt;标签在同级节点中是第一个.同理,&lt;c&gt;标签有`.previous_sibling`属性,却没有`.next_sibling`属性:

```
print(sibling_soup.b.previous_sibling)
# None
print(sibling_soup.c.next_sibling)
# None
```

例子中的字符串“text1”和“text2”不是兄弟节点,因为它们的父节点不同:

```
sibling_soup.b.string
# u'text1'

print(sibling_soup.b.string.next_sibling)
# None
# None
```

实际文档中的tag的`.next_sibling`和`.previous_sibling`属性通常是字符串或空白. 看看“爱丽丝”文档:

```
sibling_soup.b.string
# u'text1'

print(sibling_soup.b.string.next_sibling)
# None
```

如果以为第一个&lt;a&gt;标签的`.next_sibling`结果是第二个&lt;a&gt;标签,那就错了,真实结果是第一个&lt;a&gt;标签和第二个&lt;a&gt;标签之间的顿号和换行符:

```
link = soup.a
link
# <a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>

link.next_sibling
# u',\n'
```

第二个&lt;a&gt;标签是顿号的`.next_sibling`属性:

```
link.next_sibling.next_sibling
# <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>
```



