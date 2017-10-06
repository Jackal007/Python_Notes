通过元素的`.parents`属性可以递归得到元素的所有父辈节点,下面的例子使用了`.parents`方法遍历了&lt;a&gt;标签到根节点的所有节点.

```
link = soup.a
link
# <a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>
for parent in link.parents:
    if parent is None:
        print(parent)
    else:
        print(parent.name)
# p
# body
# html
# [document]
# None
```



