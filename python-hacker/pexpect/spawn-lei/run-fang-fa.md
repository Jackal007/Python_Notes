# run方法

run是使用pexpect进行封装的调用外部命令的函数，类似os.system或os.popen方法，不同的是，使用run\(\)可以同时获得命令的输出结果及命令的退出状态。

```python
  run(command, timeout=-1, withexitstatus=False, events=None, extra_args=None, logfile=None, cwd=None, env=None)
#默认情况下该指令：
#1.运行给出的指令command，如果指令不是以绝对路径给出，会自动在PATH中寻找。结果输出作为字符串返回，行与行之间以\r\n分割。
#2.withexitstatus设置为True时，结果返回一个元组，(command_output,
    exitstatus)
#events是一个字典，有模式和应答组成，可以自动输入内容，如果应答需要输入enter键时，此时需要为一个新行，即添加\n.
>>> pexpect.run('cat /root/a.txt')
'qian shan\r\nniao fei jue\r\ndu diao han jiang xue\r\n'
>>> pexpect.run('cat /root/a.txt',withexitstatus=1)
('qian shan\r\nniao fei jue\r\ndu diao han jiang xue\r\n', 0)
>>> pexpect.run('scp /root/a.txt 192.168.56.102:/root',withexitstatus=1,events={'password': '123456\n'})
("root@192.168.56.102's password: \r\n\ra.txt
```

