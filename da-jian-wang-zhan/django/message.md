### https://www.cnblogs.com/jl-bai/p/6209653.html

### 一.简介

　　在网页应用中，你经常需要在处理完表单或其它类型的用户输入后，显示一个通知消息（也叫做“flash message”）给用户

对于这个功能，Django 提供基于Cookie 和会话的消息，无论是匿名用户还是认证的用户。

其消息框架允许你临时将消息存储在请求中，并在接下来的请求（通常就是下一个请求）中提取它们并显示。每个消息都带有一个特定level 标签，表示其优先级（例如info、warning 或error）

### 二.启用消息框架

消息框架的实现通过一个中间件 类和对应的context processor。

django-admin startproject 创建的默认settings.py  已经包含启用消息框架功能需要的所有的设置：

* INSTALLED\_APPS 中的'django.contrib.messages'。

* MIDDLEWARE\_CLASSES 中的'django.contrib.sessions.middleware.SessionMiddleware' 和'django.contrib.messages.middleware.MessageMiddleware'。

  默认的后端存储 依赖[sessions](http://python.usyiyi.cn/documents/django_182/topics/http/sessions.html)。所以MIDDLEWARE\_CLASSES 中必须启用SessionMiddleware 并出现在MessageMiddleware 之前。

* TEMPLATES 设置中定义的DjangoTemplates 的'context\_processors' 选项包含'django.contrib.messages.context\_processors.messages'。

如果你不想使用消息框架，你可以删除INSTALLED\_APPS 中的 'django.contrib.messages'、MIDDLEWARE\_CLASSES 中的MessageMiddleware 和TEMPLATES 中的messages context processo

#### 2.1 配置消息框架引擎



消息框架可以使用不同的后台存储临时消息。

Django 在[django.contrib.messages](http://python.usyiyi.cn/documents/django_182/ref/contrib/messages.html#module-django.contrib.messages) 中提供三个内建的存储类：

class 

storage.session.

SessionStorage

[  
](http://python.usyiyi.cn/documents/django_182/ref/contrib/messages.html#django.contrib.messages.storage.session.SessionStorage)

这个类存储所有的消息于请求的会话中。因此，它要求启用Django 的contrib.sessions 应用。

class 

storage.cookie.

CookieStorage

[  
](http://python.usyiyi.cn/documents/django_182/ref/contrib/messages.html#django.contrib.messages.storage.cookie.CookieStorage)

这个类存储消息数据于与Cookie 中（已经用一个安全的哈希进行签名以防止篡改）以在请求之间传递消息。如果Cookie 数据的大小将超过2048 字节，将丢弃旧的消息。

class 

storage.fallback.

FallbackStorage

[  
](http://python.usyiyi.cn/documents/django_182/ref/contrib/messages.html#django.contrib.messages.storage.fallback.FallbackStorage)

这个类首先使用CookieStorage，如果消息塞不进一个Cookie 中则使用SessionStorage。 它同样要求启用Django 的contrib.sessions 应用。

这个行为避免每次都写会话。在通常情况下，它提供的性能应该是最好的。

FallbackStorage 是默认的存储类。如果它不适合你的需要，你可以通过设置 MESSAGE\_STORAGE 为它的完整导入路径选择另外一个存储类，例如：

```
MESSAGE_STORAGE = 
'
django.contrib.messages.storage.cookie.CookieStorage
'
```

3.3 消息级别

消息框架的级别是可配置的，与Python logging 模块类似。消息的级别可以让你根据类型进行分组，这样它们能够在不同的视图和模板中过滤或显示出来

django.contrib.messages 导入的内建级别有：

| Constant | Purpose |
| :--- | :--- |
| DEBUG | Development-related messages that will be ignored \(or removed\) in a production deployment |
| INFO | Informational messages for the user |
| SUCCESS | An action was successful, e.g. “Your profile was updated successfully” |
| WARNING | A failure did not occur but may be imminent |
| ERROR | An action was **not** successful or some other failure occurred |

[MESSAGE\_LEVEL](http://python.usyiyi.cn/documents/django_182/ref/settings.html#std:setting-MESSAGE_LEVEL) 设置可以用来改变记录的最小级别（它还可以在每个请求中修改）。小于这个级别的消息将被忽略。

若要修改消息级别的默认标签，设置MESSAGE\_TAGS为包含你想要修改的级别的字典

```
from
 django.contrib.messages 
import
 constants as messages
MESSAGE_TAGS 
=
 {
    messages.INFO: 
''
,
    
50: 
'
critical
'
,
}
```

#### 3.3 在视图及模板中使用

```
add_message(request, level, message, extra_tags=
''
, fail_silently=False)
```

例 

新增消息

```
from
 django.contrib 
import
 messages
messages.add_message(request, messages.INFO, 
'
Hello world.
'
)
```

有几个快捷方法提供标准的方式来新增消息并带有常见的标签（这些标签通常表示消息的HTML 类型）

```
messages.debug(request, 
'
%s SQL statements were executed.
'
 %
 count)
messages.info(request, 
'
Three credits remain in your account.
'
)
messages.success(request, 
'
Profile details updated.
'
)
messages.warning(request, 
'
Your account expires in three days.
'
)
messages.error(request, 
'
Document deleted.
'
)
```

#### 3.4 显示消息

get\_messages\(request\)

**在你的模板中**，像下面这样使用：

[![](https://common.cnblogs.com/images/copycode.gif "复制代码")](javascript:void%280%29;)

```
{% 
if
 messages %
}

<
ul 
class
=
"
messages
"
>

    {
% 
for
 message 
in
 messages %
}
    
<
li{% 
if
 message.tags %} 
class
=
"
{{ message.tags }}
"
{% endif %}
>
{{ message }}
<
/li
>

    {
% endfor %
}

<
/ul
>

{
% endif %}
```

[![](https://common.cnblogs.com/images/copycode.gif "复制代码")](javascript:void%280%29;)

#### 三.配置使用

　　以上只是简单举例使用，看更详细文档请参考 [https://docs.djangoproject.com/en/1.10/ref/contrib/messages/](https://docs.djangoproject.com/en/1.10/ref/contrib/messages/)

　　在生产使用中我们可以把它整合成一个模块便于调用，结合前端显示当有错误或者其它信息时浏览器可以alert消息

例

![](http://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif)

settings

![](http://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif)

message method

![](http://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif)

前端显示

VIEWS调用

```
 result =
 XXXXX
      
if
 result:
         flash(request,
"
success
"
, 
"
成功！
"
)
      
else
:
         flash(request,
"
error
"
,  
"
。。。。
"
)
```



