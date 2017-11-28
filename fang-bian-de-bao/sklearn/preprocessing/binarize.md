# Binarize二值化

```py
class sklearn.preprocessing.Binarizer(threshold=0.0, copy=True)
```

将数据二值化（根据阈值将特征值设置为0或1）

大于阈值的值映射到1，而小于或等于阈值的值映射到0.默认阈值为0时，只有正值映射到1。

二值化是文本计数数据的常用操作，分析人员可以决定只考虑是否存在某个特征，而不是量化出现次数。

它也可以用作考虑布尔随机变量的估计器的预处理步骤（例如，在贝叶斯设置中使用伯努利分布建模）。

这个估计器是无状态的（除了构造器参数），fit方法在流水线中使用时什么都不会有用。

---

### 参数：

**threshold**：float，可选（默认为0.0）

> 低于或等于此值的特征值被替换为0，高于该特征值1.对于稀疏矩阵上的操作，阈值可能不小于0。

**复制**：布尔，可选，默认为True

> 设置为False来执行就地二进制化并避免复制（如果输入已经是numpy数组或scipy.sparse CSR矩阵）。

---

### 方法：

| `fit`（X \[，y\]） | 不做任何事情，并保持估计不变\(只是为了实现API而已，废的\) |
| :--- | :--- |
| [`fit_transform`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.fit_transform)（X \[，y\]） | 适合数据，然后转换它。 |
| [`get_params`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.get_params)（_deep=True_） | 获取此估算器的参数。 |
| [`set_params`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.set_params)（\*\* PARAMS） | 设置此估算器的参数。 |
| [`transform`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.transform)（X \[，y，copy\]） | 二进制化X的 |



