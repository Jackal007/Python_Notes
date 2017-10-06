```
soup = BeautifulSoup('<b class="boldest">Extremely bold</b>')
```

```
tag = soup.b
type(tag)
# <class 'bs4.element.Tag'>
```

tag中最重要的属性: **name**和**attributes**

### Name

每个tag都有自己的名字,通过`.name`来获取:

```
tag.name
# u'b'
```

如果改变了tag的name,那将影响所有通过当前Beautiful Soup对象生成的HTML文档:

```
tag.name="blockquote"
tag
# <blockquote class="boldest">Extremely bold</blockquote>
```

### Attributes

一个tag可能有很多个属性. tag`<bclass="boldest">`有一个 “class” 的属性,值为 “boldest” . tag的属性的操作方法与字典相同:

```
tag['class']
# u'boldest'
```

也可以直接”点”取属性, 比如:`.attrs`:

```
tag.attrs
# {u'class': u'boldest'}
```

tag的属性可以被添加,删除或修改. 再说一次, tag的属性操作方法与字典一样

```
tag['class'] = 'verybold'
tag['id'] = 1
tag
# <blockquote class="verybold" id="1">Extremely bold</blockquote>

del tag['class']
del tag['id']
tag
# <blockquote>Extremely bold</blockquote>

tag['class']
# KeyError: 'class'
print(tag.get('class'))
# None
```

#### 多值属性

HTML 4定义了一系列可以包含多个值的属性.在HTML5中移除了一些,却增加更多.最常见的多值的属性是 class \(一个tag可以有多个CSS的class\). 还有一些属性`rel`,`rev`,`accept-charset`,`headers`,`accesskey`. 在Beautiful Soup中多值属性的返回类型是list:

```
css_soup = BeautifulSoup('<p class="body strikeout"></p>')
css_soup.p['class']
# ["body", "strikeout"]

css_soup = BeautifulSoup('<p class="body"></p>')
css_soup.p['class']
# ["body"]
```

如果某个属性看起来好像有多个值,但在任何版本的HTML定义中都没有被定义为多值属性,那么Beautiful Soup会将这个属性作为字符串返回

```
id_soup = BeautifulSoup('<p id="my id"></p>')
id_soup.p['id']
# 'my id'
```

将tag转换成字符串时,多值属性会合并为一个值

```
rel_soup = BeautifulSoup('<p>Back to the <a rel="index">homepage</a></p>')
rel_soup.a['rel']
# ['index']
rel_soup.a['rel'] = ['index', 'contents']
print(rel_soup.p)
# <p>Back to the <a rel="index contents">homepage</a></p>
```

如果转换的文档是XML格式,那么tag中不包含多值属性

```
xml_soup = BeautifulSoup('<p class="body strikeout"></p>', 'xml')
xml_soup.p['class']
# u'body strikeout'
```



