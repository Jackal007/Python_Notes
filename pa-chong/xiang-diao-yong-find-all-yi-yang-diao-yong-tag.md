`find_all()`几乎是Beautiful Soup中最常用的搜索方法,所以我们定义了它的简写方法.`BeautifulSoup`对象和`tag`对象可以被当作一个方法来使用,这个方法的执行结果与调用这个对象的`find_all()`方法相同,下面两行代码是等价的:

```
soup.find_all("a")
soup("a")"
)
```

这两行代码也是等价的:

```
soup.title.find_all(string=True)
soup.title(string=True)
```



