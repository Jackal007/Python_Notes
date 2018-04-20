# Out-of-core naive Bayes model fitting

朴素贝叶斯模型可以用来解决大规模问题，所以整个训练集可能不会都被读入内存中。为了处理这种情况，[`MultinomialNB`](http://scikit-learn.org/stable/modules/generated/sklearn.naive_bayes.MultinomialNB.html#sklearn.naive_bayes.MultinomialNB)，[`BernoulliNB`](http://scikit-learn.org/stable/modules/generated/sklearn.naive_bayes.BernoulliNB.html#sklearn.naive_bayes.BernoulliNB)，和[`GaussianNB`](http://scikit-learn.org/stable/modules/generated/sklearn.naive_bayes.GaussianNB.html#sklearn.naive_bayes.GaussianNB)都有`partial_fit`方法，可以逐步用作其他分类如同行在证实法[的文本文档外的核心分类](http://scikit-learn.org/stable/auto_examples/applications/plot_out_of_core_classification.html#sphx-glr-auto-examples-applications-plot-out-of-core-classification-py)。所有朴素贝叶斯分类器都支持样本加权。

与该`fit`方法相反，第一次调用`partial_fit`需要通过所有预期类标签的列表。

> 有关scikit-learn中可用策略的概述，另请参阅[核心外学习](http://scikit-learn.org/stable/modules/scaling_strategies.html#scaling-strategies)文档。
>
> `partial_fit`朴素贝叶斯模型的方法调用引入了一些计算开销。建议使用尽可能大的数据块大小，即可用的RAM允许的大小。

