我知道你一定听过wireshark,wireshark真的很好用，可是有个更轻量的Linux命令:tcpdump。它能很容易的抓到包的，最关键的是命令可以直接结合linux的管道，威力无穷。  
比如，最简单的  
sudo tcpdump host[http://jianshu.com](http://link.zhihu.com/?target=http%3A//jianshu.com)  
它会抓取于[http://jianshu.com](http://link.zhihu.com/?target=http%3A//jianshu.com)这个host相通信的所有包，当然，你可再细一点指定过滤条件：

#### 指定协议

sudo tcpdump ip host[http://jianshu.com](http://link.zhihu.com/?target=http%3A//jianshu.com)  
sudo tcpdump tcp port 80

**注意：sudo tcpdump tcp port 80 host**[**http://jianshu.com**](http://link.zhihu.com/?target=http%3A//jianshu.com)**  
这样写，会报  
tcpdump: 'tcp' modifier applied to host的错**  
这时有两种方法：  
1.使用and 关键字  
sudo tcpdump tcp port 80 and host[http://jianshu.com](http://link.zhihu.com/?target=http%3A//jianshu.com)  
2.使用管道来查看  
ping[http://jianshu.com](http://link.zhihu.com/?target=http%3A//jianshu.com)  
得到[http://jianshu.com](http://link.zhihu.com/?target=http%3A//jianshu.com)的ip 120.132.92.21  
sudo tcpdump tcp port 80 \| grep 120.132.92.21

#### 指定源和目标

这很简单，用src代表源;用dist代表目标  
sudo tcpdump src host 120.132.92.21

#### 使用与或非过滤

非是 ‘not ‘ ‘! ‘,与运算是’and’,’&&’;或运算 是’or’,’││’；  
我还是推荐用not and or 这样的词，当然符号也行，但这样更好理解。  
比如我们上面用到了and  
还可以用not或者or来筛选主机  
sudo tcpdump host \\(210.27.48.2 or 210.27.48.3 \\)  
这里用到了括号，用以简化形式，**一定注意，使用命令行时，括号要带上这两个斜杠，并且不能和括号直接有空格！**

#### 查看抓到的数据

如果你不带-X参数，那么抓到的只是这样的概述：  
**16:08:18.731680 IP 120.132.92.21.http &gt; 192.168.16.163.45134: Flags \[.\], ack 43441, win 461, options \[nop,nop,TS val 766985341 ecr 5849335\], length 0**  
大体是**系统时间 来源主机.端口 &gt; 目标主机.端口 数据包参数**

如果要查看详细的使用 -w 参数指定输出文件，或者带上-X参数。

我的建议是把数据输出到文件。输出的文件是16进制的，你可以用一些处理十六进制的命令读出来，例如使用xxd输出抓到的包的文件 zhuabao.txt  
cat zhuabao.txt \| xxd

    00000000: d4c3 b2a1 0200 0400 0000 0000 0000 0000  ................
    00000010: 0000 0400 0100 0000 d9a6 fc57 9311 0300  ...........W....
    00000020: 4a00 0000 4a00 0000 c83a 3560 0630 8c89  J...J....:5`.0..
    00000030: a5c3 787f 0800 4500 003c f8f6 4000 4006  ..x...E..
    <
    ..@.@.
    00000040: 8440 c0a8 10a3 b7fc 343d c530 0050 d40d  .@......4=.0.P..
    00000050: 0ae4 0000 0000 a002 7210 8184 0000 0204  ........r.......



