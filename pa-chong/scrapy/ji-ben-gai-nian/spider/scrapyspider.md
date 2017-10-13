## scrapy.Spider

_class_`scrapy.spiders.Spider`

这是一个最基本的Spider，所有其他的Spider都要继承它。它没有提供特殊的函数，就提供来一个默认的[`start_requests()`](https://doc.scrapy.org/en/latest/topics/spiders.html#scrapy.spiders.Spider.start_requests)

##### 属性

* `name`  
  本Spider的名字，Scrapy会根据名字来找到这个Spider，所以名字必须唯一。

* `allowed_domains`  
  允许爬取的域名范围列表，不在范围内的网站将不会被爬取（前提是在设置里面将[`OffsiteMiddleware`](https://doc.scrapy.org/en/latest/topics/spider-middleware.html#scrapy.spidermiddlewares.offsite.OffsiteMiddleware)打开）。比如目标地址是' [https://www.baidu.com](https://www.baidu.com) '，那就要将' baidu.com '加入`allowed_domains`中

* `start_urls`

一个列表，内容为爬虫开始爬取的URL起点。如果没有在函数中指定一个特殊的起点，那么将把这个列表作为起点

* `custom_settings`

一个dict，它会在项目的setting中个性化本Spider的设置

* `crawler`





