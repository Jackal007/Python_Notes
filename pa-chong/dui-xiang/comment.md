## 注释及特殊字符串

`Tag`,`NavigableString`,`BeautifulSoup`几乎覆盖了html和xml中的所有内容,但是还有一些特殊对象.容易让人担心的内容是文档的注释部分:

```
markup = "<b><!--Hey, buddy. Want to buy a used parser?--></b>"
soup = BeautifulSoup(markup)
comment = soup.b.string
type(comment)
# <class 'bs4.element.Comment'>
```

`Comment`对象是一个特殊类型的`NavigableString`对象:

```
comment
# u'Hey, buddy. Want to buy a used parser'
```

但是当它出现在HTML文档中时,`Comment`对象会使用特殊的格式输出:

```
print(soup.b.prettify())
# <b>
#  <!--Hey, buddy. Want to buy a used parser?-->
# </b>
```

Beautiful Soup中定义的其它类型都可能会出现在XML的文档中:`CData`,`ProcessingInstruction`,`Declaration`,`Doctype`.与`Comment`对象类似,这些类都是`NavigableString`的子类,只是添加了一些额外的方法的字符串独享.下面是用CDATA来替代注释的例子:

```
from bs4 import CData
cdata = CData("A CDATA block")
comment.replace_with(cdata)

print(soup.b.prettify())
# <b>
#  <![CDATA[A CDATA block]]>
# </b>
```



