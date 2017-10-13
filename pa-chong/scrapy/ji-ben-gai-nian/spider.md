### Spider

一个Spider定义爬取的一个网站或者一组网站以及爬法（怎么爬，爬前预处理，爬后怎么保存数据）。

一个爬虫的爬取过程包括：

1. 根据第一个URL生成初始的 Requests，然后确定一个回调函数来处理收到的响应
2. 调用[`start_requests()`](https://doc.scrapy.org/en/latest/topics/spiders.html#scrapy.spiders.Spider.start_requests)来处理第一个请求，它通常是从[`start_urls`](https://doc.scrapy.org/en/latest/topics/spiders.html#scrapy.spiders.Spider.start_urls)来生成Request，然后用[`parse`](https://doc.scrapy.org/en/latest/topics/spiders.html#scrapy.spiders.Spider.parse)作为回调函数来处理响应
3. In the callback function, you parse the response \(web page\) and return either dicts with extracted data,[`Item`](https://doc.scrapy.org/en/latest/topics/items.html#scrapy.item.Item)objects,[`Request`](https://doc.scrapy.org/en/latest/topics/request-response.html#scrapy.http.Request)objects, or an iterable of these objects. Those Requests will also contain a callback \(maybe the same\) and will then be downloaded by Scrapy and then their response handled by the specified callback.
4. In callback functions, you parse the page contents, typically using[Selectors](https://doc.scrapy.org/en/latest/topics/selectors.html#topics-selectors)\(but you can also use BeautifulSoup, lxml or whatever mechanism you prefer\) and generate items with the parsed data.
5. Finally, the items returned from the spider will be typically persisted to a database \(in some[Item Pipeline](https://doc.scrapy.org/en/latest/topics/item-pipeline.html#topics-item-pipeline)\) or written to a file using[Feed exports](https://doc.scrapy.org/en/latest/topics/feed-exports.html#topics-feed-exports).

Even though this cycle applies \(more or less\) to any kind of spider, there are different kinds of default spiders bundled into Scrapy for different purposes. We will talk about those types here.

