# Imputer

```python
class sklearn.preprocessing.Imputer(
missing_values=’NaN’, 
strategy=’mean’, 
axis=0, 
verbose=0, 
copy=True)
```

填补缺失的数据

## 参数：

**missing\_values**：整数或“NaN”，可选（默认=“NaN”）

> 缺少值的占位符。所有发生的missing\_values将被计算。对于编码为np.nan的缺失值，使用字符串值“NaN”。

**strategy**：字符串，可选（默认=“平均”）

> 插补策略。
>
> * 如果“mean”，则用沿着轴的平均值代替缺失的值。
> * 如果“中位数”，则使用沿轴的中位数替换缺失值。
> * 如果“most\_frequent”，则使用轴上最频繁的值替换缺失。

**axis**：整数，可选（默认值= 0）

> 用来指示的轴线。
>
> * 如果
>
>   axis = 0
>
>   ，则沿着列进行置换。
>
> * 如果
>
>   axis = 1
>
>   ，则沿行排除。

**verbose**：整数，可选（默认= 0）

> 控制说话者的冗长。

**copy**：布尔值，可选（默认= True）

> 如果为True，则会创建一个X的副本。如果是假的，只要可能，插补将在原地完成。请注意，在下列情况下，即使copy = False，也总是会创建一个新副本：
>
> * 如果X不是浮点数组，
> * 如果X是稀疏的而且
>
>   missing\_values = 0;
>
> * 如果
>
>   axis = 0
>
>   并且X被编码为CSR矩阵;
>
> * 如果
>
>   axis = 1
>
>   并且X被编码为CSC矩阵。

## 属性：

**statistics\_**: array of shape \(n\_features,\)

> 轴== 0时，每个特征的插补填充值

## 方法：

| `fit`（X \[，y\]） | 训练，并计算X |
| :--- | :--- |
| [`fit_transform`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.fit_transform)（X \[，y\]） | 适合数据，然后转换它。 |
| [`get_params`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.get_params)（_deep=True_） | 获取此估算器的参数。 |
| [`set_params`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.set_params)（\*\* PARAMS） | 设置此估算器的参数。 |
| [`transform`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html#sklearn.preprocessing.Binarizer.transform)（X \[，y，copy\]） | 二进制化X的 |

