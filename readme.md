# 猫眼Top100电影爬取

>如果遇到[Github](maoyan.ipynb)无法打开，请查看[完整 Jupyter Notebook](https://nbviewer.jupyter.org/github/hufe09/maoyan_top100/blob/master/maoyan.ipynb)

- [爬虫](猫眼Top100爬虫.ipynb)
  
  - 爬取猫眼电影Top100榜单的电影数据
  
- [PyMysql封装为DB类](mysql_db.ipynb)
  
  - 为了避免频繁操作建立，关闭pymsql连接和游标，将pymysql基础操作封装了一个DB类
- [数据存入MySql](存入MySQL.ipynb)
  - [Python 操作 SQL的几种方式](<https://hufe09.github.io/2019/04/02/Python-&-SQL/>)
- [数据存入MongoDB](存入MongoDB.ipynb)
  - [MongoDB基础使用](<https://hufe09.github.io/2019/06/01/MongoDB/>)
- [一些好玩的功能](一些好玩的功能.ipynb)
  - 将所有电影的海报组合为一张5*20的[组合海报](https://raw.githubusercontent.com/hufe09/maoyan_top100/master/images/mixed_posters.png)
  
  - 用matplotlib和pyecharts分别绘制电影名的词云
  
  - 统计演员参演的电影数
  
  - 用Apriori算法探索演员之间的关系
  

![word cloud](https://raw.githubusercontent.com/hufe09/maoyan_top100/master/images/word_cloud_echarts.png)

**出现频率较高的明星**


```
{1: [(('张国荣',), 7),
  (('周星驰',), 4),
  (('梁朝伟',), 4),
  (('丽芙·泰勒',), 3),
  (('伊恩·麦克莱恩',), 3),
  (('伊莱贾·伍德',), 3),
  (('克里斯蒂安·贝尔',), 3),
  (('巩俐',), 3),
  (('布拉德·皮特',), 3),
  (('张曼玉',), 3),
  (('莫文蔚',), 3),
  (('阿尔·帕西诺',), 3),
  (('丹尼尔·雷德克里夫',), 2),
  (('克林特·伊斯特伍德',), 2),
  (('凯瑞-安·莫斯',), 2),
  (('刘德华',), 2),
  ...
  2: [(('丽芙·泰勒', '伊恩·麦克莱恩'), 3),
  (('丽芙·泰勒', '伊莱贾·伍德'), 3),
  (('伊恩·麦克莱恩', '伊莱贾·伍德'), 3),
  (('周星驰', '莫文蔚'), 3),
  (('张国荣', '梁朝伟'), 3),
  ...
3: [(('丽芙·泰勒', '伊恩·麦克莱恩', '伊莱贾·伍德'), 3),
  (('丹尼尔·雷德克里夫', '艾玛·沃特森', '鲁伯特·格林特'), 2)]}
```



**频率较高的演员组合**


```
[{艾玛·沃特森} -> {丹尼尔·雷德克里夫},
 {丹尼尔·雷德克里夫} -> {艾玛·沃特森},
 {鲁伯特·格林特} -> {丹尼尔·雷德克里夫},
 {丹尼尔·雷德克里夫} -> {鲁伯特·格林特},
 {伊恩·麦克莱恩} -> {丽芙·泰勒},
 {丽芙·泰勒} -> {伊恩·麦克莱恩},
 {伊莱贾·伍德} -> {丽芙·泰勒},
 {丽芙·泰勒} -> {伊莱贾·伍德},
 {伊莱贾·伍德} -> {伊恩·麦克莱恩},
 {伊恩·麦克莱恩} -> {伊莱贾·伍德},
 {迈克尔·凯恩} -> {克里斯蒂安·贝尔},
 {基努·里维斯} -> {凯瑞-安·莫斯},
 {凯瑞-安·莫斯} -> {基努·里维斯},
 {莫文蔚} -> {周星驰},
 ...
 {艾玛·沃特森, 鲁伯特·格林特} -> {丹尼尔·雷德克里夫},
 {丹尼尔·雷德克里夫, 鲁伯特·格林特} -> {艾玛·沃特森},
 ...
 
```

通过取前面自己的统计，以及apriori算法统计，能看出来，猫眼 Top100电影中，国内明星 张国荣，周星驰，梁朝伟，莫文蔚，张曼玉，巩俐等知名明星霸榜，国外明星 丽芙·泰勒，伊恩·麦克莱恩，伊莱贾·伍德，克里斯蒂安·贝尔，布拉德·皮特，阿尔·帕西诺 霸榜。

并且，有周星驰的电影基本会有莫文蔚，丽芙·泰勒，伊恩·麦克莱恩，伊莱贾·伍德三人同台的次数也非常多，张国荣，梁朝伟搭戏也必较多。


![image](https://raw.githubusercontent.com/hufe09/GitNote-Images/master/Picee/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20190807082827.4tl86waj5ko.png)  

![image](https://raw.githubusercontent.com/hufe09/GitNote-Images/master/Picee/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20190807082840.8qeggx7ywgc.png)

# Django 页面

![image](https://raw.githubusercontent.com/hufe09/GitNote-Images/master/Picee/image.lqoou3qwb1e.png)

![image](https://raw.githubusercontent.com/hufe09/GitNote-Images/master/Picee/image.9y5zw4iti5e.png)

## 一些想法

本次爬虫这些功能都是自己想到什么就做什么，就是一个逐渐把想法变为代码的转换过程，比起条条框框的规则来说，更享受我行我素的感觉。但是，真真要想做出有质量的东西，一定要严格遵循其规则。

本项目有 `.ipynb` 和 `.py` 格式，用 Jupyter Notebook 写完，最后把每一个模块整理成 `.py`文件。

我个人很喜欢 Jupyter Notebook 这款工具，非常实用，Markdown & Code，在浏览器一次性就搞定，简直不要太方便。

