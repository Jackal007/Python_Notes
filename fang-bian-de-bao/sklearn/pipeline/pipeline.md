# Pipeline管道

```py
class sklearn.pipeline.Pipeline（
steps，
memory = None 
）
```

按顺序应用`transforms`列表和最终估计器。流水线的中间步骤必须是“`transforms`”，即必须实现`fit`和`transforms`的方法（最后的估算器只需要实现`fit`）。管道中的变换器可以使用memory参数进行缓存。

管道的目的是组装几个可以一起交叉验证的步骤，同时设置不同的参数。为此，它可以使用名称和参数名以“\_\_”分隔各个步骤来设置各个步骤。一个步骤的估算器可能完全根据参数名称替换为另一个估算器，或者通过设置为None来移除`transformer`。

---

### 参数：

**steps**：列表

> 链接的（名称，变换）元组的列表（实现拟合/变换），链接的顺序是最后一个对象是一个估计器。

**memory**：None，str或带有joblib.Memory接口的对象（可选）

> 用于缓存管道的拟合变压器。默认情况下，不执行缓存。如果给出了一个字符串，它就是缓存目录的路径。在启动缓存之前，启动一个克隆`transformer`。因此，给管道的`transformer`实例不能直接检查。使用该属性`named_steps`或`steps`检查管道内的估计器。如果fit十分费时，缓存`transformers`是有利的。

---

### 属性：

**named\_steps**：束对象，一个具有属性访问的字典

> 只读属性根据用户给定的名称访问任何步骤参数。键是步骤名称，值是步骤参数。

---

### 方法：

| `decision_function(X)` | Apply transforms, and decision\_function of the final estimator |
| :--- | :--- |
| [`fit`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html#sklearn.pipeline.Pipeline.fit)\(X\[, y\]\) | Fit the model |
| [`fit_predict`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html#sklearn.pipeline.Pipeline.fit_predict)\(X\[, y\]\) | Applies fit\_predict of last step in pipeline after transforms. |
| [`fit_transform`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html#sklearn.pipeline.Pipeline.fit_transform)\(X\[, y\]\) | Fit the model and transform with the final estimator |
| [`get_params`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html#sklearn.pipeline.Pipeline.get_params)\(\[deep\]\) | Get parameters for this estimator. |
| [`predict`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html#sklearn.pipeline.Pipeline.predict)\(X\) | Apply transforms to the data, and predict with the final estimator |
| [`predict_log_proba`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html#sklearn.pipeline.Pipeline.predict_log_proba)\(X\) | Apply transforms, and predict\_log\_proba of the final estimator |
| [`predict_proba`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html#sklearn.pipeline.Pipeline.predict_proba)\(X\) | Apply transforms, and predict\_proba of the final estimator |
| [`score`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html#sklearn.pipeline.Pipeline.score)\(X\[, y, sample\_weight\]\) | Apply transforms, and score with the final estimator |
| [`set_params`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html#sklearn.pipeline.Pipeline.set_params)\(\*\*kwargs\) | Set the parameters of this estimator. |

---

###  例子：

```py
>>> from sklearn import svm
>>> from sklearn.datasets import samples_generator
>>> from sklearn.feature_selection import SelectKBest
>>> from sklearn.feature_selection import f_regression
>>> from sklearn.pipeline import Pipeline
>>> # generate some data to play with
>>> X, y = samples_generator.make_classification(
...     n_informative=5, n_redundant=0, random_state=42)
>>> # ANOVA SVM-C
>>> anova_filter = SelectKBest(f_regression, k=5)
>>> clf = svm.SVC(kernel='linear')
>>> anova_svm = Pipeline([('anova', anova_filter), ('svc', clf)])
>>> # You can set the parameters using the names issued
>>> # For instance, fit using a k of 10 in the SelectKBest
>>> # and a parameter 'C' of the svm
>>> anova_svm.set_params(anova__k=10, svc__C=.1).fit(X, y)
...                      
Pipeline(memory=None,
         steps=[('anova', SelectKBest(...)),
                ('svc', SVC(...))])
>>> prediction = anova_svm.predict(X)
>>> anova_svm.score(X, y)                        
0.829...
>>> # getting the selected features chosen by anova_filter
>>> anova_svm.named_steps['anova'].get_support()
... 
array([False, False,  True,  True, False, False, True,  True, False,
       True,  False,  True,  True, False, True,  False, True, True,
       False, False], dtype=bool)
>>> # Another way to get selected features chosen by anova_filter
>>> anova_svm.named_steps.anova.get_support()
... 
array([False, False,  True,  True, False, False, True,  True, False,
       True,  False,  True,  True, False, True,  False, True, True,
       False, False], dtype=bool)
```



