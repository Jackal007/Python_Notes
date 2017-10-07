它是一个自动化测试工具，就像“按键精灵一样”，但是好像只能作用于网页。而且它可以获取当前测试页面的源代码。所以，我们可以用它来模拟人类操作页面，来获取指定页面的数据。这可比requests包简单多了（但是速度慢了），requests需要研究下页面的代码，研究有哪些提交项什么的。

### 例子：

```py
from selenium import webdriver
from selenium.webdriver.common.keys import Keys

driver = webdriver.Chrome()
driver.get("http://www.python.org")
assert "Python" in driver.title
elem = driver.find_element_by_name("q")
elem.clear()
elem.send_keys("pycon")
elem.send_keys(Keys.RETURN)
assert "No results found." not in driver.page_source
driver.close()
```

找到“q”元素，然后输入pycon和回车

