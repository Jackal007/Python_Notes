# pexpect

[https://www.jianshu.com/p/cfd163200d12](https://www.jianshu.com/p/cfd163200d12)

[http://python.jqlinux.com/pythonchang-yong-di-san-fang-3001-nei-zhi-mo-kuai/pythonzhi-pexpect-xiang-jie.html](http://python.jqlinux.com/pythonchang-yong-di-san-fang-3001-nei-zhi-mo-kuai/pythonzhi-pexpect-xiang-jie.html)

Expect 程序主要用于人机对话的模拟，就是那种系统提问，人来回答 yes/no ，或者账号登录输入用户名和密码等等的情况。因为这种情况特别多而且繁琐，所以很多语言都有各种自己的实现。最初的第一个 Expect 是由 TCL 语言实现的，所以后来的 Expect 都大致参考了最初的用法和流程，整体来说大致的流程包括：

1. 运行程序
2. 程序要求人的判断和输入
3. Expect 通过关键字匹配
4. 根据关键字向程序发送符合的字符串

TCL 语言实现的 Expect 功能非常强大，我曾经用它实现了防火墙设备的完整测试平台。也因为它使用方便、范围广，几乎所有脚本语言都实现了各种各样的类似与Expect的功能，它们叫法虽然不同，但原理都相差不大

pexpect 是 Python 语言的类 Expect 实现。从我的角度来看，它在功能上与 TCL 语言的实现还是有一些差距，比如没有buffer\_full 事件、比如没有 expect before/after 事件等，但用来做一般的应用还是足够了。

## 基本使用流程

pexpect 的使用说来说去，就是围绕3个关键命令做操作：

1. 首先用 spawn 来执行一个程序
2. 然后用 expect 来等待指定的关键字，这个关键字是被执行的程序打印到标准输出上面的
3. 最后当发现这个关键字以后，根据关键字用 send 方法来发送字符串给这个程序

第一步只需要做一次，但在程序中会不停的循环第二、三步来一步一步的完成整个工作。掌握这个概念之后 pexpect 的使用就很容易了。当然 pexpect 不会只有这 3 个方法，实际上还有很多外围的其他方法，我们一个一个来说明

### 小例子

```python
import pexpect
child = pexpect.spawn('ftp xxx.xxx.xxx.xxx') #spawn 启动ftp程序
child.expect('Password:') #expect方法等待子程序产生的输出，判断是否匹配定义的字符串 'Password:'
child.sendline(mypassword) #匹配后则发送密码串进行回应
```

