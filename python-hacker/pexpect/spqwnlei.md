## spawn 类 {#spawn-类}

spawn是pexpect的主要类接口，功能是启动和控制子应用程序。

```py
class pexpect.spawn(
    command,args=[],
    timeout=30,
    maxread=2000,# pexpect从终端控制台一次读取的最大字节数
    searchwindowsize=None,# 参数为匹配缓冲区字符串的位置，默认是从开始位置匹配
    logfile=None,
    cwd=None,
    env=None,
    ignore_sighup=True)
```

其中command参数可以是任意已知的系统命令，比如：

```
child = pexpect.spawn('/usr/bin/ftp') 
child = pexpect.spawn('/usr/bin/ssh user@example.com')
child = pexpect.spawn('ls -latr /tmp')
```

当子程序需要参数时，还可以使用python列表来代替参数项：

```
child = pexpect.spawn('/usr/bin/ftp',[]) 
child = pexpect.spawn('/usr/bin/ssh' ,['user@example.com'])
child = pexpect.spawn('ls', ['-latr', '/tmp'])
```

注意的是，pexpect不会解析shell命令中的元字符，包括重定向‘&gt;’、管道‘\|’或者‘\*’，当然我没有可以通过将这三个特殊元字符的命令作为/bin/bash 的参数进行调用，例如

```
child = pexpect.spawn('/bin/bash -c "ls -l|grep LOG 
>
logs.txt"')
child.expect(pexpect.EOF)
```

或者

```
shell_cmd = 'ls -l |grep LOG
>
logs.txt'
child = pexpect.spawn('/bin/bash',['-c',shell_cmd]
child.expect(pexpect.EOF)
```

pexpect提供了2种途径写入log，一种为写到日志文件，另一种是标准输出。

```
写入日志文件：
child = pexpect.spawn('some_command')
fout = file('mylog.txt','w')
child.logfile = fout

输出控制台：
child = pexpect.spawn('some_command')
child.logfile = sys.stdout
```

### 实例：

```py
"""
This runs a command on a remote host using SSH. At the prompts enter hostname,
user, password and the command.
"""

import pexpect
import getpass, os

#user: ssh 主机的用户名
#host：ssh 主机的域名
#password：ssh 主机的密码
#command：即将在远端 ssh 主机上运行的命令
def ssh_command (user, host, password, command):
    """
    This runs a command on the remote host. This could also be done with the
    pxssh class, but this demonstrates what that class does at a simpler level.
    This returns a pexpect.spawn object. This handles the case when you try to
    connect to a new host and ssh asks you if you want to accept the public key
    fingerprint and continue connecting.
    """
    ssh_newkey = 'Are you sure you want to continue connecting'
    # 为 ssh 命令生成一个 spawn 类的子程序对象.
    child = pexpect.spawn('ssh -l %s %s %s'%(user, host, command))
    i = child.expect([pexpect.TIMEOUT, ssh_newkey, 'password: '])
    # 如果登录超时，打印出错信息，并退出.
    if i == 0: # Timeout
        print 'ERROR!'
        print 'SSH could not login. Here is what SSH said:'
        print child.before, child.after
        return None
    # 如果 ssh 没有 public key，接受它.
    if i == 1: # SSH does not have the public key. Just accept it.
        child.sendline ('yes')
        child.expect ('password: ')
        i = child.expect([pexpect.TIMEOUT, 'password: '])
        if i == 0: # Timeout
        print 'ERROR!'
        print 'SSH could not login. Here is what SSH said:'
        print child.before, child.after
        return None
    # 输入密码.
    child.sendline(password)
    return child

def main ():
    # 获得用户指定 ssh 主机域名.
    host = raw_input('Hostname: ')
    # 获得用户指定 ssh 主机用户名.
    user = raw_input('User: ')
    # 获得用户指定 ssh 主机密码.
    password = getpass.getpass()
    # 获得用户指定 ssh 主机上即将运行的命令.
    command = raw_input('Enter the command: ')
    child = ssh_command (user, host, password, command)
    # 匹配 pexpect.EOF
    child.expect(pexpect.EOF)
    # 输出命令结果.
    print child.before

if __name__ == '__main__':
    try:
        main()
    except Exception, e:
        print str(e)
        traceback.print_exc()
        os._exit(1)
```



