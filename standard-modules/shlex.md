# shlex

shkex 模块最常见的用法就是其中的split 函数，split 函数提供了和shell 处理命令行参数时一致的分隔方式

代码示例：

```text
shlex.split("python -u a.py -a A    -b   B     -o test")
['python', '-u', 'a.py', '-a', 'A', '-b', 'B', '-o', 'test']
```

在shell 中，对于选项和对应的值之间可以有多个空格，而shlex.split 保持了和sell 一致的处理方式

从上述代码的运行结果，可以看出来

