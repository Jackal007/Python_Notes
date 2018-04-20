# python-nmap

python-nmap是一个使用nmap进行端口扫描的python库。它可以很轻易的生成nmap扫描报告，并且可以帮助系统管理员进行自动化扫描任务和生成报告。同时，它也支持nmap脚本输出。

需要先安装nmap软件，然后再安装python-nmap包来调用软件

## 安装：

windows：

```text
1.下载 NMAP 安装，并设置好环境变量
2.pip install python-nmap
```

linux

```text
1.sudo apt-get install nmap
2.pip install python-namp
```

## 使用

```python
import nmap # 导入 nmap.py 模块 

nm = nmap.PortScanner() # 实例化nmap.PortScanner对象  
nm.scan('127.0.0.1', '22-443') # 扫描127.0.0.1,端口号从22至443  
nm.command_line() # 获取当前执行扫描的命令行: nmap -oX - -p 22-443 127.0.0.1  
nm.scaninfo() # 获取nmap扫描信息 {'tcp': {'services': '22-443', 'method': 'connect'}}  
nm.all_hosts() # 获取所有已经扫描的主机  
nm['127.0.0.1'].hostname() # 获取一个主机127.0.0.1的主机名，通常为用户记录  
nm['127.0.0.1'].hostnames() # 获取主机127.0.0.1的主机名列表，返回一个字典类型  
# [{'name':'hostname1', 'type':'PTR'}, {'name':'hostname2', 'type':'user'}]
nm['127.0.0.1'].state() # 获取主机127.0.0.1的状态 (up|down|unknown|skipped)  
nm['127.0.0.1'].all_protocols() # 获取执行的协议 ['tcp', 'udp'] 包含 (ip|tcp|udp|sctp)  
nm['127.0.0.1']['tcp'].keys() # 获取tcp协议所有的端口号  
nm['127.0.0.1'].all_tcp() # 获取tcp协议所有的端口号 (按照端口号大小进行排序)  
nm['127.0.0.1'].all_udp() # 获取udp协议所有的端口号 (按照端口号大小进行排序)  
nm['127.0.0.1'].all_sctp() # 获取sctp协议所有的端口号 (按照端口号大小进行排序)  
nm['127.0.0.1'].has_tcp(22) # 主机127.0.0.1是否有关于22端口的任何信息  
nm['127.0.0.1']['tcp'][22] # 获取主机127.0.0.1关于22端口的信息  
nm['127.0.0.1'].tcp(22) # 获取主机127.0.0.1关于22端口的信息  
nm['127.0.0.1']['tcp'][22]['state'] # 获取主机22端口的状态 (open)
```

