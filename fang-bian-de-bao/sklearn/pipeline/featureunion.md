# FeatureUnion特征联合

```py
class sklearn.pipeline.FeatureUnion(
transformer_list, 
n_jobs=1, 
transformer_weights=None
)
```

连接多个`transformer`对象的结果。

该估算器将`transformer`对象列表与输入数据并行应用，然后连接结果。

将几个`transformer`组合成一个`transformer`器是非常有用的。

其实就是将多个特征选择器合成一个

---

### 参数：

**transformer\_list**：（字符串，变换器）元组列表

> 要应用于数据的变换器对象的列表。每个元组的前半部分是变压器的名称。

**n\_jobs**：int，可选

> 并行运行的作业数（默认值为1）。

**transformer\_weights**：字典，可选

> 每个变压器功能的乘法权重。键是变压器的名称，值的权重。

### 方法：

| fit（X \[，y\]） | 适合所有变压器使用X. |
| :--- | :--- |
| [`fit_transform`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.FeatureUnion.html#sklearn.pipeline.FeatureUnion.fit_transform)（X \[，y\]） | 适合所有变压器，变换数据并连接结果。 |
| [`get_feature_names`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.FeatureUnion.html#sklearn.pipeline.FeatureUnion.get_feature_names)（） | 从所有变压器获取功能名称。 |
| [`get_params`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.FeatureUnion.html#sklearn.pipeline.FeatureUnion.get_params)（\[深\]） | 获取此估算器的参数。 |
| [`set_params`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.FeatureUnion.html#sklearn.pipeline.FeatureUnion.set_params)（\*\* kwargs） | 设置此估算器的参数。 |
| [`transform`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.FeatureUnion.html#sklearn.pipeline.FeatureUnion.transform)（X） | 通过每个变压器分别变换X，连接结果。 |



