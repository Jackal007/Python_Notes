# selenium

它是一个自动化测试工具，就像“按键精灵一样”，而且它可以获取当前测试页面的源代码。所以，我们可以用它来模拟人类操作页面，来获取指定页面的数据。这可比requests包简单多了（但是速度慢了），requests需要研究下页面的代码，研究有哪些提交项什么的。

### 例子：

```python
from selenium import webdriver
from selenium.webdriver.common.keys import Keys

driver = webdriver.Chrome()    #打开浏览器
driver.get("http://www.python.org")    #开始请求
driver.maximize_window()    #窗口最大化
assert "Python" in driver.title
elem = driver.find_element_by_name("q")
elem.clear()
elem.send_keys("pycon")
elem.send_keys(Keys.RETURN)
assert "No results found." not in driver.page_source
driver.set_window_size(240, 320)    #设置浏览器窗口大小
driver.close()    #关闭浏览器
```

找到“q”元素，然后输入pycon和回车

#### 可以写成测试类

```python
import unittest
from selenium import webdriver
from selenium.webdriver.common.keys import Keys

class PythonOrgSearch(unittest.TestCase):

    def setUp(self):
        self.driver = webdriver.Firefox()

    def test_search_in_python_org(self):
        driver = self.driver
        driver.get("http://www.python.org")
        self.assertIn("Python", driver.title)
        elem = driver.find_element_by_name("q")
        elem.send_keys("pycon")
        elem.send_keys(Keys.RETURN)
        assert "No results found." not in driver.page_source


    def tearDown(self):
        self.driver.close()

if __name__ == "__main__":
    unittest.main()
```

## Using Selenium with remote WebDriver

待写

## WebDriver 的一些常用操作 {#webdriver-的一些常用操作}

1. `browser.curren_url`

    : 获取当前加载页面的 URL

2. `browser.close()`

    : 关闭当前窗口, 如果当前窗口是最后一个窗口, 浏览器将关闭

3. `browser.quit()`

    : 关闭所有窗口并停止 ChromeDriver 的执行

4. `browser.add_cookie(cookie_dict)` : 为当前会话添加 cookie  
   `browser.get_cookie(name)` : 得到执行 cookie  
   `browser.get_cookies()` : 得到所有的 cookie

   driver.add\_cookie\({‘name’ : ‘foo’, ‘value’ : ‘bar’}\) driver.add\_cookie\({‘name’ : ‘foo’, ‘value’ : ‘bar’, ‘path’ : ‘/’}\) driver.add\_cookie\({‘name’ : ‘foo’, ‘value’ : ‘bar’, ‘path’ : ‘/’, ‘secure’:True}\)

5. `browser.delete_all_cookies()` : 删除当前会话的所有cookie `browser.delete_cookie(name)` : 删除指定 cookie
6. `browser.back()` : 相当于浏览器的后退历史记录
7. `browser.forward()` : 相当于浏览器的前进历史记录
8. `browser.execute_script(script, *args)`  
   : 同步执行 js 脚本

   `browser.execute_async_script(script, *args)`  
   : 异步执行 js 脚本

9. `browser.get(url)` : 在当前窗口加载 url
10. `browser.refresh()` : 刷新当前页面
11. `browser.current_window_handle` : 当前窗口的 handle， 相当于一个指针一样的东西, 用来指向当前窗口
12. `browser.window_handles` : 当前浏览器中的已经打开的所有窗口, 是一个 list
13. `browser.switch_to_window(window_handle)`

     : 切换 window\_handle 指向的窗口

14. `browser.title`

     : 当前页面的 title

15. `browser.name`

     : 当前浏览器的名字

## WebElement 的一些常用操作 {#webelement-的一些常用操作}

1. `webEle.clear()`

    : 清楚元素的内容, 假如这个元素是一个文本元素

2. `webEle.click()`

    : 点击当前元素

3. `webEle,is_displayed()`

    : 当前元素是否可见

4. `webEle.is_enabled()`

    : 当前元素是否禁止, 比如经常会禁用一些元素的点击

5. `webEle.is_selected()`

    : 当前元素是否选中, 文本输入框的内容

6. `webEle.send_keys(*value)`

    : 向当前元素模拟键盘事件

7. `webEle.submit()`

    : 提交表单

8. `webEle.tag_name`

    : 当前元素的标签名

9. `webEle.text`

    : 当前元素的内容

10. `webEle.get_attribute(name)`

     : 获取当前元素执行属性的值

