# Items

就相当于mvc中的model

---

#### 声名item

```py
import scrapy

class Product(scrapy.Item):
    name = scrapy.Field()
    price = scrapy.Field()
    stock = scrapy.Field()
    last_updated = scrapy.Field(serializer=str)
```

#### 创建item

```py
product = Product(name='Desktop PC', price=1000)
```

#### 获得item的field

```py
 product['name']
 product.get('name')
 product['last_updated']
 product.get('last_updated', 'not set')
```

#### 设置item的field的值

```py
product['last_updated'] = 'today'

product['lala'] = 'test' # setting unknown field
Traceback (most recent call last):
    ...
KeyError: 'Product does not support field: lala'
```

#### 获得所有的值

```py
>>> product.keys()
['price', 'name']

>>> product.items()
[('price', 1000), ('name', 'Desktop PC')]
```

#### 扩展

直接集成别的item就好了

```py
class DiscountedProduct(Product):
    discount_percent = scrapy.Field(serializer=str)
    discount_expiration_date = scrapy.Field()

class SpecificProduct(Product):
    name = scrapy.Field(Product.fields['name'], serializer=my_serializer)
```

#### 其他操作

##### 复制items

```py
product2 = Product(product)
product3 = product2.copy()
```

##### items转item

```py
dict(product)
```

##### 从dict创建item

```py
Product({'name': 'Laptop PC', 'price': 1500})
```



