# Baskets 推荐的论文

| model  | conference | link  |
| :----- | :---- |:---- |
|Beacon|IJCAI2019|[github地址](https://github.com/PreferredAI/beacon)|
|triple2vec|ICKM2018|[github地址](https://github.com/MengtingWan/grocery)|
|DREAM|SIGIR2016|[github地址](https://github.com/LaceyChen17/DREAM)|
|CFSH|AIRS2016|还未找到|
|FPMC|www2010|[github地址](https://github.com/khesui/FPMC)|


## 1、Correlation-Sensitive Next-Basket Recommendation (ICJAI 19)
[github地址](https://github.com/PreferredAI/beacon)

### 主要贡献：
假设篮子内的item之间有相关依赖性，再将一个sequence的basket用LSTM进行编码。既考虑了篮子内item的相关性，也有考虑篮子的连续性

协同矩阵 C 基于在可观察的训练basket的item联合出现的次数构建
### 论文模型：
![Beacon(IJCAI 19)](./image/Beacon(IJCAI19).png)
### 数据集：
1. [TaFeng](https://www.kaggle.com/chiranjivdas09/
ta-feng-grocery-dataset) 
    - TaFeng是一个杂货购物数据集，包含从2000年11月到2001年2月的交易。每笔交易都是一篮子购买的物品。每个序列是用户对篮子的时间顺序。
2. [Delicious](https://grouplens.org/datasets/hetrec-20)
    - Delicious由用户的书签序列组成。每个书签与一篮子标签分配相关联。
3. [Foursquare](http://www.ntu.edu.sg/home/gaocong/datacode.htm)
    - Foursquare从2010年8月到2011年7月有用户的年月日签到记录。我们将篮子定义为同一天内的一组check-in。

### 对比的baselines
* POP
* MC
* MCN
* [DREAM](https://github.com/LaceyChen17/DREAM)
* BSEQ
* [triple2vec](https://github.com/MengtingWan/grocery)

### 我的idea
在news recommendation的一篇文论中获取灵感--Neural News Recommendation with Attentive Multi-View Learning (IJCAI 19)，考虑将杂货铺的数据集中的 categories 以及 products description 的信息进行word embedding，再分别引入attention。
下面是这个论文的model
![NAML(IJCAI19)](./image/NAML(IJCAI19).png)
<br>

## 2、Representing and Recommending Shopping Baskets with Complementarity, Compatibility, and Loyalty (CIKM 18)

### 论文模型：
![triple2vec(CIKM18)](./image/triple2vec(CIKM18).png)

### 数据集：
1. [Dunnhumby](https://www.dunnhumby.com/sourcefles)
    - 这个数据集中包含了从大约2000个家庭收集的两年多的交易。用户是频繁的购物者，平均每周购物一次。
2. [Instacart](https://instacart.com/datasets/grocery-shopping-2017)
    - 这个数据集是由instacart.com发布的，这是一个在美国提供当日杂货递送的web服务。
它包含来自20多万用户的300多万份杂货订单。缺少每个订单的specifc日期，但是提供了每个用户的事务顺序

3. MSR-Grocery (WA) 
    - <font color="#ff0000">私有数据集，拿不到</font>.该数据集是从西雅图地区的一家便利店收集的。 我们扩展了该数据集，以包括来自约36万用户的12个月的交易。 由于该商店的类型，与其他数据集相比，用户倾向于较少的交易和较小的购物篮大小。

4. MSR-Grocery (UT)
    - <font color=red>私有数据集，拿不到。</font>font>我们从盐湖城地区的两家中型杂货店收集了8个月的交易记录。
这两家店来自同一家连锁超市，消费者相对多样化，包括家庭和大学生


## DREAM

### 模型贡献
我们的模型可以将用户当前的兴趣和全局顺序特性合并到用户的循环和动态表示中。

主要是加入了RNN，捕获篮子之间的时序信息。也采用了BPR的思想，负采样。

### MODEL
[model的github地址](https://github.com/LaceyChen17/DREAM)

![DREAM(SIGIR2016)](./image/DREAM(SIGIR2016).png)

### baselines
* TOP
* [NMF](http://cogsys.imm.dtu.dk/toolbox/nm)
* MC
* FPMC
* HRM

### 数据集
1. [Ta-Feng](http://recsyswiki.com/wiki/Grocery shopping datasets)
   
    - Ta-Feng数据集包含了从杂货店购买的许多购物篮，其中每个购物篮封装了一个用户在一段时间内购买的商品。该数据集是一个公共数据集，包含32,266个用户的817,741个事务和23,812个条目。
2. [T-mall](http://102.alibaba.com/competition/addDiscovery/index.htm)
    - T-mall 数据集是一个公共发布的在线电子商务数据集 Alibaba group, 包含 884 个 用户、9531 品牌、 4298 笔交易。

    这两个数据集之间的细微差别是，T-mall数据集记录了基于品牌的交易，每个品牌可能包含一系列项目。

<br/>
## Factorizing Sequential and Historical Purchase Data for Basket Recommendation (AIRS2016)
### 模型贡献
将item-centric 和 user-centric 的方法融合在一起。

* 通过挖掘和因子化全局序列模式，我们可以避免传统以item为中心的方法的稀疏性问题。
* 通过因子化 item-item、user-item 矩阵，我们可以同时利用序列和历史行为来学习user 和 item的表示

### MODEL
![item-item](./image/CFSH_1(AIRS2016).png)

![item-item](./image/CFSH_2(AIRS2016).png)

### 数据集
1. [Ta-Feng](http://recsyswiki.com/wiki/Grocery_shopping_datasets)
2. [BeiRen](http://www.brjt.cn)
3. [T-Mall](http://102.alibaba.com/competition/addDiscovery/index.htm) 链接已丢失

### baselines
* TOP
* MC
* FMC
* [NMF](http://cogsys.imm.dtu.dk/toolbox/nmf/.)

### 评估指标
* F1-score@top5

* Hit-Ratio@top5

* Precision@top5

* Recall@top5


##  Factorizing Personalized Markov Chains for Next-Basket Recommendation (www2010)

> [github地址](https://github.com/khesui/FPMC)



