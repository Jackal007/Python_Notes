# MinMaxScaler

```py
class sklearn.preprocessing.MinMaxScaler(
feature_range=(0, 1), 
copy=True)

>>> from sklearn.preprocessing import MinMaxScaler
>>>
>>> data = [[-1, 2], [-0.5, 6], [0, 10], [1, 18]]
>>> scaler = MinMaxScaler()
>>> print(scaler.fit(data))
MinMaxScaler(copy=True, feature_range=(0, 1))
>>> print(scaler.data_max_)
[  1.  18.]
>>> print(scaler.transform(data))
[[ 0.    0.  ]
 [ 0.25  0.25]
 [ 0.5   0.5 ]
 [ 1.    1.  ]]
>>> print(scaler.transform([[2, 2]]))
[[ 1.5  0. ]]
```

将特征缩放到一个范围

---

### 属性：

**min\_**：ndarray，shape（n\_features，）

> 每个功能调整最小。

**scale\_**：ndarray，shape（n\_features，）

> 每个功能相对缩放的数据。
>
> 版本0.17中的新增功能：_scale\__属性。

**data\_min\_**：ndarray，shape（n\_features，）

> 每个功能在数据中看到的最小值
>
> 新版本0.17：_data\_min\__

**data\_max\_**：ndarray，shape（n\_features，）

> 每个功能在数据中最多可见
>
> 新版本0.17：_data\_max\__

**data\_range\_**：ndarray，shape（n\_features，）

> 每功能范围的数据可见`(data_max_-data_min_)`
>
> 新版本0.17：_data\_range\__

---

### 方法：

| `fit`（X \[，y\]） | 训练，并计算X |
| :--- | :--- |
| [`fit_transform`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.fit_transform)（X \[，y\]） | 适合数据，然后转换它。 |
| [`get_params`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.get_params)（_deep=True_） | 获取此估算器的参数。 |
| inverse\_transform\(X\) | Reverse the transformation operation |
| [`set_params`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.set_params)（\*\* PARAMS） | 设置此估算器的参数。 |
| [`transform`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.transform)（X \[，y，copy\]） | 二进制化X的 |
| partial\_fit\(X\[, y\]\) | Online computation of min and max on X for later scaling. |



