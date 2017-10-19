直接调用windows的各种组件，这样做其实就和按键精灵差不多

http://timgolden.me.uk/pywin32-docs/contents.html

python操作QQ

```py
# 原理是先将需要发送的文本放到剪贴板中，然后将剪贴板内容发送到qq窗口
# 之后模拟按键发送enter键发送消息

import win32gui
import win32con
import win32clipboard as w

def getText():
    """获取剪贴板文本"""
    w.OpenClipboard()
    d = w.GetClipboardData(win32con.CF_UNICODETEXT)
    w.CloseClipboard()
    return d

def setText(aString):
    """设置剪贴板文本"""
    w.OpenClipboard()
    w.EmptyClipboard()
    w.SetClipboardData(win32con.CF_UNICODETEXT, aString)
    w.CloseClipboard()

def send_qq(to_who, msg):
    """发送qq消息
    to_who：qq消息接收人
    msg：需要发送的消息
    """
    # 将消息写到剪贴板
    setText(msg)
    # 获取qq窗口句柄
    qq = win32gui.FindWindow(None, to_who)
    # 投递剪贴板消息到QQ窗体
    win32gui.SendMessage(qq, 258, 22, 2080193)
    win32gui.SendMessage(qq, 770, 0, 0)
    # 模拟按下回车键
    win32gui.SendMessage(qq, win32con.WM_KEYDOWN, win32con.VK_RETURN, 0)
    win32gui.SendMessage(qq, win32con.WM_KEYUP, win32con.VK_RETURN, 0)


# 测试
to_who='xxx'
msg='这是测试消息'
send_qq(to_who, msg)
```

# 参考： {#参考}

[http://blog.csdn.net/dahuae/article/details/43969175](http://blog.csdn.net/dahuae/article/details/43969175)  
[http://blog.csdn.net/seele52/article/details/17504925](http://blog.csdn.net/seele52/article/details/17504925)  
[http://lixxu.iteye.com/blog/417218](http://lixxu.iteye.com/blog/417218)  
[http://www.codeweblog.com/%E7%94%A8pywin32%E5%AE%9E%E7%8E%B0windows%E6%A8%A1%E6%8B%9F%E9%BC%A0%E6%A0%87%E5%8F%8A%E9%94%AE%E7%9B%98%E5%8A%A8%E4%BD%9C/](http://www.codeweblog.com/%E7%94%A8pywin32%E5%AE%9E%E7%8E%B0windows%E6%A8%A1%E6%8B%9F%E9%BC%A0%E6%A0%87%E5%8F%8A%E9%94%AE%E7%9B%98%E5%8A%A8%E4%BD%9C/)













  


