下面这些输入方法的作用都是向子程序发送响应命令，可以理解成代替了我们的标准输入键盘。

```
send(self,s) 发送命令，不回车
sendline(self,s='')发送命令，回车
sendcontrol(self,char) 发送控制字符，如child.sendcontrol('c') 等价于"Ctrl+c"

sendeof() 发送eof
```



