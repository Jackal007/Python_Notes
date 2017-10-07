会返回第一个符合css选择式的元素，如果没有符合条件的，会抛出`NoSuchElementException`

比如：

```html
<html>
 <body>
  <p class="content">Site content goes here.</p>
</body>
<html>
```

要找`p`元素，可以这么来：

```py
content = driver.find_element_by_css_selector('p.content')
```

---

### 孩子

```html
直接孩子：
<div>
    <a>xx</a><!--选这个-->
</div>

css=div > a

内部孩子：
<div>
    <div>
        <a>xx</a><!--选这个-->
    </div>
</div>

css=div a
```

### 兄弟节点

```html
<form>
    <input name="username"/>
    <input /><!--选这个-->
</div>

css=form input.username + input
```

### ID && CLASS

```html
ID：
<div id="example">
    <div>
        <a>xx</a><!--选这个-->
    </div>
</div>

css=div#example > a

CLASS：
<div class="example">
    <div>
        <a>xx</a><!--选这个-->
    </div>
</div>

css=div.example > a
```

### 属性

```
css=form input[name='username']
css=input[name='continue'][type='button']
css=a[id^='id_prefix_']    #前缀
css=a[id$='_id_sufix']    #后缀
css=a[id*='id_pattern']    #正则匹配
```

### 内部文本匹配

```
<a>Log Out</a>
css=a:contains('Log Out')
```



