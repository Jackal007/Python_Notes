# [DecisionTree](http://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html#sklearn.tree.DecisionTreeClassifier)

```py
from sklearn import tree

X = [[0, 0], [1, 1]]
Y = [0, 1]
clf = tree.DecisionTreeClassifier()
clf = clf.fit(X, Y)
>>> clf.predict([[2., 2.]])
array([1])
```

---

```py
class sklearn.tree.DecisionTreeClassifier(
criterion:"标准,可取gini、entropy"=’gini’, 
splitter:"best或random"=’best’, 
max_depth:"树的最大深度.如为None，则展开节点,直到所有叶子都是纯粹的,或者直到所有叶子都包含少于min_samples_split样本"=None, 
min_samples_split:"分割内部节点所需的最少样本数量.是int,作为最小数字;为float，为百分比"=2, 
min_samples_leaf:"需要在叶节点上的最小样本数量"=1, 
min_weight_fraction_leaf:""=0.0, 
max_features=None, 
random_state:"随机数种子或者随机数生成器"=None, 
max_leaf_nodes=None, 
min_impurity_split :"树木生长早期停止的阈值。如果一个节点的杂质高于阈值，节点将分裂，否则就是一片叶子[新版中变了]"=0.0, 
class_weight:"样本权重，比如{'label':weight}];对于多分类的见官网"=None, 
presort:"提前排序数据以加速拟合中的最佳分裂的发现,大数据集中，可能会减慢过程;当使用小的数据集或限制的深度时,可能会加速训练。"=False
)
```

---

### 属性

```py
classes_ : array of shape = [n_classes] or a list of such arrays
                The classes labels (single output problem), or a list of arrays of class labels (multi-output problem).

feature_importances_ : array of shape = [n_features]
                The feature importances. The higher, the more important the feature. The importance of a feature is computed as the (normalized) total reduction of the criterion brought by that feature. It is also known as the Gini importance [R251].

max_features_ : int,
                The inferred value of max_features.

n_classes_ : int or list
                The number of classes (for single output problems), or a list containing the number of classes for each output (for multi-output problems).

n_features_ : int
                The number of features when fit is performed.

n_outputs_ : int
                The number of outputs when fit is performed.

tree_ : Tree object
                The underlying Tree object.
```

---

### 方法

```py
apply（X，check_input = True ）    #返回每个样本被预测为的叶的索引

decision_path（X，check_input = True ）    #返回树中的决策路径

fit（X，y，sample_weight = None，check_input = True，X_idx_sorted = None ）    #训练

get_params（deep = True ）    #获取此估算器的参数

predict（X，check_input = True ）#预测

predict_log_proba（X ）    #预测输入样本X的类别对数概率

predict_proba（X，check_input = True ）    #预测输入样本X的类概率

score（X，y，sample_weight = None ）[source]    #返回给定测试数据和标签的平均精确度

set_params（** params )     #设置此分类器的参数
```



