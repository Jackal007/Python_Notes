tag的`.contents`属性可以将tag的子节点以列表的方式输出:

```
head_tag = soup.head
head_tag
# <head><title>The Dormouse's story</title></head>

head_tag.contents
[<title>The Dormouse's story</title>]

title_tag = head_tag.contents[0]
title_tag
# <title>The Dormouse's story</title>
title_tag.contents
# [u'The Dormouse's story']
```

`BeautifulSoup`对象本身一定会包含子节点,也就是说&lt;html&gt;标签也是`BeautifulSoup`对象的子节点:

```
len(soup.contents)
# 1
soup.contents[0].name
# u'html'
```

字符串没有`.contents`属性,因为字符串没有子节点:

```
text = title_tag.contents[0]
text.contents
# AttributeError: 'NavigableString' object has no attribute 'contents'
```

通过tag的`.children`生成器,可以对tag的子节点进行循环:

```
for child in title_tag.children:
    print(child)
    # The Dormouse's story
```



