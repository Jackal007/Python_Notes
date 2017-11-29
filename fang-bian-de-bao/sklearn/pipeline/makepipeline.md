# [`sklearn.pipeline`](http://scikit-learn.org/stable/modules/classes.html#module-sklearn.pipeline).make\_pipeline

```py
sklearn.pipeline.make_pipeline（* steps，** kwargs ）
```



从给定的估计者构建管道。

这是Pipeline构造函数的简写。它不要求也不允许命名估计量。相反，他们的名字将被自动设置为它们类型的小写字母。

| 参数： | **\*步骤**：估算人员名单，**内存**：无，str或带有joblib.Memory接口的对象，可选用于缓存管道的拟合变压器。默认情况下，不执行缓存。如果给出了一个字符串，它就是缓存目录的路径。在启动缓存之前，启动一个克隆变压器。因此，给管道的变压器实例不能直接检查。使用该属性`named_steps`或`steps`检查管道内的估计器。当拟合费时时，高速缓存变压器是有利的。 |
| :--- | :--- |
| 返回： | **p**：管道 |

例子

```py
>>> from sklearn.naive_bayes import GaussianNB
>>> from sklearn.preprocessing import StandardScaler
>>> make_pipeline(StandardScaler(), GaussianNB(priors=None))
...     
Pipeline(memory=None,
         steps=[('standardscaler',
                 StandardScaler(copy=True, with_mean=True, with_std=True)),
                ('gaussiannb', GaussianNB(priors=None))])
```



