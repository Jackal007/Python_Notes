# Items

就相当于mvc中的model

## 声名item

```python
import scrapy

class Product(scrapy.Item):
    name = scrapy.Field()
    price = scrapy.Field()
    stock = scrapy.Field()
    last_updated = scrapy.Field(serializer=str)
```

## 创建item

```python
product = Product(name='Desktop PC', price=1000)
```

## 获得item的field

```python
 product['name']
 product.get('name')
 product['last_updated']
 product.get('last_updated', 'not set')
```

## 设置item的field的值

```python
product['last_updated'] = 'today'

product['lala'] = 'test' # setting unknown field
Traceback (most recent call last):
    ...
KeyError: 'Product does not support field: lala'
```

## 获得所有的值

```python
>>> product.keys()
['price', 'name']

>>> product.items()
[('price', 1000), ('name', 'Desktop PC')]
```

## 扩展

直接集成别的item就好了

```python
class DiscountedProduct(Product):
    discount_percent = scrapy.Field(serializer=str)
    discount_expiration_date = scrapy.Field()

class SpecificProduct(Product):
    name = scrapy.Field(Product.fields['name'], serializer=my_serializer)
```

## 其他操作

### 复制items

```python
product2 = Product(product)
product3 = product2.copy()
```

### items转item

```python
dict(product)
```

### 从dict创建item

```python
Product({'name': 'Laptop PC', 'price': 1500})
```

