# Summary

* [介绍](README.md)
* [Basic Syntax](ji-ben-yu-fa.md)
  * [\_\_init\_\_.py的作用](ji-ben-yu-fa/init-py-de-zuo-yong.md)
  * [注释规范](ji-ben-yu-fa/zhu-shi-gui-fan.md)
  * [命名规范](ji-ben-yu-fa/ming-ming-gui-fan.md)
  * [特殊方法](ji-ben-yu-fa/te-shu-fang-fa.md)
    * [\_\_str\_\_和\_\_repr](ji-ben-yu-fa/te-shu-fang-fa/str-he-repr.md)
    * [\_\_len\_\_](ji-ben-yu-fa/te-shu-fang-fa/len.md)
* [Standard Modules](incide-packages.md)
  * [os](os.md)
  * [subprocess](subprocess.md)
  * [shlex](shlex.md)
  * [sys](sys.md)
* [Python Web](da-jian-wang-zhan.md)
  * [Django](da-jian-wang-zhan/django.md)
    * [创建项目](da-jian-wang-zhan/django/chuang-jian-yi-ge-xiang-mu.md)
    * [创建应用](da-jian-wang-zhan/django/chuang-jian-ying-yong.md)
      * [安装应用](da-jian-wang-zhan/django/chuang-jian-ying-yong/an-zhuang-ying-yong.md)
      * [编写应用视图](da-jian-wang-zhan/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu.md)
        * [页面模板](da-jian-wang-zhan/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/ye-mian.md)
          * [用法](da-jian-wang-zhan/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/ye-mian/yong-fa.md)
          * [内置后端](da-jian-wang-zhan/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/ye-mian/nei-zhi-hou-duan.md)
        * [Django模板语言](da-jian-wang-zhan/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/djangomo-ban-yu-yan.md)
          * [变量](da-jian-wang-zhan/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/djangomo-ban-yu-yan/bian-liang.md)
          * [标记](da-jian-wang-zhan/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/djangomo-ban-yu-yan/biao-ji.md)
          * [过滤器](da-jian-wang-zhan/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/djangomo-ban-yu-yan/guo-lv-qi.md)
          * [注释](da-jian-wang-zhan/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/djangomo-ban-yu-yan/zhu-shi.md)
    * [模型](da-jian-wang-zhan/django/mo-xing.md)
      * [创建模型](da-jian-wang-zhan/django/chuang-jian-mo-xing.md)
      * [模型字段类型](da-jian-wang-zhan/django/mo-xing/mo-xing-zi-duan-lei-xing.md)
      * [配置数据库](da-jian-wang-zhan/django/pei-zhi-shu-ju-ku.md)
    * [打开网站](da-jian-wang-zhan/django/da-kai-wang-zhan.md)
    * [管理模块](da-jian-wang-zhan/django/guan-li-mo-kuai.md)
    * [视图](da-jian-wang-zhan/django/shi-tu.md)
      * 基于类的视图
    * [message](da-jian-wang-zhan/django/message.md)
    * [auth](da-jian-wang-zhan/django/auth.md)
  * [web.py](da-jian-wang-zhan/webpy.md)
  * [规范WSGI](da-jian-wang-zhan/gui-fan-wsgi.md)
  * flask
* Python BigData
  * 5
  * [sklearn](fang-bian-de-bao/sklearn.md)
    * [Preprocessing预处理](fang-bian-de-bao/sklearn/preprocessing.md)
      * [MinMaxScaler](fang-bian-de-bao/sklearn/preprocessing/jiang-te-zheng-suo-fang-dao-yi-ge-fan-wei.md)
        * minmax\_scale
      * [FunctionTransformer](fang-bian-de-bao/sklearn/preprocessing/functiontransformer.md)
      * [Imputer](fang-bian-de-bao/sklearn/preprocessing/imputer.md)
      * [KernelCenterer](fang-bian-de-bao/sklearn/preprocessing/kernelcenterer.md)
      * [add\_dummy\_feature](fang-bian-de-bao/sklearn/preprocessing/adddummy-feature.md)
      * [Binarize](fang-bian-de-bao/sklearn/preprocessing/binarize.md)
      * [Normalizer](fang-bian-de-bao/sklearn/preprocessing/normalizer.md)
      * [Scale](fang-bian-de-bao/sklearn/preprocessing/scale.md)
        * [StandardScaler](fang-bian-de-bao/sklearn/preprocessing/scale/standardscaler.md)
      * [OneHotEncoder](fang-bian-de-bao/sklearn/preprocessing/onehotencoder.md)
    * [Feature Selection特征选择](fang-bian-de-bao/sklearn/feature-selection.md)
      * [SelectKBest](fang-bian-de-bao/sklearn/feature-selection/selectkbest.md)
      * [SelectPercentile](fang-bian-de-bao/sklearn/feature-selection/selectpercentile.md)
      * ...
    * [Estimator预测器](fang-bian-de-bao/sklearn/estimator.md)
      * [Regression](fang-bian-de-bao/sklearn/regression.md)
      * Clustering
      * [Classification](fang-bian-de-bao/sklearn/classification.md)
        * [Trees](fang-bian-de-bao/sklearn/classification/decision-trees.md)
          * [DecisionTree](fang-bian-de-bao/sklearn/classification/decision-trees/decisiontree.md)
          * [ExtraTree](fang-bian-de-bao/sklearn/classification/decision-trees/extratree.md)
        * [Naive Bayes](fang-bian-de-bao/sklearn/classification/naive-bayes.md)
          * [Gaussian Naive Bayes](fang-bian-de-bao/sklearn/classification/naive-bayes/gaussian-naive-bayes.md)
          * [Multinomial Naive Bayes](fang-bian-de-bao/sklearn/classification/naive-bayes/multinomial-naive-bayes.md)
          * [Bernoulli Naive Bayes](fang-bian-de-bao/sklearn/classification/naive-bayes/bernoulli-naive-bayes.md)
          * [Out-of-core naive Bayes model fitting](fang-bian-de-bao/sklearn/classification/naive-bayes/out-of-core-naive-bayes-model-fitting.md)
        * [Nearest Neighbors](fang-bian-de-bao/sklearn/classification/nearest-neighbors.md)
          * KDTree和BallTree类
        * Gaussian Processes
        * [Cross decomposition](fang-bian-de-bao/sklearn/classification/cross-decomposition.md)
    * [算法融合](fang-bian-de-bao/sklearn/classification/suan-fa-rong-he.md)
      * [Bagging meta-estimator](fang-bian-de-bao/sklearn/classification/suan-fa-rong-he/bagging-meta-estimator.md)
      * [Forests of randomized trees](fang-bian-de-bao/sklearn/classification/suan-fa-rong-he/forests-of-randomized-trees.md)
      * [AdaBoost](fang-bian-de-bao/sklearn/classification/suan-fa-rong-he/adaboost.md)
      * [Gradient Tree Boosting](fang-bian-de-bao/sklearn/classification/suan-fa-rong-he/gradient-tree-boosting.md)
      * [Voting Classifier](fang-bian-de-bao/sklearn/classification/suan-fa-rong-he/voting-classifier.md)
    * [Pipeline管道](fang-bian-de-bao/sklearn/pipeline.md)
      * [FeatureUnion](fang-bian-de-bao/sklearn/pipeline/featureunion.md)
        * [make\_union](fang-bian-de-bao/sklearn/pipeline/makeunion.md)
      * [Pipeline](fang-bian-de-bao/sklearn/pipeline/pipeline.md)
        * [make\_pipeline](fang-bian-de-bao/sklearn/pipeline/makepipeline.md)
    * [Model Selection模型选择，算法评估](fang-bian-de-bao/sklearn/model-selection.md)
  * [NumPy](fang-bian-de-bao/numpy.md)
    * [基本](fang-bian-de-bao/numpy/ji-ben.md)
    * [数组创建](fang-bian-de-bao/numpy/dui-xiang-chuang-jian.md)
  * [SciPy](fang-bian-de-bao/scipy.md)
  * matplotlib
* [Python Spider](pa-chong.md)
  * [反爬虫](pa-chong/fan-pa-chong.md)
  * [requests](pa-chong/requests.md)
    * [response](pa-chong/requests/response.md)
    * [data](pa-chong/requests/data.md)
    * [head](pa-chong/requests/head.md)
    * [session](pa-chong/requests/session.md)
    * [配置](pa-chong/requests/pei-zhi.md)
    * [exceptions](pa-chong/requests/exceptions.md)
  * [BeautifulSoup](pa-chong/beautifulsoup.md)
    * [对象](pa-chong/dui-xiang.md)
      * [Tag](pa-chong/dui-xiang/tag.md)
      * [NavigableString](pa-chong/dui-xiang/navigablestring.md)
      * [BeautifulSoup ](pa-chong/dui-xiang/beautifulsoup.md)
      * [Comment ](pa-chong/dui-xiang/comment.md)
    * [遍历文档树](pa-chong/bian-li-wen-dang-shu.md)
      * [子节点](pa-chong/bian-li-wen-dang-shu/zi-jie-dian.md)
        * [tag的名字](pa-chong/bian-li-wen-dang-shu/zi-jie-dian/tagde-ming-zi.md)
        * [.contents 和 .children](pa-chong/bian-li-wen-dang-shu/zi-jie-dian/contents-he-children.md)
        * [.descendants](pa-chong/bian-li-wen-dang-shu/zi-jie-dian/descendants.md)
        * [.string](pa-chong/bian-li-wen-dang-shu/zi-jie-dian/string.md)
        * [.strings 和 stripped\_strings](pa-chong/bian-li-wen-dang-shu/zi-jie-dian/strings-he-stripped-strings.md)
      * [父节点](pa-chong/bian-li-wen-dang-shu/fu-jie-dian.md)
        * [.parent](pa-chong/bian-li-wen-dang-shu/fu-jie-dian/parent.md)
        * [.parents](pa-chong/bian-li-wen-dang-shu/fu-jie-dian/parents.md)
      * [兄弟节点](pa-chong/bian-li-wen-dang-shu/xiong-di-jie-dian.md)
        * [.next\_sibling 和 .previous\_sibling](pa-chong/bian-li-wen-dang-shu/xiong-di-jie-dian/nextsibling-he-previoussibling.md)
        * [.next\_siblings 和 .previous\_siblings](pa-chong/bian-li-wen-dang-shu/xiong-di-jie-dian/nextsiblings-he-previoussiblings.md)
        * [回退和前进](pa-chong/bian-li-wen-dang-shu/xiong-di-jie-dian/hui-tui-he-qian-jin.md)
        * [.next\_element 和 .previous\_element](pa-chong/bian-li-wen-dang-shu/xiong-di-jie-dian/nextelement-he-previouselement.md)
        * [.next\_elements 和 .previous\_elements](pa-chong/bian-li-wen-dang-shu/xiong-di-jie-dian/nextelements-he-previouselements.md)
    * 搜索文档树
      * [CSS选择器](pa-chong/cssxuan-ze-qi.md)
      * [过滤器](pa-chong/guo-lv-qi.md)
        * [字符串](pa-chong/guo-lv-qi/zi-fu-chuan.md)
        * [正则表达式](pa-chong/guo-lv-qi/zheng-ze-biao-da-shi.md)
        * [列表](pa-chong/guo-lv-qi/lie-biao.md)
        * [True](pa-chong/guo-lv-qi/true.md)
        * [方法](pa-chong/guo-lv-qi/fang-fa.md)
      * [find\_all\(\)](pa-chong/findall.md)
        * [name参数](pa-chong/findall/namecan-shu.md)
        * [keyword参数](pa-chong/findall/keywordcan-shu.md)
        * [按CSS搜索](pa-chong/findall/an-css-sou-suo.md)
        * [string参数](pa-chong/findall/stringcan-shu.md)
        * [limit参数](pa-chong/findall/limitcan-shu.md)
        * [recursive 参数](pa-chong/findall/recursive-can-shu.md)
      * [像调用 find\_all\(\) 一样调用tag](pa-chong/xiang-diao-yong-find-all-yi-yang-diao-yong-tag.md)
      * [find\(\)](pa-chong/find.md)
      * find\_parents\(\) 和 find\_parent\(\)
      * find\_next\_siblings\(\) 合 find\_next\_sibling\(\)
      * find\_previous\_siblings\(\) 和 find\_previous\_sibling\(\)
      * find\_previous\_siblings\(\) 和 find\_previous\_sibling\(\)
      * find\_all\_next\(\) 和 find\_next\(\)
      * find\_all\_next\(\) 和 find\_next\(\)
      * find\_all\_next\(\) 和 find\_next\(\)
      * find\_all\_next\(\) 和 find\_next\(\)
      * find\_all\_previous\(\) 和 find\_previous\(\)
    * [修改文档树](pa-chong/xiu-gai-wen-dang-shu.md)
      * 修改tag的名称和属性
      * 修改 .string
      * append\(\)
      * NavigableString\(\) 和 .new\_tag\(\)
      * insert\(\)
      * insert\_before\(\) 和 insert\_after\(\)
      * clear\(\)
      * extract\(\)
      * decompose\(\)
      * replace\_with\(\)
      * wrap\(\)
      * unwrap\(\)
  * [selenium](pa-chong/selenium.md)
    * [定位元素](pa-chong/selenium/ding-wei.md)
      * 通过id
      * 通过class
      * 通过name
      * 通过XPath
      * 通过链接文本定位链接
      * 通过标签名
      * [使用css选择器](pa-chong/selenium/shi-yong-css-xuan-ze-qi.md)
    * [对元素进行操作](pa-chong/selenium/ye-mian-yuan-su.md)
      * [key](pa-chong/selenium/ye-mian-yuan-su/key.md)
    * [等待](pa-chong/selenium/deng-dai.md)
      * 显示等待
      * 隐式等待
    * WebDriver
      * 异常
    * exceptions
  * [scrapy](pa-chong/scrapy.md)
    * [安装](pa-chong/scrapy/an-zhuang.md)
    * [创建项目](pa-chong/scrapy/chuang-jian-xiang-mu.md)
    * [基本概念](pa-chong/scrapy/ji-ben-gai-nian.md)
      * [Spiders](pa-chong/scrapy/ji-ben-gai-nian/spider.md)
        * [scrapy.Spider](pa-chong/scrapy/ji-ben-gai-nian/spider/scrapyspider.md)
        * Spider arguments
        * Generic Spiders
          * CrawlSpider
          * XMLFeedSpider
          * CSVSpider
          * SitemapSider
      * [Selector](pa-chong/scrapy/ji-ben-gai-nian/selector.md)
      * [Items](pa-chong/scrapy/ji-ben-gai-nian/items.md)
      * Item Loaders
      * Scrapy Shell
      * Item Pipeline
      * Feed exports
      * Requests
      * Responses
      * Link Extractors
      * [Settings](pa-chong/scrapy/ji-ben-gai-nian/settings.md)
      * Exceptions
      * Command line tool
    * 内置服务
* [Python Hacker](python-hacker.md)
  * [python-nmap](python-hacker/nmap.md)
    * [nmap软件使用手册](python-hacker/nmap/nmapruan-jian-shi-yong-shou-ce.md)
  * pywifi 处理wifi
  * [socket](python-hacker/socket.md)
  * [pexpect](python-hacker/pexpect.md)
  * Metasploit
* [Other Packages](fang-bian-de-bao.md)
  * tqdm 显示进度
  * [win32](fang-bian-de-bao/win32.md)
  * [pytube下载视频](fang-bian-de-bao/pytubexia-zai-shi-pin.md)
  * SQLite
  * [optparse 处理脚本的选项](fang-bian-de-bao/optparse-chu-li-jiao-ben-de-xuan-xiang.md)
* [Debug](dai-ma-diao-shi.md)
  * [PDB](dai-ma-diao-shi/pdb.md)
  * [PyDev](dai-ma-diao-shi/pydev.md)
  * [日志功能](dai-ma-diao-shi/ri-zhi-gong-neng.md)
* incide Packages

