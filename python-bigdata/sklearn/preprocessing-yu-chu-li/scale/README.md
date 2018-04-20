# Scale

```python
sklearn.preprocessing.scale（
X，
axis = 0，
with_mean = True，
with_std = True，
copy = True 
）
```

还没写。下面是假的

## 参数：

**X**：{数组式，稀疏矩阵}

> 数据集中和缩放。

**axis**：int（默认为0）

> 轴用于计算平均值和标准偏差。如果是0，则独立标准化每个特征，否则（如果是1）标准化每个样本。

**with\_mean**：布尔值，默认为true

> 如果为True，则在缩放之前将数据居中。

**with\_std**：布尔值，默认为True

> 如果为真，则将数据缩放到单位差异（或等同于单位标准偏差）。

**复制**：布尔，可选，默认为True

> 设置为False来执行就地行规范化，并避免复制（如果输入已经是一个numpy数组或一个scipy.sparse CSC矩阵，如果axis是1）。

