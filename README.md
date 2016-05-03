# 	Python数据可视化模块—[Seaborn](http://web.stanford.edu/~mwaskom/software/seaborn/index.html)
`声明：本文主要内容翻译自Seaborn官方文档，可以作为Seaborn数据可视化入门`  

## 1. 为什么介绍Seaborn库？
**Matplotlib**是Python主要的绘图库。但是，不建议直接使用它。虽然Matplotlib很强大，但它因此也很复杂，你的图经过大量的调整才能变得精致。因此，作为替代，推荐一开始使用Seaborn。Seaborn本质上使用Matplotlib作为核心库（就像Pandas对NumPy一样）。seaborn有以下几个优点：
  
* 默认情况下就能创建赏心悦目的图表。  
* 创建具有统计意义的图。  
* 能理解pandas的DataFrame类型，所以它们一起可以很好地工作。

虽然anaconda预装了pandas，却没安装seaborn。可以通过 conda install seaborn轻松地安装。当然，如果在终端中使用， 可以直接pip install seaborn，如果提示有什么错误，可以按照其说明，即可轻松安装上。

## 2. Seaborn使用

### 2.1. 管理图表的艺术

* Matplotlib VS Seaborn  

	画一个吸引人注意的图表相当重要。当你探索一个数据集，需要画图表，图表看起来令人愉悦是件很高兴的事。在与你的观众交流观点时，可视化同样重要，同时，也很有必要去让图表吸引注意力和印入脑海里。Matplotlib自动化程度非常高，但是，掌握如何设置系统以便获得一个吸引人的图是相当困难的事。为了控制matplotlib图表的外观，Seaborn模块自带许多定制的主题和高级的接口。  
	
	- 导入模块  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/1.jpg)
	- 定义一个函数用来可视化弦函数，这将帮助我们了解我们可以控制的不同风格的参数  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/2.png)
	- 默认情况下matplotlib的画的图是这样的：  	
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/3.png)
	- 转换成Seaborn模块，只需要引入seaborn模块。  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/4.png)
		- Seaborn默认浅灰色背景与白色网络线的灵感来源于MATLAB，却比MATBLAB的颜色更多柔和。我们发现，网格线对于传播信息很有用，几乎在所有情况下，人们喜欢图甚于表。默认情况下白灰网格的形式可以避免过于刺眼。在多面作图的情况下，网络形式显得相当的有利，提供了一种作图结构，这对模块中的一些复杂工具非常重要。  
		- seaborn将matplotlib的参数划分为两个组。第一组控制图表的样式，第二组控制图的度量尺度元素，这样就可以轻易在纳入到不同的上下文中。  
		- 操控这些参数由两个函数提供接口。控制样式，用axes_style()和set_style()这两个函数。度量图则用plotting_context()和set_context()这两个函数。在这两种情况下，第一组函数返回一系列的参数，第二组则设置matplotlib的默认属性。

* **图样式方法axes_style()和set_style()**  

	有5种seaborn主题形式：darkgrid, whitegrid, dark, white, ticks，默认为darkgrid。 每个人可以根据应用和自己的喜好来选择。有关于白灰色网格的作用，上面已经介绍，这里就不再重复介绍。下面，依次展示一下几个主题显示效果。
	- whitegrid－－白色网格
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/5.png)
	- dark－－灰底  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/6.png)
	- white －－白底  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/7.png)
	- ticks－－刻度  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/8.png)
* **用despine()方法去掉图表中的各种轴**  
可以看到，在白底和带刻度的两幅图表中，顶部的轴式不需要的，这时候就需要我们将其去掉。如果使用matplotlib进行去除，这是非常困难的，但是，Seaborn很轻松就可以实现。
	- 去掉顶部  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/9.png)
	- 去掉y轴  
	为了更好的显示去掉y轴带来的优越图表效果，这里通过使用另一个图表来详细介绍一下。  
		- 生成图表    
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/10.png)  
		- 去掉y轴后效果更佳  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/11.png)
	
* **With语句临时设置图表样式**

	- 先用一张图介绍一下matplotlib.pylab的subplot()函数：  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/12.png)  
	- 在with语句中使用axes_style函数能够暂时设置图参数，这也可以使数据不同样式的轴。  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/13.png)

	
### 2.2. 简单介绍一下Seaborn中的颜色设置  
对于一个图表来说，颜色在其中占有重要的地位。在matplotlib中也有介绍颜色在可视化中的使用。但是，seaborn非常便于选择和使用调色板，适合将数据进行可视化。  

* 导入相应模块  
![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/21.png)  

* 无渐变调色板  

	-  默认分类调色板  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/22.png)  
	-  调色板颜色循环  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/23.png)  
	* 亮度、饱和度  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/24.png)   
	*  更人性化的HUSL  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/25.png)

* 渐变调色板

	- 浅色渐变深色  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/26.png)  
	- 深色渐变浅色  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/27.png)

* 用set_palette()方法改变默认调色板  
可以看出，色彩绚丽了很多  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/28.png)
	
### 2.3. 可视化绘图

#### 可视化数据集分布
在处理一组数据时，通常我们首先要做的就是考虑这组数据的分布有什么意义。这一部分，给大家简单介绍一下Seaborn中检查一元和二元分布。

	在seaborn中最便捷的方式构造一个单变量分布是是用distplot()方法，默认情况下，它会绘出矩形图(histogram)或者核密度估计(KDE)
	
* 导入相应模块  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/311.png)  
	
* 使用numpy.random.normal随机抽样生成正态分布数据  
![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/312.png)  

* 单变量分布图
	- 矩形图---直方图  
	矩形图，大家都很熟悉，在matplotlib中已经使用过。
		![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/313.png)  
	在绘制直方图时，我们可以规定其数量和位置，displot()方法使用了一种简单的规则对数据进行猜测，控制矩形方块的数量，以更好的解释数据的意义。
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/314.png)
		
	- 核密度估计（KDE）
	[核密度估计](http://baike.baidu.com/view/3380594.htm)用于绘制形状的分布  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/315.png)
		
* 绘制二维分布  
绘制二位变量分布是非常有用的，seaborn可以用jointplot()方法非常容易的绘制出联合变量、单变量的图。强大的多图显示，请往下看。
	- 生成多维正态分布数据
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/316.png)
	- 散点图  
	二位分布最常见的是散点图，可以使用Matplotlib的plt.scatter()方法来绘制，而Seaborn中是使用jointplot()方法。
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/317.png)

	- 六边形图  
	直方图的二位模拟称为六边形图，这个图对相对大的数据集非常有效，matplotlib的plt.hexbin()方法和jointplot()类似。在seaborn中使用了非常棒的白色背景：  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/318.png)
	- 核密度估计  
	在seaborn中，核密度估计中使用轮廓图来可视化二维分布：
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/319.png)
	
#### 可视化的线性关系
许多数据集包含多个变量，分析的目标往往是这些变量之间的关系。上面介绍了变量联合分布的可视化，非常直观。但是，在包涵嘈杂数据值时，我们如何观测数据之间的简单关系呢？这一部分介绍线性回归。
Seaborn中回归图主要是引导增强可视化，有助于数据分析中发现数据间关系。所以，seaborn并不是一个数据分析包（如果想了解数据线性回归拟合，可以了解[statsmodels](http://statsmodels.sourceforge.net)模块。Seaborn的目标时是通过更快速、更容易的可视化来探索数据关系。

* 导入各模块  
![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/321.png)

* 导入Seaborn自带数据  
![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/322.png)

* 绘制线性回归模型函数  
在Seaborn中，有两个方法通过回归用于可视化线性关系，regplot() and lmplot() ，这两个方法非常相似，所以需要根据特点的数据分析工作来选择正确的方法。

	* 不同种类的模型  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/323.png)  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/324.png)  
	可以看出，两个图除了图表形状、大小外，其它没有什么特别明显的差别。之后会说明一下为什么下面的图变小了。这里先说一下输入参数的主要区别。regplot()方法接受的x和y变量的格式包括简单的numpy arrays, pandas Series objects or pandas DataFrame object。相反，implot()方法必须有参数设置，并且x和y必须是字符串。
	- 当有其中一个变量是离散值时，可以对其进行线性回归拟合。但是，通过这种数据集生成的简单散点图往往不是最优的：  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/325.png)  
	- 一种选择是通过往离散数据中添加一些随即噪声（“抖动－jitter”），使得这些值得分布更加清晰。注意，jitter只适用于散点图的数据并且不影响回归线拟合本身。  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/326.png)  
	- 另一种选择是在置信区间内对中心趋势估计：  
	![](https://raw.githubusercontent.com/baibaibai66/Seaborn/pictures/327.png)


 Seaborn模块的使用就简单介绍这些，如果有兴趣，还可以到官方网站自行查阅。`
