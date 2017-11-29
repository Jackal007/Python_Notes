# [`sklearn.pipeline`](http://scikit-learn.org/stable/modules/classes.html#module-sklearn.pipeline).make\_union

```py
sklearn.pipeline.make_union(*transformers, **kwargs)
```

Construct a FeatureUnion from the given transformers.

This is a shorthand for the FeatureUnion constructor; it does not require, and does not permit, naming the transformers. Instead, they will be given names automatically based on their types. It also does not allow weighting.

| Parameters: | **\*transformers**: list of estimators**n\_jobs**: int, optionalNumber of jobs to run in parallel \(default 1\). |
| :--- | :--- |
| Returns: | **f**: FeatureUnion |

Examples

```py
>>> from sklearn.decomposition import PCA, TruncatedSVD
>>> from sklearn.pipeline import make_union
>>> make_union(PCA(), TruncatedSVD())    
FeatureUnion(n_jobs=1,
       transformer_list=[('pca',
                          PCA(copy=True, iterated_power='auto',
                              n_components=None, random_state=None,
                              svd_solver='auto', tol=0.0, whiten=False)),
                         ('truncatedsvd',
                          TruncatedSVD(algorithm='randomized',
                          n_components=2, n_iter=5,
                          random_state=None, tol=0.0))],
       transformer_weights=None)
```



