# Django模板语言

> from:[http://usyiyi.cn/documents/Django\_111/ref/templates/language.html](http://usyiyi.cn/documents/Django_111/ref/templates/language.html)

## Django模板语言

Django模板是一个简单的文本文档，或用Django模板语言标记的一个Python字符串。某些结构是被模板引擎解释和识别的。主要的有变量和标签。

模板是由context来进行渲染的。渲染的过程是用在context中找到的值来替换模板中相应的变量，并执行相关tags。其他的一切都原样输出。

Django模板语言的语法包括四个结构。

