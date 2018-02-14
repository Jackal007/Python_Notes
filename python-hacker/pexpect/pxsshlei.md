pxssh 是pexpect的派生类，针对上ssh会话操作上再做一层封装，提供与基类更加直接的操作方法。  
pxssh 类定义：

```py
  class pexpect.pxssh.pxssh(
      timeout=30,
      maxread=2000,
      searchwindow=None,
      logfile=None,
      cwd=None,
      env=None)
```

* login\(\) 建立ssh连接；
* logout\(\)断开连接；
* prompt\(\)等待系统提示符，用于等待命令执行结束。

### 例子：

实现ssh登录的例子

```py
#!/usr/bin/env python
 #-*- coding:utf-8 -*-

import pxssh
import getpass
try:
    # 调用构造函数，创建一个 pxssh 类的对象.
    s = pxssh.pxssh()
    # 获得用户指定 ssh 主机域名.
    hostname = raw_input('hostname: ')
    # 获得用户指定 ssh 主机用户名.
    username = raw_input('username: ')
    # 获得用户指定 ssh 主机密码.
    password = getpass.getpass('password: ')
    #ssh 端口
    port = raw_input('port:')
    # 利用 pxssh 类的 login 方法进行 ssh 登录，原始 prompt 为'$' , '#'或'>'
    s.login (hostname, username, password, port=port ,original_prompt='[$#>]')

    # 发送命令 'uptime'
    s.sendline ('uptime')
    # 匹配 prompt
    s.prompt()
    # 将 prompt 前所有内容打印出，即命令 'uptime' 的执行结果.
    print s.before
    # 发送命令 ' ls -l '
    s.sendline ('ls -l')
    # 匹配 prompt
    s.prompt()
    # 将 prompt 前所有内容打印出，即命令 ' ls -l ' 的执行结果.
    print s.before
    # 退出 ssh session
    s.logout()
except pxssh.ExceptionPxssh, e:
    print "pxssh failed on login."
    print str(e)
```

实现自动化ftp操作

```py
#!/usr/bin/env python
#-*- coding:utf-8 -*-

from __future__ import unicode_literals #使用Unicode编码
import pexpect
import sys

child = pexpect.spawnu('ftp www.jqlinux.com') #运行ftp命令
child.expect('(?i)name .*:') #(?i)表示后面的字符串正则匹配忽略大小写
child.sendline('root') #输入ftp账号信息
child.expect('(?i)password') #匹配密码输入提示
child.sendline('123456')
child.expect('ftp>')
child.sendline('get python_test/scapy-test.py') #下载文件
child.expect('ftp>')
sys.stdout.write(child.before) #输出匹配“ftp>” 之前的输入与输出
print("Escape character is '^]'.\n")
sys.stdout.write(child.after)
sys.stdout.flush()
#调用interract()让出控制权，用户可以继续当前的回话手工控制程序，默认输入“^]” 字符跳出child.interact()
child.sendline('bye')
child.close()
```



