# subprocess

subprocess模块是python从2.4版本开始引入的模块。主要用来取代 一些旧的模块方法，如os.system、os.spawn\*、os.popen\*、commands.\*等。subprocess通过子进程来执行外部指令，并通过input/output/error管道，获取子进程的执行的返回信息。

常用方法：

* subprocess.call\(\)：执行命令，并返回执行状态，其中shell参数为False时，命令需要通过列表的方式传入，当shell为True时，可直接传入命令

示例如下：

```text
>>> a = subprocess.call(['df','-hT'],shell=False)
Filesystem    Type    Size  Used Avail Use% Mounted on
tmpfs        tmpfs    2.8G     0  2.8G   0% /dev/shm
/dev/sda1     ext4    976M   56M  853M   7% /boot

>>> a = subprocess.call('df -hT',shell=True)
Filesystem    Type    Size  Used Avail Use% Mounted on
tmpfs        tmpfs    2.8G     0  2.8G   0% /dev/shm
/dev/sda1     ext4    976M   56M  853M   7% /boot

>>> print a
0
```

* subprocess.check\_call\(\)：用法与subprocess.call\(\)类似，区别是，当返回值不为0时，直接抛出异常
* subprocess.check\_output\(\)：用法与上面两个方法类似，区别是，如果当返回值为0时，直接返回输出结果，如果返回值不为0，直接抛出异常。需要说明的是，该方法在python3.x中才有。
* subprocess.Popen\(\)：

  在一些复杂场景中，我们需要将一个进程的执行输出作为另一个进程的输入。在另一些场景中，我们需要先进入到某个输入环境，然后再执行一系列的指令等。这个时候我们就需要使用到suprocess的Popen\(\)方法。该方法有以下参数：

  args：shell命令，可以是字符串，或者序列类型，如list,tuple。

  bufsize：缓冲区大小，可不用关心

  stdin,stdout,stderr：分别表示程序的标准输入，标准输出及标准错误

  shell：与上面方法中用法相同

  cwd：用于设置子进程的当前目录

  env：用于指定子进程的环境变量。如果env=None，则默认从父进程继承环境变量

  universal\_newlines：不同系统的的换行符不同，当该参数设定为true时，则表示使用\n作为换行符

* ```text
  #在/root下创建一个suprocesstest的目录：
  >>> a = subprocess.Popen('mkdir subprocesstest',shell=True,cwd='/root')
  ```
* child.poll\(\) \#检查子进程状态
* child.kill\(\) \#终止子进程
* child.send\_signal\(\) \#向子进程发送信号
* child.terminate\(\) \#终止子进程

例子

```text
import subprocess

obj = subprocess.Popen(["python"], stdin=subprocess.PIPE, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
obj.stdin.write('print 1 \n')
obj.stdin.write('print 2 \n')
obj.stdin.write('print 3 \n')
obj.stdin.write('print 4 \n')
obj.stdin.close()

cmd_out = obj.stdout.read()
obj.stdout.close()
cmd_error = obj.stderr.read()
obj.stderr.close()

print cmd_out
print cmd_error


也可以使用如下方法：

import subprocess

obj = subprocess.Popen(["python"], stdin=subprocess.PIPE, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
obj.stdin.write('print 1 \n')
obj.stdin.write('print 2 \n')
obj.stdin.write('print 3 \n')
obj.stdin.write('print 4 \n')

out_error_list = obj.communicate()
print out_error_list

#将一个子进程的输出，作为另一个子进程的输入：

import subprocess
child1 = subprocess.Popen(["cat","/etc/passwd"], stdout=subprocess.PIPE)
child2 = subprocess.Popen(["grep","0:0"],stdin=child1.stdout, stdout=subprocess.PIPE)
out = child2.communicate()
```

