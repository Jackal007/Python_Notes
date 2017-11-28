# 合奏方法

**集合方法**的目标是结合使用给定的学习算法构建的几个基本估计量的预测，以便在单个估计量上提高可推广性/鲁棒性。

通常可以区分两种族的方法：

* 在**平均方法中**，驱动原则是独立地建立几个估计器，然后平均他们的预测。平均而言，组合估计量通常比任何单个基本估计量都好，因为它的方差减小了。

  **示例：**[装袋方法](http://scikit-learn.org/stable/modules/ensemble.html#bagging)，[随机树木森林](http://scikit-learn.org/stable/modules/ensemble.html#forest)，...

* 相比之下，在**增强方法中**，基本估计器是按顺序建立的，并且试图减少组合估计器的偏差。动机是结合几个弱模型来产生一个强大的合奏。

  **示例：**[AdaBoost](http://scikit-learn.org/stable/modules/ensemble.html#adaboost)，[渐变树增强](http://scikit-learn.org/stable/modules/ensemble.html#gradient-boosting)，...



