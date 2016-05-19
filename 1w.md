#数据科学导论笔记

##数据科学介绍 1/5

“Data Science is the art of turning `data` into `acitons`.”-《The Field Guide to Data Science》
+ Hacking Skills
+ Math &Statistics Knownlege
+ Substantive Expertise

##数据闭环 2/5
+ 不间断的收集数据  `＃数据如何采集和存储？`
+ 基于数据获得洞察
+ 基于发现做出决策
+ 跟踪效果迭代优化

##数据产生价值的方式 3/5
+ 直接使用数据
+ 数据建模和数据报告（解释历史 预测&控制未来）
+ 数据产品（把模型嵌入产品中，让产品更自动化和高效，例如猜你喜欢电台）
`#对未来数据科学家的要求数据库中做etl ，数据库写脚本，会处理图片／文本多种类型数据，懂计算机，懂商业(基本就是全能嘛)`

##数据科学家技能树 4/5
+ 理论
+ 工具
+ 实践
+ 探索前沿

##统计思维的陷阱 5/5
+ 批判性思维

本节参考数据 [`传送门下载`]( http://pan.baidu.com/s/1clyd46)
- 《深入浅出数据分析》
- 《统计学的世界》
- 《利用python进行数据分析》
- 《数据科学实战》
- Numerical Python
- Think Stats
- Python for scientists
- [Scipy Lecture Notes](http://scipy-lectures.org)

---
- 《赤裸裸的统计学》
- 《统计学的世界》
- 《女士品茶》
- 《数据科学实战第1章》

##练习题
＋图解中国人到生活水平
中国人到生活水平，是一个抽象到概念，需要对概念对操作化，变成可操作可衡量对具体指标，这里借用恩格尔系数作为衡量指标。
![](https://raw.githubusercontent.com/panfeng3141/pic/master/恩格尔系数.png)
数据来源：[国家统计局－城乡居民恩格尔系数](http://data.stats.gov.cn/easyquery.htm?cn=C01)
  

＋理解[双盲实验](https://en.wikipedia.org/wiki/Blind_experiment#Double-blind_trials)
 心理学经典实验方式之一，主要了是为了避免主试和被试对试验结果的误差。
 之前做过用户关于音效的测试，采用了这个试验，主要是在测试人员和被测都不知道的情况下，去观察用户对音频效果是否高品质的喜好。

+学习使用Google Ngram Viewer
![](https://raw.githubusercontent.com/panfeng3141/pic/master/goole.png)
  
+[Simpson's Paradox](https://en.wikipedia.org/wiki/Simpson%27s_paradox)
以［男女性别比例］（http://www.guokr.com/article/6222/）为例

＋[贝叶斯定理](https://zh.wikipedia.org/wiki/贝叶斯定理)

 P(A)发病概率,P(A)=0.001
 
 P(a)不发病概率,P(a)=1-P(A)=0.999
 
 P(+|A)发病被检查出对概率＝0.99
 
 P(+|a)不发病概被检出有病对概率＝0.05
 
 P(+)不考虑其他因素，被查处阳性概率
 
 P(+)＝P(+|A)*P(A)+ P(+|a)*P(a)=0.05094
 
 所以，P(+|A)＝P(+|A)＊P(A)／P(+)＝0.0194




