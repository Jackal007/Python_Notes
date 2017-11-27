# [ExtraTree](http://scikit-learn.org/stable/modules/generated/sklearn.tree.ExtraTreeClassifier.html#sklearn.tree.ExtraTreeClassifier)

```py
from sklearn import tree

X = [[0, 0], [1, 1]]
Y = [0, 1]
clf = tree.ExtraTreeClassifier()
clf = clf.fit(X, Y)
>>> clf.predict([[2., 2.]])
array([1])
```

---

```py
class sklearn.tree.ExtraTreeClassifier(
criterion=’gini’, 
splitter=’random’, 
max_depth=None, 
min_samples_split=2, 
min_samples_leaf=1, 
min_weight_fraction_leaf=0.0, 
max_features=’auto’, 
random_state=None, 
max_leaf_nodes=None, 
min_impurity_decrease=0.0,
min_impurity_split=None, 
class_weight=None
)
#见DecisionTree的
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



