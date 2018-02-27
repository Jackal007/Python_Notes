from：[http://www.nmap.com.cn/doc/manual.shtm](http://www.nmap.com.cn/doc/manual.shtm)

# nmap软件使用手册

如果是为了测试，scanme.nmap.org 允许被扫描。但仅允许使用Nmap扫描并禁止测试漏洞或进行DoS攻击。为保证带宽，对该主机的扫描每天不要超过12次。如果这个免费扫描服务滥用，系统将崩溃而且Nmap将报告解析 指定的主机名/IP地址失败：scanme.nmap.org。这些免费扫描要求也适用于scanme2.nmap.org、 scanme3.nmap.org等等，虽然这些主机目前还不存在。

### 选项概要

Usage: nmap \[Scan Type\(s\)\] \[Options\] {target specification}  
TARGET SPECIFICATION:  
Can pass hostnames, IP addresses, networks, etc.  
Ex: scanme.nmap.org, microsoft.com/24, 192.168.0.1; 10.0-255.0-255.1-254  
-iL &lt;inputfilename&gt;: Input from list of hosts/networks  
-iR &lt;num hosts&gt;: Choose random targets  
--exclude &lt;host1\[,host2\]\[,host3\],...&gt;: Exclude hosts/networks  
--excludefile &lt;exclude\_file&gt;: Exclude list from file  
HOST DISCOVERY:  
-sL: List Scan - simply list targets to scan  
-sP: Ping Scan - go no further than determining if host is online  
-P0: Treat all hosts as online -- skip host discovery  
-PS/PA/PU \[portlist\]: TCP SYN/ACK or UDP discovery probes to given ports  
-PE/PP/PM: ICMP echo, timestamp, and netmask request discovery probes  
-n/-R: Never do DNS resolution/Always resolve \[default: sometimes resolve\]  
SCAN TECHNIQUES:  
-sS/sT/sA/sW/sM: TCP SYN/Connect\(\)/ACK/Window/Maimon scans  
-sN/sF/sX: TCP Null, FIN, and Xmas scans  
--scanflags &lt;flags&gt;: Customize TCP scan flags  
-sI &lt;zombie host\[:probeport\]&gt;: Idlescan  
-sO: IP protocol scan  
-b &lt;ftp relay host&gt;: FTP bounce scan  
PORT SPECIFICATION AND SCAN ORDER:  
-p &lt;port ranges&gt;: Only scan specified ports  
Ex: -p22; -p1-65535; -p U:53,111,137,T:21-25,80,139,8080  
-F: Fast - Scan only the ports listed in the nmap-services file\)  
-r: Scan ports consecutively - don't randomize  
SERVICE/VERSION DETECTION:  
-sV: Probe open ports to determine service/version info  
--version-light: Limit to most likely probes for faster identification  
--version-all: Try every single probe for version detection  
--version-trace: Show detailed version scan activity \(for debugging\)  
OS DETECTION:  
-O: Enable OS detection  
--osscan-limit: Limit OS detection to promising targets  
--osscan-guess: Guess OS more aggressively  
TIMING AND PERFORMANCE:  
-T\[0-6\]: Set timing template \(higher is faster\)  
--min-hostgroup/max-hostgroup &lt;msec&gt;: Parallel host scan group sizes  
--min-parallelism/max-parallelism &lt;msec&gt;: Probe parallelization  
--min-rtt-timeout/max-rtt-timeout/initial-rtt-timeout &lt;msec&gt;: Specifies  
probe round trip time.  
--host-timeout &lt;msec&gt;: Give up on target after this long  
--scan-delay/--max-scan-delay &lt;msec&gt;: Adjust delay between probes  
FIREWALL/IDS EVASION AND SPOOFING:  
-f; --mtu &lt;val&gt;: fragment packets \(optionally w/given MTU\)  
-D &lt;decoy1,decoy2\[,ME\],...&gt;: Cloak a scan with decoys  
-S &lt;IP\_Address&gt;: Spoof source address  
-e &lt;iface&gt;: Use specified interface  
-g/--source-port &lt;portnum&gt;: Use given port number  
--data-length &lt;num&gt;: Append random data to sent packets  
--ttl &lt;val&gt;: Set IP time-to-live field  
--spoof-mac &lt;mac address, prefix, or vendor name&gt;: Spoof your MAC address  
OUTPUT:  
-oN/-oX/-oS/-oG &lt;file&gt;: Output scan results in normal, XML, s\|&lt;rIpt kIddi3,  
and Grepable format, respectively, to the given filename.  
-oA &lt;basename&gt;: Output in the three major formats at once  
-v: Increase verbosity level \(use twice for more effect\)  
-d\[level\]: Set or increase debugging level \(Up to 9 is meaningful\)  
--packet-trace: Show all packets sent and received  
--iflist: Print host interfaces and routes \(for debugging\)  
--append-output: Append to rather than clobber specified output files  
--resume &lt;filename&gt;: Resume an aborted scan  
--stylesheet &lt;path/URL&gt;: XSL stylesheet to transform XML output to HTML  
--no-stylesheet: Prevent Nmap from associating XSL stylesheet w/XML output  
MISC:  
-6: Enable IPv6 scanning  
-A: Enables OS detection and Version detection  
--datadir &lt;dirname&gt;: Specify custom Nmap data file location  
--send-eth/--send-ip: Send packets using raw ethernet frames or IP packets  
--privileged: Assume that the user is fully privileged  
-V: Print version number  
-h: Print this help summary page.  
EXAMPLES:  
nmap -v -A scanme.nmap.org  
nmap -v -sP 192.168.0.0/16 10.0.0.0/8  
nmap -v -iR 10000 -P0 -p 80

## 实例

下面给出一些实例，简单的、复杂的到深奥的。为更具体，一 些例子使用了实际的IP地址和域名。在这些位置，可以使用_你自己网络_的地址/域名替换。注意，扫描其它网络不一定合法，一些网络管理员不愿看到 未申请过的扫描，会产生报怨。因此，先获得允许是最好的办法。

**nmap -v scanme.nmap.org**

这个选项扫描主机scanme.nmap.org中 所有的保留TCP端口。选项-v启用细节模式。

**nmap -sS -O scanme.nmap.org/24**

进行秘密SYN扫描，对象为主机Saznme所在的“C类”网段 的255台主机。同时尝试确定每台工作主机的操作系统类型。因为进行SYN扫描 和操作系统检测，这个扫描需要有根权限。

**nmap -sV -p 22，53，110，143，4564 198.116.0-255.1-127**

进行主机列举和TCP扫描，对象为B类188.116网段中255个8位子网。这 个测试用于确定系统是否运行了sshd、DNS、imapd或4564端口。如果这些端口 打开，将使用版本检测来确定哪种应用在运行。

**nmap -v -iR 100000 -P0 -p 80**

随机选择100000台主机扫描是否运行Web服务器\(80端口\)。由起始阶段 发送探测报文来确定主机是否工作非常浪费时间，而且只需探测主机的一个端口，因 此使用-P0禁止对主机列表。

**nmap -P0 -p80 -oX logs/pb-port80scan.xml -oG logs/pb-port80scan.gnmap 216.163.128.20/20**

扫描4096个IP地址，查找Web服务器\(不ping\)，将结果以Grep和XML格式保存。

**host -l company.com \| cut -d -f 4 \| nmap -v -iL -**

进行DNS区域传输，以发现company.com中的主机，然后将IP地址提供给 Nmap。上述命令用于GNU/Linux -- 其它系统进行区域传输时有不同的命令。

