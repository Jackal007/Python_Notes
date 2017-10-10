# Summary

* [介绍](README.md)
* [爬虫](pa-chong.md)
  * [反爬虫](pa-chong/fan-pa-chong.md)
  * 常用包
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
    * [requests](pa-chong/requests.md)
      * [response](pa-chong/requests/response.md)
      * [data](pa-chong/requests/data.md)
      * [head](pa-chong/requests/head.md)
      * [session](pa-chong/requests/session.md)
      * [配置](pa-chong/requests/pei-zhi.md)
      * [exceptions](pa-chong/requests/exceptions.md)
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
* [方便的包](fang-bian-de-bao.md)
  * pywifi

