如果tag只有一个`NavigableString`类型子节点,那么这个tag可以使用`.string`得到子节点:

```
title_tag.string
# u'The Dormouse's story'
```

如果一个tag仅有一个子节点,那么这个tag也可以使用`.string`方法,输出结果与当前唯一子节点的`.string`结果相同:

```
head_tag.contents
# [<title>The Dormouse's story</title>]

head_tag.string
# u'The Dormouse's story'
```

如果tag包含了多个子节点,tag就无法确定`.string`方法应该调用哪个子节点的内容,`.string`的输出结果是`None`:

```
print(soup.html.string)
# None
```



