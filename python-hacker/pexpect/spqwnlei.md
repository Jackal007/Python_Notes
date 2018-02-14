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



