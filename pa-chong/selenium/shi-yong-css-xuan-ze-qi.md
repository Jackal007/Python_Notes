会返回第一个符合css选择式的元素，如果没有符合条件的，会抛出`NoSuchElementException`

比如：

```html
<html>
 <body>
  <p class="content">Site content goes here.</p>
</body>
<html>
```

要找`p ` 元素，可以这么来：

```py
content = driver.find_element_by_css_selector('p.content')
```

---

### 直接孩子

```html
<div>
    <a>xx</a>
</div>

css=div > a
```

### 内部节点

```html
<div>
    <div>
        <a>xx</a>
    </div>
</div>

css=div a
```

### ID

```html
<div>
    <div>
        <a>xx</a>
    </div>
</div>

css=div a
```



