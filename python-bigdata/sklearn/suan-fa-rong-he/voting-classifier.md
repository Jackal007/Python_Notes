# Voting Classifier

是结合概念上不同的机器学习分类器，并使用大多数投票或平均预测概率（软投票）来预测类标签。

这样的分类器可以用于一组同样表现良好的模型，以便平衡它们各自的弱点。

## 软投票和硬投票

▲多数投票（硬投票，hard voting）：多个分类器预测的结果不同时，采用权值最大的分类器的结果

▲软投票返回预测概率值的总和最大的标签。可通过参数weights指定每个分类器的权重；若权重提供了，在计算时则会按照权重计算，然后取平均；标签则为概率最高的标签。

举例说明，假设有3个分类器，3个类，每个分类器的**权重为：w1=1，w2=1，w3=1**。如下表：

| 分类器 | 标签1 | 标签2 | 标签3 |
| :--- | :--- | :--- | :--- |
| 分类器1 | W1\*0.2 | W1\*0.5 | W1\*0.3 |
| 分类器2 | W1\*0.6 | W1\*0.3 | W1\*0.1 |
| 分类器3 | W1\*0.3 | W1\*0.4 | W1\*0.3 |
| 权重平均 | 0.37 | 0.4（预测结果采用这个） | 0.23 |

```python
from sklearn import datasets
from sklearn.model_selection import cross_val_score
from sklearn.linear_model import LogisticRegression
from sklearn.naive_bayes import GaussianNB
from sklearn.ensemble import RandomForestClassifier
from sklearn.ensemble import VotingClassifier

iris = datasets.load_iris()
X, y = iris.data[:, 1:3], iris.target

clf1 = LogisticRegression(random_state=1)
clf2 = RandomForestClassifier(random_state=1)
clf3 = GaussianNB()

eclf = VotingClassifier(estimators=[('lr', clf1), ('rf', clf2), ('gnb', clf3)], voting='hard')

for clf, label in zip([clf1, clf2, clf3, eclf], ['Logistic Regression', 'Random Forest', 'naive Bayes', 'Ensemble']):
    scores = cross_val_score(clf, X, y, cv=5, scoring='accuracy')
    print("Accuracy: %0.2f (+/- %0.2f) [%s]" % (scores.mean(), scores.std(), label))

Accuracy: 0.90 (+/- 0.05) [Logistic Regression]
Accuracy: 0.93 (+/- 0.05) [Random Forest]
Accuracy: 0.91 (+/- 0.04) [naive Bayes]
Accuracy: 0.95 (+/- 0.05) [Ensemble]
```

