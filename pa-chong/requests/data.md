```
postdata={
```

```
    'xx':1,
    'xxx':2,
}
r = requests.put(self.start_url,  data=self.postdata)
```

提交表单后，可以使用chrome的开发者工具--&gt;NetWork，然后在下面选择相应的页面数据的header看formdata，就知道页面提交了哪些数据段了

