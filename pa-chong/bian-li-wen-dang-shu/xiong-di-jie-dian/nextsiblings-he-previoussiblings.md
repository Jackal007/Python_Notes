通过`.next_siblings`和`.previous_siblings`属性可以对当前节点的兄弟节点迭代输出:

```
for sibling in soup.a.next_siblings:
    print(repr(sibling))
    # u',\n'
    # <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>
    # u' and\n'
    # <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>
    # u'; and they lived at the bottom of a well.'
    # None

for sibling in soup.find(id="link3").previous_siblings:
    print(repr(sibling))
    # ' and\n'
    # <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>
    # u',\n'
    # <a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>
    # u'Once upon a time there were three little sisters; and their names were\n'
    # None
```



