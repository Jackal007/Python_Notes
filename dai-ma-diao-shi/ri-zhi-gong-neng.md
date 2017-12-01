## 使用日志功能达到调试的目的 {#major4}

日志信息是软件开发过程中进行调试的一种非常有用的方式，特别是在大型软件开发过程需要很多相关人员进行协作的情况下。开发人员通过在代码中加入一些特定的能够记录软件运行过程中的各种事件信息能够有利于甄别代码中存在的问题。这些信息可能包括时间，描述信息以及错误或者异常发生时候的特定上下文信息。 最原始的 debug 方法是通过在代码中嵌入 print 语句，通过输出一些相关的信息来定位程序的问题。但这种方法有一定的缺陷，正常的程序输出和 debug 信息混合在一起，给分析带来一定困难，当程序调试结束不再需要 debug 输出的时候，通常没有很简单的方法将 print 的信息屏蔽掉或者定位到文件。python 中自带的 logging 模块可以比较方便的解决这些问题，它提供日志功能，将 logger 的 level 分为五个级别，可以通过 Logger.setLevel\(lvl\) 来设置。默认的级别为 warning。

##### 表 2. 日志的级别 {#N101A7}

| Level | 使用情形 |
| :--- | :--- |
| DEBUG | 详细的信息，在追踪问题的时候使用 |
| INFO | 正常的信息 |
| WARNING | 一些不可预见的问题发生，或者将要发生，如磁盘空间低等，但不影响程序的运行 |
| ERROR | 由于某些严重的问题，程序中的一些功能受到影响 |
| CRITICAL | 严重的错误，或者程序本身不能够继续运行 |

logging lib 包含 4 个主要对象

* logger:logger 是程序信息输出的接口。它分散在不同的代码中使得程序可以在运行的时候记录相应的信息，并根据设置的日志级别或 filter 来决定哪些信息需要输出并将这些信息分发到其关联的 handler。常用的方法有 Logger.setLevel\(\)，Logger.addHandler\(\) ，Logger.removeHandler\(\) ，Logger.addFilter\(\) ，Logger.debug\(\), Logger.info\(\), Logger.warning\(\), Logger.error\(\)，getLogger\(\) 等。logger 支持层次继承关系，子 logger 的名称通常是父 logger.name 的方式。如果不创建 logger 的实例，则使用默认的 root logger，通过 logging.getLogger\(\) 或者 logging.getLogger\(""\) 得到 root logger 实例。
* Handler:Handler 用来处理信息的输出，可以将信息输出到控制台，文件或者网络。可以通过 Logger.addHandler\(\) 来给 logger 对象添加 handler，常用的 handler 有 StreamHandler 和 FileHandler 类。StreamHandler 发送错误信息到流，而 FileHandler 类用于向文件输出日志信息，这两个 handler 定义在 logging 的核心模块中。其他的 hander 定义在 logging.handles 模块中，如 HTTPHandler,SocketHandler。
* Formatter:Formatter 则决定了 log 信息的格式 , 格式使用类似于 %\(
  &lt;
   dictionary key 
  &gt;
  \)s 的形式来定义，如'%\(asctime\)s - %\(levelname\)s - %\(message\)s'，支持的 key 可以在 python 自带的文档 LogRecord attributes 中查看。
* Filter:Filter 用来决定哪些信息需要输出。可以被 handler 和 logger 使用，支持层次关系，比如如果设置了 filter 为名称为 A.B 的 logger，则该 logger 和其子 logger 的信息会被输出，如 A.B,A.B.C.

```py
import logging 
LOG1=logging.getLogger('b.c') 
LOG2=logging.getLogger('d.e') 
filehandler = logging.FileHandler('test.log','a') 
formatter = logging.Formatter('%(name)s %(asctime)s %(levelname)s %(message)s') 
filehandler.setFormatter(formatter) 
filter=logging.Filter('b') 
filehandler.addFilter(filter) 
LOG1.addHandler(filehandler) 
LOG2.addHandler(filehandler) 
LOG1.setLevel(logging.INFO) 
LOG2.setLevel(logging.DEBUG) 
LOG1.debug('it is a debug info for log1') 
LOG1.info('normal infor for log1') 
LOG1.warning('warning info for log1:b.c') 
LOG1.error('error info for log1:abcd') 
LOG1.critical('critical info for log1:not worked') 
LOG2.debug('debug info for log2') 
LOG2.info('normal info for log2') 
LOG2.warning('warning info for log2') 
LOG2.error('error:b.c') 
LOG2.critical('critical')
```



