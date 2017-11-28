# OneHotEncoder独热编码

```py
class sklearn.preprocessing.OneHotEncoder（
n_values ='auto'，
categorical_features ='all'，
dtype = <class'numpy.float64'>，
sparse = True，
handle_unknown ='error' ）
```

假如只有一个特征是离散值：

　　　　{sex：{male， female，other}}

　　该特征总共有3个不同的分类值，此时需要3个bit位表示该特征是什么值，对应bit位为1的位置对应原来的特征的值（一般情况下可以将原始的特征的取值进行排序，以便于后期使用），此时得到独热码为{100}男性 ，{010}女性，{001}其他

　　假如多个特征需要独热码编码，那么久按照上面的方法依次将每个特征的独热码拼接起来：

　　　　{sex：{male， female，other}}

　　　　{grade：{一年级， 二年级，三年级， 四年级}}

　　此时对于输入为{sex：male； grade： 四年级}进行独热编码，可以首先将sex按照上面的进行编码得到{100}，然后按照grade进行编码为{0001}，那么两者连接起来得到最后的独热码{1000001}；

---

### 参数：

**n\_values**：'auto'，int或整数数组

> 每个功能的值数量。
>
> * “自动”：从训练数据中确定数值范围。
>
> * int
>   ：
>   每个要素的分类值数量。
>   每个特征值都应该在`range(n_values)`
>
> * 数组
>   ：
>   `n_values[i]`
>   是中的分类值的数量
>   `X[:,i]`。每个特征值都应该在`range(n_values[i])`

**categorical\_features**：“全部”或索引或掩码数组

> 指定哪些功能被视为分类。
>
> * “全部”（默认）：所有功能都被视为分类。
> * 索引数组：分类特征索引数组。
> * mask：长度为n\_features的数组，dtype = bool。
>
> 非分类特征总是堆叠在矩阵的右侧。

**dtype**：数字类型，默认= np.float

> 所需的dtype输出。

**稀疏**：布尔值，默认= True

> 如果设置True将返回稀疏矩阵否则将返回一个数组。

**handle\_unknown**：str，'错误'或'忽略'

> 在变换过程中是否存在未知类别特征时是否提出错误或忽略。

---

### 属性

**active\_features\_**：数组

> 活动特征的指标，意味着实际发生在训练集中的值。只有当n\_values是可用的`'auto'`。

**feature\_indices\_**：形状数组（n\_features，）

> 指数功能范围。特征`i`在原始数据被映射到特征从`feature_indices_[i]`到`feature_indices_[i+1]`（然后潜在地由掩蔽active\_features\_事后）

**n\_values\_**：形状数组（n\_features，）

> 每个功能的最大数量。

---

### 方法
| [`fit`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html#sklearn.preprocessing.OneHotEncoder.fit)\(X\[, y\]\) | Fit OneHotEncoder to X. |
| :--- | :--- |
| [`fit_transform`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html#sklearn.preprocessing.OneHotEncoder.fit_transform)\(X\[, y\]\) | Fit OneHotEncoder to X, then transform X. |
| [`get_params`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html#sklearn.preprocessing.OneHotEncoder.get_params)\(\[deep\]\) | Get parameters for this estimator. |
| [`set_params`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html#sklearn.preprocessing.OneHotEncoder.set_params)\(\*\*params\) | Set the parameters of this estimator. |
| [`transform`](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html#sklearn.preprocessing.OneHotEncoder.transform)\(X\) | Transform X using one-hot encoding. |



