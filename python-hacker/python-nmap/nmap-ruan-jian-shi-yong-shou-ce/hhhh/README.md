# hhhh

## 扫描单个目标

```text
nmap xxx.xxx.xxx.xxx[ipv4]
nmap -6 x.x.x.x[ipv6]
nmap 主机名
```

## 扫描多个目标

```text
 nmap 192.168.1.1 192.168.1.101 192.168.1.105
 nmap 192.168.1.1,101,105
 nmap 192.168.1.1-100
 nmap 192.168.1.1/24 --exclude 192.168.1.101
```

### 扫描整个子网

```text
nmap 192.168.1.1/24[CIDR格式的网络地址]
```

### 扫描主机列表

```text
nmap -iL [IP地址列表文件]
```

### 扫描随机目标

```text
 nmap -iR 2[随机的数量]
```

#### 排除指定目标

```text
 nmap 192.168.1.1/24 --exclude 192.168.1.101
  nmap 192.168.1.0/24 --excludefile list.txt
```

