# SelectPercentile

```py
class sklearn.feature_selection.SelectKBest(
score_func:"计算分数的函数"=<function f_classif>, 
percentile:"重要程度高于这个百分数的值的特征将被选择"=10
)
```

根据特征重要程度的百分数得分进行选择

---

### 属性：

**scores\_**: array-like, shape=\(n\_features,\)

> 特征的得分

**percentile**: int, optional, default=10

> Percent of features to keep.

---

### 方法：

| `fit`（X \[，y\]） | 训练，并计算X |
| :--- | :--- |
| [`fit_transform`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.fit_transform)（X \[，y\]） | 适合数据，然后转换它。 |
| [`get_params`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.get_params)（_deep=True_） | 获取此估算器的参数。 |
| get\_support\(\[indices\]\) | Get a mask, or integer index, of the features selected |
| inverse\_transform\(X\)  |  Reverse the transformation operation |
| [`set_params`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.set_params)（\*\* PARAMS） | 设置此估算器的参数。 |
| [`transform`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.transform)（X \[，y，copy\]） | 二进制化X的 |



