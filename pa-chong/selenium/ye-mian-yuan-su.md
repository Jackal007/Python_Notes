### `selenium.webdriver.common.action_chains.ActionChains(driver)`

可以进行连续的多个操作：

```py
menu = driver.find_element_by_css_selector(".nav")
hidden_submenu = driver.find_element_by_css_selector(".nav #submenu1")

ActionChains(driver).move_to_element(menu).click(hidden_submenu).perform()
```

也可以以下一下来：

```
menu = driver.find_element_by_css_selector(".nav")
hidden_submenu = driver.find_element_by_css_selector(".nav #submenu1")

actions = ActionChains(driver)
actions.move_to_element(menu)
actions.click(hidden_submenu)
actions.perform()
```

### 操作

| **鼠标操作** |  |
| :--- | :--- |
| click\(on\_element=None\) | 左击on\_element，如果on\_element为空，则点击当前鼠标位置 |
| click\_and\_hold\(on\_element=None\) | 按住不放 |
| context\_click\(on\_element=None\) | 右击 |
| double\_click\(on\_element=None\) | 双击 |
| drag\_and\_drop\_by\_offset\(source, xoffset, yoffset\) | 按住鼠标左键不放，拖动xoffset和yoffset后放掉 |
| release\(on\_element=None\) | 对某一元素放开鼠标 |
| move\_by\_offset\(xoffset, yoffset\) | 根据给定偏移移动鼠标 |
| move\_to\_element\(to\_element\) | 把鼠标移到某个位置 |
| move\_to\_element\_with\_offset\(to\_element, xoffset, yoffset\) | 把鼠标移动到指定元素的某个地方 |
| **键盘操作** | `selenium.webdriver.common.keys.Keys` |
| key\_down\(value, element=None\) | 按住（CTRL:Keys.CONTROL、ALT:Keys.ALTER、SHIFT:Keys.SHIFT中的某一个）不放 |
| key\_up\(value, element=None\) | 释放掉之前按着的某一个键 |
| send\_keys\(\*keys\_to\_send\) | 输入要输入的内容 |
| send\_keys\_to\_element\(element, \*keys\_to\_send\) | 对指定元素输入内容 |
| **弹出窗口** | `class selenium.webdriver.common.alert.Alert(driver)` |
| Alert\(driver\).accept\(\) | 接受 |
| Alert\(driver\).dismiss\(\) | 拒绝 |
| authenticate\(username, password\) | 输入用户名和密码 |
| send\_keys\(keysToSend\) | 输入键 |
| text | 获取弹出窗口的文本 |
| **下拉框** | `selenium.webdriver.support.select.Select(webelement)` |
| deselect\_all\(\) | 取消所有选择项（只对多选框有效） |
| deselect\_by\_index\(index\) | 取消指定索引（根据页面代码里面选项的索引，而不是自己数的）项的选择 |
| deselect\_by\_value\(value\) | 根据值取消选择 |
| deselect\_by\_visible\_text\(text\) | 根据文本取消选择 |
| select\_by\_index\(index\) |  |
| select\_by\_value\(value\) |  |
| select\_by\_visible\_text\(text\) |  |
| all\_selected\_options | 返回所有被选中的选项 |
| first\_selected\_option | 返回第一个被选中的选项 |
| options | 返回所有选项 |
| **其他** |  |
| pause\(seconds\) | 暂停数秒 |
| reset\_actions\(\) | Clears actions that are already stored on the remote end. |
| perform\(\) | 开始你的表演：在perform之前的所有操作开始按顺序执行 |



