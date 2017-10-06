`.contents`和`.children`属性仅包含tag的直接子节点.例如,&lt;head&gt;标签只有一个直接子节点&lt;title&gt;

```
head_tag.contents
# [<title>The Dormouse's story</title>]
```

但是&lt;title&gt;标签也包含一个子节点:字符串 “The Dormouse’s story”,这种情况下字符串 “The Dormouse’s story”也属于&lt;head&gt;标签的子孙节点.`.descendants`属性可以对所有tag的子孙节点进行递归循环[\[5\]](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id92):

```
for child in head_tag.descendants:
    print(child)
    # <title>The Dormouse's story</title>
    # The Dormouse's story
```

上面的例子中, &lt;head&gt;标签只有一个子节点,但是有2个子孙节点:&lt;head&gt;节点和&lt;head&gt;的子节点,`BeautifulSoup`有一个直接子节点\(&lt;html&gt;节点\),却有很多子孙节点:

```
len(list(soup.children))
# 1
len(list(soup.descendants))
# 25
```



