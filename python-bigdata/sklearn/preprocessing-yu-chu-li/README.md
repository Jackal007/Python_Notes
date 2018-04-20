# Preprocessing预处理

[`sklearn.preprocessing`](http://scikit-learn.org/stable/modules/classes.html#module-sklearn.preprocessing)

几个常用的效用函数和变换器类，用于将原始特征向量更改为更适合下游估计器的表示形式。

通常，学习算法从数据集的标准化中受益。如果在一组中存在一些异常值，则鲁棒的比例调整器或变压器更合适。[比较不同缩放](http://scikit-learn.org/stable/auto_examples/preprocessing/plot_all_scaling.html#sphx-glr-auto-examples-preprocessing-plot-all-scaling-py)比例[对数据与异常值的影响，](http://scikit-learn.org/stable/auto_examples/preprocessing/plot_all_scaling.html#sphx-glr-auto-examples-preprocessing-plot-all-scaling-py)突出显示[不同缩放](http://scikit-learn.org/stable/auto_examples/preprocessing/plot_all_scaling.html#sphx-glr-auto-examples-preprocessing-plot-all-scaling-py)比例，变换比例和归一化数据在包含边缘离群值的数据集上的行为。

| 包 | 类 | 参数列表 | 类别 | fit方法有用 | 说明 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| sklearn.preprocessing | StandardScaler | 特征 | 无监督 | Y | 标准化 |
| sklearn.preprocessing | MinMaxScaler | 特征 | 无监督 | Y | 区间缩放 |
| sklearn.preprocessing | Normalizer | 特征 | 无信息 | N | 归一化 |
| sklearn.preprocessing | Binarizer | 特征 | 无信息 | N | 定量特征二值化 |
| sklearn.preprocessing | OneHotEncoder | 特征 | 无监督 | Y | 定性特征编码 |
| sklearn.preprocessing | Imputer | 特征 | 无监督 | Y | 缺失值计算 |
| sklearn.preprocessing | PolynomialFeatures | 特征 | 无信息 | N | 多项式变换（fit方法仅仅生成了多项式的表达式） |
| sklearn.preprocessing | FunctionTransformer | 特征 | 无信息 | N | 自定义函数变换（自定义函数在transform方法中调用） |
| sklearn.feature\_selection | VarianceThreshold | 特征 | 无监督 | Y | 方差选择法 |
| sklearn.feature\_selection | SelectKBest | 特征/特征+目标值 | 无监督/有监督 | Y | 自定义特征评分选择法 |
| sklearn.feature\_selection | SelectKBest+chi2 | 特征+目标值 | 有监督 | Y | 卡方检验选择法 |
| sklearn.feature\_selection | RFE | 特征+目标值 | 有监督 | Y | 递归特征消除法 |
| sklearn.feature\_selection | SelectFromModel | 特征+目标值 | 有监督 | Y | 自定义模型训练选择法 |
| sklearn.decomposition | PCA | 特征 | 无监督 | Y | PCA降维 |
| sklearn.lda | LDA | 特征+目标值 | 有监督 | Y | LDA降维 |

## 例子：

```python
from sklearn import preprocessing
import numpy as np
X_train = np.array([[ 1., -1.,  2.],
                    [ 2.,  0.,  0.],
                    [ 0.,  1., -1.]])
X_scaled = preprocessing.scale(X_train)

X_scaled       
array([[ 0.  ..., -1.22...,  1.33...],
       [ 1.22...,  0.  ..., -0.26...],
       [-1.22...,  1.22..., -1.06...]])

#Scaled data has zero mean and unit variance:
>>> X_scaled.mean(axis=0)
array([ 0.,  0.,  0.])

>>> X_scaled.std(axis=0)
array([ 1.,  1.,  1.])
```

`preprocessing`模块还提供了实用程序类[`StandardScaler`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html#sklearn.preprocessing.StandardScaler)，该实用程序类实现`Transformer`API来计算训练集上的均值和标准差，以便能够稍后在测试集上重新应用相同的变换。因此，这个类适用于以下几个步骤的早期阶段[`sklearn.pipeline.Pipeline`](http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html#sklearn.pipeline.Pipeline)：

```python
>>> scaler = preprocessing.StandardScaler().fit(X_train)
>>> scaler
StandardScaler(copy=True, with_mean=True, with_std=True)

>>> scaler.mean_                                      
array([ 1. ...,  0. ...,  0.33...])

>>> scaler.scale_                                       
array([ 0.81...,  0.81...,  1.24...])

>>> scaler.transform(X_train)                           
array([[ 0.  ..., -1.22...,  1.33...],
       [ 1.22...,  0.  ..., -0.26...],
       [-1.22...,  1.22..., -1.06...]])

#The scaler instance can then be used on new data to transform it the same way it did on the training set:
>>> X_test = [[-1., 1., 0.]]
>>> scaler.transform(X_test)                
array([[-2.44...,  1.22..., -0.26...]])
```

可以通过传递with\_mean=False或with\_std=False构造函数禁用居中或缩放StandardScaler。

