## 可以遍历的字符串

字符串常被包含在tag内.Beautiful Soup用`NavigableString`类来包装tag中的字符串:

```
tag.string
# u'Extremely bold'
type(tag.string)
# <class 'bs4.element.NavigableString'>
```

一个`NavigableString`字符串与Python中的Unicode字符串相同,并且还支持包含在[遍历文档树](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id18)和[搜索文档树](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id27)中的一些特性. 通过`unicode()`方法可以直接将`NavigableString`对象转换成Unicode字符串:

```
unicode_string = unicode(tag.string)
unicode_string
# u'Extremely bold'
type(unicode_string)
# <type 'unicode'>
```

tag中包含的字符串不能编辑,但是可以被替换成其它的字符串,用[replace\_with\(\)](http://beautifulsoup.readthedocs.io/zh_CN/latest/#replace-with)方法:

```
tag.string.replace_with("No longer bold")
tag
# <blockquote>No longer bold</blockquote>
```

`NavigableString`对象支持[遍历文档树](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id18)和[搜索文档树](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id27)中定义的大部分属性, 并非全部.尤其是,一个字符串不能包含其它内容\(tag能够包含字符串或是其它tag\),字符串不支持`.contents`或`.string`属性或`find()`方法.

如果想在Beautiful Soup之外使用`NavigableString`对象,需要调用`unicode()`方法,将该对象转换成普通的Unicode字符串,否则就算Beautiful Soup已方法已经执行结束,该对象的输出也会带有对象的引用地址.这样会浪费内存.

