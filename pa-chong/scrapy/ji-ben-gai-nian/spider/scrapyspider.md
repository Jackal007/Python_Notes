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
  This attribute is set by the[`from_crawler()`](https://doc.scrapy.org/en/latest/topics/item-pipeline.html#from_crawler)class method after initializating the class, and links to the[`Crawler`](https://doc.scrapy.org/en/latest/topics/api.html#scrapy.crawler.Crawler)object to which this spider instance is bound.  
  Crawlers encapsulate a lot of components in the project for their single entry access \(such as extensions, middlewares, signals managers, etc\). See[Crawler API](https://doc.scrapy.org/en/latest/topics/api.html#topics-api-crawler)to know more about them.

* `settings`  
  要加载的配置

* `logger`  
  根据本Spider的名字创建的logger，可以记录log

##### 操作

* `from_crawler(crawler, *args, **kwargs)`  
  This is the class method used by Scrapy to create your spiders.

* `start_requests()、`  
  This method must return an iterable with the first Requests to crawl for this spider. It is called by Scrapy when the spider is opened for scraping. Scrapy calls it only once, so it is safe to implement start\_requests\(\) as a generator.  
  The default implementation generates Request\(url, dont\_filter=True\) for each url in start\_urls.  
  If you want to change the Requests used to start scraping a domain, this is the method to override. For example, if you need to start by logging in using a POST request, you could do:

  ```
  class MySpider(scrapy.Spider):
    name = 'myspider'

    def start_requests(self):
        return [scrapy.FormRequest("http://www.example.com/login",
                                   formdata={'user': 'john', 'pass': 'secret'},
                                   callback=self.logged_in)]

    def logged_in(self, response):
        # here you would extract links to follow and return Requests for
        # each of them, with another callback
        pass
  ```

* `parse(response)`  
  This is the default callback used by Scrapy to process downloaded responses, when their requests don’t specify a callback.  
  The`parse`method is in charge of processing the response and returning scraped data and/or more URLs to follow. Other Requests callbacks have the same requirements as the[`Spider`](https://doc.scrapy.org/en/latest/topics/spiders.html#scrapy.spiders.Spider)class.  
  This method, as well as any other Request callback, must return an iterable of[`Request`](https://doc.scrapy.org/en/latest/topics/request-response.html#scrapy.http.Request)and/or dicts or[`Item`](https://doc.scrapy.org/en/latest/topics/items.html#scrapy.item.Item)objects.  
  Parameters:  **response**\([`Response`](https://doc.scrapy.org/en/latest/topics/request-response.html#scrapy.http.Response)\) – the response to parse

* `log`\(_message_\[,_level_,_component_\]\)
Wrapper that sends a log message through the Spider’s[`logger`](https://doc.scrapy.org/en/latest/topics/spiders.html#scrapy.spiders.Spider.logger), kept for backwards compatibility. For more information see[Logging from Spiders](https://doc.scrapy.org/en/latest/topics/logging.html#topics-logging-from-spiders).

* `closed`\(_reason_\)
Called when the spider closes. This method provides a shortcut to signals.connect\(\) for the[`spider_closed`](https://doc.scrapy.org/en/latest/topics/signals.html#std:signal-spider_closed)signal.



