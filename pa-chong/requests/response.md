#### _**clas**s _`requests.Response`

```
r=request.get(xxxbalabalaxxx);    //这个r就是response对象
```

每一个Request对象都会有一个response类成员，下表为response对象的属性

| config_= None_ |  |
| :--- | :--- |
| content_= None_ | 响应的内容，bytes形式 |
| cookies_= None_ | 服务器返回的cookie |
| encoding_= None_ | content的编码方式 |
| error_= None_ | request的HTTPError |
| headers_= None_ |  |
| history_= None_ | 请求的响应列表，比如重定向经过的路径 |
| iter\_content\(chunk\_size=10240, decode\_unicode=False\) | 该读入内存的字节大小，可以防止一次性将response都读入内存（这不一定是在解码可以发生时返回的每个项目的长度） |
| iter\_lines\(chunk\_size=10240, decode\_unicode=None\) | 同上 |
| raise\_for\_status | 保存着HTTPError或URLError |
| raw=None | 一个类似文件一样的对象，保存着响应 |
| request = None | 生成这个response的request |
| text | response的unicode内容，如果response的编码是空，chardet模块是可用的话，那么最终编码是不可测的 |
| url | response的最终url，即这个response是从url返回的 |



