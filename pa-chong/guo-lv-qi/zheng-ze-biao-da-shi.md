如果传入正则表达式作为参数,Beautiful Soup会通过正则表达式的`match()`来匹配内容.下面例子中找出所有以b开头的标签,这表示&lt;body&gt;和&lt;b&gt;标签都应该被找到:

```
import re
for tag in soup.find_all(re.compile("^b")):
    print(tag.name)
# body
# b
```

下面代码找出所有名字中包含”t”的标签:

```
for tag in soup.find_all(re.compile("t")):
    print(tag.name)
# html
# title
```



