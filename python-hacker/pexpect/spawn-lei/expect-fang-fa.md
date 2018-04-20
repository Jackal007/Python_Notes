# expect方法

expect定义了一个子程序输出的匹配规则。

```python
expect(
    pattern,# 表示字符串、pexpect.EOF(指向缓冲区尾部，无匹配项)、
            # pexpect.TIMEOUT(匹配等待超时）、正则表达式
            # 或者前面四种类型组成的列表（List），
            # 当pattern为一个列表时，且不止一个表列元素被匹配，
            # 则返回的结果是子程序输出最先出现的那个元素，或者是列表最左边的元素（最小索引ID）
    timeout=30, # 指定等待匹配结果的超时时间，单位为秒。当超时被触发时，expect将匹配到pexpect.TIMEOUT
    searchwindowsize=None # 匹配缓冲区字符串的位置，默认是从开始位置匹配
    )
```

```text
import pexpect
child = pexpect.spawn("echo 'foobar'")
print child.expect(['bar','foo','foobar'])
输出：1，即'foo'被匹配
```

```text
index = p.expect(['good','bad',pexpect.EOF,pexpect.TIMEOUT])
if index == 0:
  do_someting()
elif index ==1:
  do_something_else()
elif index ==2:
  do_some_other_thing()
elif index ==3:
  do_something_completely_different()
```

以上等价于

```text
try: 
  index = p.expect(['good','bad'])
  if index == 0:
    do_something()
  elif index == 1:
    do_something_else()
  except EOF:
    do_some_other_thiing()
  except TIMEOUT:
    do_something_completely_different()
```

expect 方法有两个非常棒的成员：before与after。before成员保存了最近匹配成功之前的内容，after成员保存了最近匹配成功之后的内容。例如：

```text
import pexpect
import sys
child = pexpect.spawn('ssh  root@127.0.0.1')
fout = file('mylog.txt','w')
#child.logfile = fout
child.logfile = sys.stdout
child.expect('password:')
child.sendline('123456')
print "before:" + child.before
print "after:" + child.after

运行结果：

before： root@127.0.0.1's
agter: password:
```

