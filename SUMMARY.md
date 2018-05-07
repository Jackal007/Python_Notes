# Table of contents

* [介绍](README.md)
* [Basic Syntax](basic-syntax/README.md)
  * [\_\_init\_\_.py的作用](basic-syntax/init.py-de-zuo-yong.md)
  * [注释规范](basic-syntax/zhu-shi-gui-fan.md)
  * [命名规范](basic-syntax/ming-ming-gui-fan.md)
  * [特殊方法](basic-syntax/te-shu-fang-fa/README.md)
    * [\_\_str\_\_和\_\_repr](basic-syntax/te-shu-fang-fa/str-he-repr.md)
    * [\_\_len\_\_](basic-syntax/te-shu-fang-fa/__len__.md)
  * [temp](basic-syntax/temp.md)
* [Standard Modules](standard-modules/README.md)
  * [os](standard-modules/os.md)
  * [subprocess](standard-modules/subprocess.md)
  * [shlex](standard-modules/shlex.md)
  * [sys](standard-modules/sys.md)
  * [ftplib](standard-modules/ftplib.md)
* [Python Web](python-web/README.md)
  * [Django](python-web/django/README.md)
    * [创建项目](python-web/django/chuang-jian-xiang-mu.md)
    * [创建应用](python-web/django/chuang-jian-ying-yong/README.md)
      * [安装应用](python-web/django/chuang-jian-ying-yong/an-zhuang-ying-yong.md)
      * [编写应用视图](python-web/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/README.md)
        * [页面模板](python-web/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/ye-mian-mo-ban/README.md)
          * [用法](python-web/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/ye-mian-mo-ban/yong-fa.md)
          * [内置后端](python-web/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/ye-mian-mo-ban/nei-zhi-hou-duan.md)
        * [Django模板语言](python-web/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/django-mo-ban-yu-yan/README.md)
          * [变量](python-web/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/django-mo-ban-yu-yan/bian-liang.md)
          * [标记](python-web/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/django-mo-ban-yu-yan/biao-ji.md)
          * [过滤器](python-web/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/django-mo-ban-yu-yan/guo-lv-qi.md)
          * [注释](python-web/django/chuang-jian-ying-yong/bian-xie-ying-yong-shi-tu/django-mo-ban-yu-yan/zhu-shi.md)
    * [模型](python-web/django/mo-xing/README.md)
      * [创建模型](python-web/django/mo-xing/chuang-jian-mo-xing.md)
      * [模型字段类型](python-web/django/mo-xing/mo-xing-zi-duan-lei-xing.md)
      * [配置数据库](python-web/django/mo-xing/pei-zhi-shu-ju-ku.md)
    * [打开网站](python-web/django/da-kai-wang-zhan.md)
    * [管理模块](python-web/django/guan-li-mo-kuai.md)
    * [视图](python-web/django/shi-tu/README.md)
      * 基于类的视图
    * [message](python-web/django/message.md)
    * [auth](python-web/django/auth.md)
  * [web.py](python-web/web.py.md)
  * [规范WSGI](python-web/gui-fan-wsgi.md)
  * flask
* Python BigData
  * 5
  * [sklearn](python-bigdata/sklearn/README.md)
    * [Preprocessing预处理](python-bigdata/sklearn/preprocessing-yu-chu-li/README.md)
      * [MinMaxScaler](python-bigdata/sklearn/preprocessing-yu-chu-li/minmaxscaler/README.md)
        * minmax\_scale
      * [FunctionTransformer](python-bigdata/sklearn/preprocessing-yu-chu-li/functiontransformer.md)
      * [Imputer](python-bigdata/sklearn/preprocessing-yu-chu-li/imputer.md)
      * [KernelCenterer](python-bigdata/sklearn/preprocessing-yu-chu-li/kernelcenterer.md)
      * [add\_dummy\_feature](python-bigdata/sklearn/preprocessing-yu-chu-li/add_dummy_feature.md)
      * [Binarize](python-bigdata/sklearn/preprocessing-yu-chu-li/binarize.md)
      * [Normalizer](python-bigdata/sklearn/preprocessing-yu-chu-li/normalizer.md)
      * [Scale](python-bigdata/sklearn/preprocessing-yu-chu-li/scale/README.md)
        * [StandardScaler](python-bigdata/sklearn/preprocessing-yu-chu-li/scale/standardscaler.md)
      * [OneHotEncoder](python-bigdata/sklearn/preprocessing-yu-chu-li/onehotencoder.md)
    * [Feature Selection特征选择](python-bigdata/sklearn/feature-selection-te-zheng-xuan-ze/README.md)
      * [SelectKBest](python-bigdata/sklearn/feature-selection-te-zheng-xuan-ze/selectkbest.md)
      * [SelectPercentile](python-bigdata/sklearn/feature-selection-te-zheng-xuan-ze/selectpercentile.md)
      * ...
    * [Estimator预测器](python-bigdata/sklearn/estimator-yu-ce-qi/README.md)
      * [Regression](python-bigdata/sklearn/estimator-yu-ce-qi/regression.md)
      * Clustering
      * [Classification](python-bigdata/sklearn/estimator-yu-ce-qi/classification/README.md)
        * [Trees](python-bigdata/sklearn/estimator-yu-ce-qi/classification/trees/README.md)
          * [DecisionTree](python-bigdata/sklearn/estimator-yu-ce-qi/classification/trees/decisiontree.md)
          * [ExtraTree](python-bigdata/sklearn/estimator-yu-ce-qi/classification/trees/extratree.md)
        * [Naive Bayes](python-bigdata/sklearn/estimator-yu-ce-qi/classification/naive-bayes/README.md)
          * [Gaussian Naive Bayes](python-bigdata/sklearn/estimator-yu-ce-qi/classification/naive-bayes/gaussian-naive-bayes.md)
          * [Multinomial Naive Bayes](python-bigdata/sklearn/estimator-yu-ce-qi/classification/naive-bayes/multinomial-naive-bayes.md)
          * [Bernoulli Naive Bayes](python-bigdata/sklearn/estimator-yu-ce-qi/classification/naive-bayes/bernoulli-naive-bayes.md)
          * [Out-of-core naive Bayes model fitting](python-bigdata/sklearn/estimator-yu-ce-qi/classification/naive-bayes/out-of-core-naive-bayes-model-fitting.md)
        * [Nearest Neighbors](python-bigdata/sklearn/estimator-yu-ce-qi/classification/nearest-neighbors/README.md)
          * KDTree和BallTree类
        * Gaussian Processes
        * [Cross decomposition](python-bigdata/sklearn/estimator-yu-ce-qi/classification/cross-decomposition.md)
    * [算法融合](python-bigdata/sklearn/suan-fa-rong-he/README.md)
      * [Bagging meta-estimator](python-bigdata/sklearn/suan-fa-rong-he/bagging-meta-estimator.md)
      * [Forests of randomized trees](python-bigdata/sklearn/suan-fa-rong-he/forests-of-randomized-trees.md)
      * [AdaBoost](python-bigdata/sklearn/suan-fa-rong-he/adaboost.md)
      * [Gradient Tree Boosting](python-bigdata/sklearn/suan-fa-rong-he/gradient-tree-boosting.md)
      * [Voting Classifier](python-bigdata/sklearn/suan-fa-rong-he/voting-classifier.md)
    * [Pipeline管道](python-bigdata/sklearn/pipeline-guan-dao/README.md)
      * [FeatureUnion](python-bigdata/sklearn/pipeline-guan-dao/featureunion/README.md)
        * [make\_union](python-bigdata/sklearn/pipeline-guan-dao/featureunion/make_union.md)
      * [Pipeline](python-bigdata/sklearn/pipeline-guan-dao/pipeline/README.md)
        * [make\_pipeline](python-bigdata/sklearn/pipeline-guan-dao/pipeline/make_pipeline.md)
    * [Model Selection模型选择，算法评估](python-bigdata/sklearn/model-selection-mo-xing-xuan-ze-suan-fa-ping-gu.md)
  * [NumPy](python-bigdata/numpy/README.md)
    * [基本](python-bigdata/numpy/ji-ben.md)
    * [数组创建](python-bigdata/numpy/shu-zu-chuang-jian.md)
  * [SciPy](python-bigdata/scipy.md)
  * matplotlib
* [Python Spider](python-spider/README.md)
  * [反爬虫](python-spider/fan-pa-chong.md)
  * [requests](python-spider/requests/README.md)
    * [response](python-spider/requests/response.md)
    * [data](python-spider/requests/data.md)
    * [head](python-spider/requests/head.md)
    * [session](python-spider/requests/session.md)
    * [配置](python-spider/requests/pei-zhi.md)
    * [exceptions](python-spider/requests/exceptions.md)
  * [BeautifulSoup](python-spider/beautifulsoup/README.md)
    * [对象](python-spider/beautifulsoup/dui-xiang/README.md)
      * [Tag](python-spider/beautifulsoup/dui-xiang/tag.md)
      * [NavigableString](python-spider/beautifulsoup/dui-xiang/navigablestring.md)
      * [BeautifulSoup](python-spider/beautifulsoup/dui-xiang/beautifulsoup.md)
      * [Comment](python-spider/beautifulsoup/dui-xiang/comment.md)
    * [遍历文档树](python-spider/beautifulsoup/bian-li-wen-dang-shu/README.md)
      * [子节点](python-spider/beautifulsoup/bian-li-wen-dang-shu/zi-jie-dian/README.md)
        * [tag的名字](python-spider/beautifulsoup/bian-li-wen-dang-shu/zi-jie-dian/tag-de-ming-zi.md)
        * [.contents 和 .children](python-spider/beautifulsoup/bian-li-wen-dang-shu/zi-jie-dian/.contents-he-.children.md)
        * [.descendants](python-spider/beautifulsoup/bian-li-wen-dang-shu/zi-jie-dian/.descendants.md)
        * [.string](python-spider/beautifulsoup/bian-li-wen-dang-shu/zi-jie-dian/.string.md)
        * [.strings 和 stripped\_strings](python-spider/beautifulsoup/bian-li-wen-dang-shu/zi-jie-dian/.strings-he-strippedstrings.md)
      * [父节点](python-spider/beautifulsoup/bian-li-wen-dang-shu/fu-jie-dian/README.md)
        * [.parent](python-spider/beautifulsoup/bian-li-wen-dang-shu/fu-jie-dian/.parent.md)
        * [.parents](python-spider/beautifulsoup/bian-li-wen-dang-shu/fu-jie-dian/.parents.md)
      * [兄弟节点](python-spider/beautifulsoup/bian-li-wen-dang-shu/xiong-di-jie-dian/README.md)
        * [.next\_sibling 和 .previous\_sibling](python-spider/beautifulsoup/bian-li-wen-dang-shu/xiong-di-jie-dian/.nextsibling-he-.previoussibling.md)
        * [.next\_siblings 和 .previous\_siblings](python-spider/beautifulsoup/bian-li-wen-dang-shu/xiong-di-jie-dian/.nextsiblings-he-.previoussiblings.md)
        * [回退和前进](python-spider/beautifulsoup/bian-li-wen-dang-shu/xiong-di-jie-dian/hui-tui-he-qian-jin.md)
        * [.next\_element 和 .previous\_element](python-spider/beautifulsoup/bian-li-wen-dang-shu/xiong-di-jie-dian/.nextelement-he-.previouselement.md)
        * [.next\_elements 和 .previous\_elements](python-spider/beautifulsoup/bian-li-wen-dang-shu/xiong-di-jie-dian/.nextelements-he-.previouselements.md)
    * 搜索文档树
      * [CSS选择器](python-spider/beautifulsoup/sou-suo-wen-dang-shu/css-xuan-ze-qi.md)
      * [过滤器](python-spider/beautifulsoup/sou-suo-wen-dang-shu/guo-lv-qi/README.md)
        * [字符串](python-spider/beautifulsoup/sou-suo-wen-dang-shu/guo-lv-qi/zi-fu-chuan.md)
        * [正则表达式](python-spider/beautifulsoup/sou-suo-wen-dang-shu/guo-lv-qi/zheng-ze-biao-da-shi.md)
        * [列表](python-spider/beautifulsoup/sou-suo-wen-dang-shu/guo-lv-qi/lie-biao.md)
        * [True](python-spider/beautifulsoup/sou-suo-wen-dang-shu/guo-lv-qi/true.md)
        * [方法](python-spider/beautifulsoup/sou-suo-wen-dang-shu/guo-lv-qi/fang-fa.md)
      * [find\_all\(\)](python-spider/beautifulsoup/sou-suo-wen-dang-shu/find_all/README.md)
        * [name参数](python-spider/beautifulsoup/sou-suo-wen-dang-shu/find_all/name-can-shu.md)
        * [keyword参数](python-spider/beautifulsoup/sou-suo-wen-dang-shu/find_all/keyword-can-shu.md)
        * [按CSS搜索](python-spider/beautifulsoup/sou-suo-wen-dang-shu/find_all/an-css-sou-suo.md)
        * [string参数](python-spider/beautifulsoup/sou-suo-wen-dang-shu/find_all/string-can-shu.md)
        * [limit参数](python-spider/beautifulsoup/sou-suo-wen-dang-shu/find_all/limit-can-shu.md)
        * [recursive 参数](python-spider/beautifulsoup/sou-suo-wen-dang-shu/find_all/recursive-can-shu.md)
      * [像调用 find\_all\(\) 一样调用tag](python-spider/beautifulsoup/sou-suo-wen-dang-shu/xiang-tiao-yong-findall-yi-yang-tiao-yong-tag.md)
      * [find\(\)](python-spider/beautifulsoup/sou-suo-wen-dang-shu/find.md)
      * find\_parents\(\) 和 find\_parent\(\)
      * find\_next\_siblings\(\) 合 find\_next\_sibling\(\)
      * find\_previous\_siblings\(\) 和 find\_previous\_sibling\(\)
      * find\_previous\_siblings\(\) 和 find\_previous\_sibling\(\)
      * find\_all\_next\(\) 和 find\_next\(\)
      * find\_all\_next\(\) 和 find\_next\(\)
      * find\_all\_next\(\) 和 find\_next\(\)
      * find\_all\_next\(\) 和 find\_next\(\)
      * find\_all\_previous\(\) 和 find\_previous\(\)
    * [修改文档树](python-spider/beautifulsoup/xiu-gai-wen-dang-shu/README.md)
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
  * [selenium](python-spider/selenium/README.md)
    * [定位元素](python-spider/selenium/ding-wei-yuan-su/README.md)
      * 通过id
      * 通过class
      * 通过name
      * 通过XPath
      * 通过链接文本定位链接
      * 通过标签名
      * [使用css选择器](python-spider/selenium/ding-wei-yuan-su/shi-yong-css-xuan-ze-qi.md)
    * [对元素进行操作](python-spider/selenium/dui-yuan-su-jin-hang-cao-zuo/README.md)
      * [key](python-spider/selenium/dui-yuan-su-jin-hang-cao-zuo/key.md)
    * [等待](python-spider/selenium/deng-dai/README.md)
      * 显示等待
      * 隐式等待
    * WebDriver
      * 异常
    * exceptions
  * [scrapy](python-spider/scrapy/README.md)
    * [安装](python-spider/scrapy/an-zhuang.md)
    * [创建项目](python-spider/scrapy/chuang-jian-xiang-mu.md)
    * [基本概念](python-spider/scrapy/ji-ben-gai-nian/README.md)
      * [Spiders](python-spider/scrapy/ji-ben-gai-nian/spiders/README.md)
        * [scrapy.Spider](python-spider/scrapy/ji-ben-gai-nian/spiders/scrapy.spider.md)
        * Spider arguments
        * Generic Spiders
          * CrawlSpider
          * XMLFeedSpider
          * CSVSpider
          * SitemapSider
      * [Selector](python-spider/scrapy/ji-ben-gai-nian/selector.md)
      * [Items](python-spider/scrapy/ji-ben-gai-nian/items.md)
      * Item Loaders
      * Scrapy Shell
      * Item Pipeline
      * Feed exports
      * Requests
      * Responses
      * Link Extractors
      * [Settings](python-spider/scrapy/ji-ben-gai-nian/settings.md)
      * Exceptions
      * Command line tool
    * 内置服务
* [Python Hacker](python-hacker/README.md)
  * [python-nmap](python-hacker/python-nmap/README.md)
    * [nmap软件使用手册](python-hacker/python-nmap/nmap-ruan-jian-shi-yong-shou-ce/README.md)
      * [hhhh](python-hacker/python-nmap/nmap-ruan-jian-shi-yong-shou-ce/hhhh/README.md)
        * [全面扫描](python-hacker/python-nmap/nmap-ruan-jian-shi-yong-shou-ce/hhhh/quan-mian-sao-miao.md)
      * [主机发现](python-hacker/python-nmap/nmap-ruan-jian-shi-yong-shou-ce/zhu-ji-fa-xian.md)
      * [端口扫描](python-hacker/python-nmap/nmap-ruan-jian-shi-yong-shou-ce/duan-kou-sao-miao.md)
      * [服务和版本探测](python-hacker/python-nmap/nmap-ruan-jian-shi-yong-shou-ce/fu-wu-he-ban-ben-tan-ce.md)
      * [操作系统探测](python-hacker/python-nmap/nmap-ruan-jian-shi-yong-shou-ce/cao-zuo-xi-tong-tan-ce.md)
      * [时间与性能](python-hacker/python-nmap/nmap-ruan-jian-shi-yong-shou-ce/shi-jian-yu-xing-neng.md)
      * [输出](python-hacker/python-nmap/nmap-ruan-jian-shi-yong-shou-ce/shu-chu.md)
      * [其他](python-hacker/python-nmap/nmap-ruan-jian-shi-yong-shou-ce/qi-ta.md)
    * [sdfsdf](python-hacker/python-nmap/sdfsdf.md)
  * [pexpect](python-hacker/pexpect/README.md)
    * [spawn类](python-hacker/pexpect/spawn-lei/README.md)
      * [expect方法](python-hacker/pexpect/spawn-lei/expect-fang-fa.md)
      * [read方法](python-hacker/pexpect/spawn-lei/read-fang-fa.md)
      * [send方法](python-hacker/pexpect/spawn-lei/send-fang-fa.md)
      * [run方法](python-hacker/pexpect/spawn-lei/run-fang-fa.md)
    * [pxssh类](python-hacker/pexpect/pxssh-lei.md)
  * pywifi 处理wifi
  * [socket](python-hacker/socket.md)
  * Metasploit
  * [ftplib](python-hacker/ftplib.md)
* [Other Packages](other-packages/README.md)
  * tqdm 显示进度
  * [win32](other-packages/win32.md)
  * [pytube下载视频](other-packages/pytube-xia-zai-shi-pin.md)
  * SQLite
  * [optparse 处理脚本的选项](other-packages/optparse-chu-li-jiao-ben-de-xuan-xiang.md)
  * ItChat
    * [给文件传输助手发一条信息](other-packages/itchat/gei-wen-jian-chuan-shu-zhu-shou-fa-yi-tiao-xin-xi.md)
    * [Untitled](other-packages/itchat/untitled.md)
* [Debug](debug/README.md)
  * [PDB](debug/pdb.md)
  * [PyDev](debug/pydev.md)
  * [日志功能](debug/ri-zhi-gong-neng.md)
* inside Packages
* Python APP

