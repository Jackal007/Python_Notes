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
| **键盘操作** |  |
| key\_down\(value, element=None\) | 按住（CTRL:Keys.CONTROL、ALT:Keys.ALTER、SHIFT:Keys.SHIFT中的某一个）不放 |
| key\_up\(value, element=None\) | 释放掉之前按着的某一个键 |
| send\_keys\(\*keys\_to\_send\) | 输入要输入的内容 |
| send\_keys\_to\_element\(element, \*keys\_to\_send\) | 对指定元素输入内容 |
| **其他** |  |
| pause\(seconds\) | 暂停数秒 |
| reset\_actions\(\) | Clears actions that are already stored on the remote end. |
| perform\(\) | 开始你的表演：在perform之前的所有操作开始按顺序执行 |



