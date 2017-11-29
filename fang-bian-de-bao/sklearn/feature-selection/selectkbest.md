# SelectKBest

```py
class sklearn.feature_selection.SelectKBest(
score_func:"计算分数的函数"=<function f_classif>, 
k:"要选的特征的数量"=10
)
```

选出k个分数最高的特征

---

### 属性：

**scores\_**: array-like, shape=\(n\_features,\)

> 特征的得分

**pvalues\_**: array-like, shape=\(n\_features,\)

> p-values of feature scores, None ifscore\_funcreturned only scores.

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



