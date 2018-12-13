最近需要从文本中抽取结构化信息，用到了很多github上的包，遂整理了一下，后续会不断更新。

很多包非常有趣，值得收藏，满足大家的收集癖！
如果觉得有用，请分享并star，谢谢！

涉及内容包括：**中英文敏感词、语言检测、中外手机/电话归属地/运营商查询、名字推断性别、手机号抽取、身份证抽取、邮箱抽取、中日文人名库、中文缩写库、拆字词典、词汇情感值、停用词、反动词表、暴恐词表、繁简体转换、英文模拟中文发音、汪峰歌词生成器、职业名称词库、同义词库、反义词库、否定词库、汽车品牌词库、汽车零件词库、连续英文切割、各种中文词向量、公司名字大全、古诗词库、IT词库、财经词库、成语词库、地名词库、历史名人词库、诗词词库、医学词库、饮食词库、法律词库、汽车词库、动物词库、中文聊天语料、中文谣言数据**。

**1\. textfilter: 中英文敏感词过滤**  [observerss/textfilter](https://github.com/observerss/textfilter)
```
 >>> f = DFAFilter()
 >>> f.add("sexy")
 >>> f.filter("hello sexy baby")
 hello **** baby
```
敏感词包括政治、脏话等话题词汇。其原理主要是基于词典的查找（项目中的keyword文件），内容很劲爆。。。

**2\. langid：97种语言检测** [https://github.com/saffsd/langid.py](https://github.com/saffsd/langid.py)

> pip install langid
```
>>> import langid
>>> langid.classify("This is a test")
('en', -54.41310358047485)
```
**3\. langdetect：另一个语言检测**[https://code.google.com/archive/p/language-detection/](https://code.google.com/archive/p/language-detection/)

> pip install langdetect
```
from langdetect import detect
from langdetect import detect_langs

s1 = "本篇博客主要介绍两款语言探测工具，用于区分文本到底是什么语言，"
s2 = 'We are pleased to introduce today a new technology'
print(detect(s1))
print(detect(s2))
print(detect_langs(s3))    # detect_langs()输出探测出的所有语言类型及其所占的比例
```

输出结果如下： 注：语言类型主要参考的是ISO 639-1语言编码标准，详见[ISO 639-1百度百科](https://baike.baidu.com/item/ISO%20639-1)

跟上一个语言检测比较，准确率低，效率高。

**4\. phone 中国手机归属地查询：** [ls0f/phone](https://github.com/ls0f/phone)
```
from phone import Phone
p  = Phone()
p.find(18100065143)
#return {'phone': '18100065143', 'province': '上海', 'city': '上海', 'zip_code': '200000', 'area_code': '021', 'phone_type': '电信'}
```
支持号段: 13*,15*,18*,14[5,7],17[0,6,7,8]

记录条数: 360569 (updated:2017年4月)

作者提供了数据[phone.dat](https://github.com/lovedboy/phone/raw/master/phone/phone.dat) 方便非python用户Load数据。

**5\. phone国际手机、电话归属地查询：**[AfterShip/phone](https://github.com/AfterShip/phone)

> npm install phone
```
import phone from 'phone';
phone('+852 6569-8900'); // return ['+85265698900', 'HKG']
phone('(817) 569-8900'); // return ['+18175698900, 'USA']
```
**6\. ngender 根据名字判断性别：**[observerss/ngender](https://github.com/observerss/ngender)

> pip install ngender # 基于朴素贝叶斯计算的概率
```
>>> import ngender
>>> ngender.guess('赵本山')
('male', 0.9836229687547046)
>>> ngender.guess('宋丹丹')
('female', 0.9759486128949907)
```
**7\. 抽取email的正则表达式**
```
email_pattern = '^[*#\u4e00-\u9fa5 a-zA-Z0-9_.-]+@[a-zA-Z0-9-]+(\.[a-zA-Z0-9-]+)*\.[a-zA-Z0-9]{2,6}$'
emails = re.findall(email_pattern, text, flags=0)
```
**8\. 抽取phone_number的正则表达式**
```
cellphone_pattern = '^((13[0-9])|(14[0-9])|(15[0-9])|(17[0-9])|(18[0-9]))\d{8}$'
phoneNumbers = re.findall(cellphone_pattern, text, flags=0)
```
**9\. 抽取身份证号的正则表达式**
```
IDCards_pattern = r'^([1-9]\d{5}[12]\d{3}(0[1-9]|1[012])(0[1-9]|[12][0-9]|3[01])\d{3}[0-9xX])$'
IDs = re.findall(IDCards_pattern, text, flags=0)
```
**10.  人名语料库：** [wainshine/Chinese-Names-Corpus](https://github.com/wainshine/Chinese-Names-Corpus)
```
中文（现代、古代）名字、日文名字、中文的姓和名、称呼（大姨妈、小姨妈等）、英文->中文名字（李约翰）、成语词典
```
（可用于中文分词、姓名识别）

**11\. 中文缩写库：**[github](https://github.com/zhangyics/Chinese-abbreviation-dataset/blob/master/dev_set.txt)
```
全国人大: 全国/n 人民/n 代表大会/n
中国: 中华人民共和国/ns
女网赛: 女子/n 网球/n 比赛/vn
```
**12\. 汉语拆字词典：**[kfcd/chaizi](https://github.com/kfcd/chaizi)
```
漢字	拆法 (一)	拆法 (二)	拆法 (三)
拆	手 斥	扌 斥	才 斥
```
**13\. 词汇情感值：**[rainarch/SentiBridge](https://github.com/rainarch/SentiBridge/blob/master/Entity_Emotion_Express/CCF_data/pair_mine_result)
```
山泉水	充沛	0.400704566541	0.370067395878
视野	        宽广	0.305762728932	0.325320747491
大峡谷	惊险	0.312137906517	0.378594957281
```
**14\. 中文词库、停用词、敏感词** [dongxiexidian/Chinese](https://github.com/dongxiexidian/Chinese)

此package的敏感词库分类更细：

[反动词库](https://github.com/dongxiexidian/Chinese/blob/master/%E6%95%8F%E6%84%9F%E8%AF%8D%E5%BA%93/%E5%8F%8D%E5%8A%A8%E8%AF%8D%E5%BA%93.txt)， [敏感词库表统计](https://github.com/dongxiexidian/Chinese/blob/master/%E6%95%8F%E6%84%9F%E8%AF%8D%E5%BA%93/%E6%95%8F%E6%84%9F%E8%AF%8D%E5%BA%93%E8%A1%A8%E7%BB%9F%E8%AE%A1.txt)， [暴恐词库](https://github.com/dongxiexidian/Chinese/blob/master/%E6%95%8F%E6%84%9F%E8%AF%8D%E5%BA%93/%E6%9A%B4%E6%81%90%E8%AF%8D%E5%BA%93.txt)， [民生词库](https://github.com/dongxiexidian/Chinese/blob/master/%E6%95%8F%E6%84%9F%E8%AF%8D%E5%BA%93/%E6%B0%91%E7%94%9F%E8%AF%8D%E5%BA%93.txt)， [色情词库](https://github.com/dongxiexidian/Chinese/blob/master/%E6%95%8F%E6%84%9F%E8%AF%8D%E5%BA%93/%E8%89%B2%E6%83%85%E8%AF%8D%E5%BA%93.txt)

**15\. 汉字转拼音：**[mozillazg/python-pinyin](https://github.com/mozillazg/python-pinyin)

文本纠错会用到

**16\. 中文繁简体互转：**[skydark/nstools](https://github.com/skydark/nstools/tree/master/zhtools)

**17\. 英文模拟中文发音引擎** funny chinese text to speech enginee：[tinyfool/ChineseWithEnglish](https://github.com/tinyfool/ChineseWithEnglish)
```
say wo i ni
#说：我爱你
```
相当于用英文音标，模拟中文发音。

**18\. 汪峰歌词生成器：**[phunterlau/wangfeng-rnn](https://github.com/phunterlau/wangfeng-rnn)
```
我在这里中的夜里
就像一场是一种生命的意旪
就像我的生活变得在我一样
可我们这是一个知道
我只是一天你会怎吗
```
**19\. 同义词库、反义词库、否定词库：**[guotong1988/chinese_dictionary](https://github.com/guotong1988/chinese_dictionary)

**20\. 无空格英文串分割、抽取单词：**[wordinja](https://github.com/keredson/wordninja)
```
>>> import wordninja
>>> wordninja.split('derekanderson')
['derek', 'anderson']
>>> wordninja.split('imateapot')
['im', 'a', 'teapot']
```
**21\. IP地址正则表达式：**
```
(25[0-5]|2[0-4]\d|[0-1]\d{2}|[1-9]?\d)\.(25[0-5]|2[0-4]\d|[0-1]\d{2}|[1-9]?\d)\.(25[0-5]|2[0-4]\d|[0-1]\d{2}|[1-9]?\d)\.(25[0-5]|2[0-4]\d|[0-1]\d{2}|[1-9]?\d)
```
**22\. 腾讯QQ号正则表达式：**
```
[1-9]([0-9]{5,11})
```
**23\. 国内固话号码正则表达式：**
```
[0-9-()（）]{7,18}
```
**24\. 用户名正则表达式：**
```
[A-Za-z0-9_\-\u4e00-\u9fa5]+
```
**25\. 汽车品牌、汽车零件相关词汇：**
```
见本repo的data文件 [data](https://github.com/fighting41love/funNLP/tree/master/data)
```
**26\. 时间抽取：**
```
在2016年6月7日9:44执行測試，结果如下

Hi，all。下周一下午三点开会

>> 2016-06-13 15:00:00-false

周一开会

>> 2016-06-13 00:00:00-true

下下周一开会

>> 2016-06-20 00:00:00-true
```
[java version]( https://github.com/shinyke/Time-NLP)

[python version](https://github.com/zhanzecheng/Time_NLP)

**27\. 各种中文词向量：** [github repo](https://github.com/Embedding/Chinese-Word-Vectors)

中文词向量大全

**28\. 公司名字大全：** [github repo](https://github.com/wainshine/Company-Names-Corpus)

**29\. 古诗词库：** [github repo](https://github.com/panhaiqi/AncientPoetry) [更全的古诗词库](https://github.com/chinese-poetry/chinese-poetry)

**30\. THU整理的词库：** [link](http://thuocl.thunlp.org/sendMessage)

已整理到本repo的data文件夹中.
```
IT词库、财经词库、成语词库、地名词库、历史名人词库、诗词词库、医学词库、饮食词库、法律词库、汽车词库、动物词库
```
**31\. 中文聊天语料** [link](https://github.com/codemayq/chaotbot_corpus_Chinese)
```
该库搜集了包含:豆瓣多轮, PTT八卦语料, 青云语料, 电视剧对白语料, 贴吧论坛回帖语料,微博语料,小黄鸡语料
```
**32\. 中文谣言数据**[github](https://github.com/thunlp/Chinese_Rumor_Dataset)
```
该数据文件中，每一行为一条json格式的谣言数据，字段释义如下：

rumorCode: 该条谣言的唯一编码，可以通过该编码直接访问该谣言举报页面。
title: 该条谣言被举报的标题内容
informerName: 举报者微博名称
informerUrl: 举报者微博链接
rumormongerName: 发布谣言者的微博名称
rumormongerUr: 发布谣言者的微博链接
rumorText: 谣言内容
visitTimes: 该谣言被访问次数
result: 该谣言审查结果
publishTime: 该谣言被举报时间
```
[jieba](https://github.com/fxsjy/jieba)和[hanlp](https://github.com/hankcs/pyhanlp)就不必说了吧。

**33\. 情感波动分析：**[github](https://github.com/CasterWx/python-girlfriend-mood/)

词库已整理到本repo的data文件夹中.
```
本repo项目是一个通过与人对话获得其情感值波动图谱, 内用词库在data文件夹中.
```
