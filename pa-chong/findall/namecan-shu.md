`name`参数可以查找所有名字为`name`的tag,字符串对象会被自动忽略掉.

简单的用法如下:

```
soup.find_all("title")
# [<title>The Dormouse's story</title>]
```

重申: 搜索`name`参数的值可以使任一类型的[过滤器](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id28),字符窜,正则表达式,列表,方法或是`True`.

