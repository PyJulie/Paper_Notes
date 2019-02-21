## 摘要
* 置信度校准 - 预测代表真实正确性的概率值估计问题，作者提出了temperature scaling，一种plat scaling的single parameter方法，可以有效地作用于calibrating predictions

## 介绍
* 分类网络不仅必须准确，而且还需要指出何时不准确。 
* 在汽车驾驶中，如果检测网络无法自信地预测障碍物，应该交由其他传感器的输出来判断。
* 在医疗中，如果机器没有信息去判断是否患病，则应该交由人类医生来决断。
* 另外就是可解释性很重要，良好的置信度估计可以提供额外的信息，也可以应用于其他的概率模型中。
* 一个例子
* ![图](https://pic1.zhimg.com/80/v2-7c5ad85edd33da85fe1913a7f4ea7c18_hd.jpg)
* 上图中是两个不同网络的输出。
* X轴表示置信度（Confidence）区间, Y轴表示在某个预测置信度区间的数量占总测试集的百分比。
* 这篇论文的idea是对于一定数量的测试集，模型越可靠，平均置信度（Average Confidence）越接近准确率（Accuracy）。
* 从上图中可以发现，虽然Lenet 准确率比Resent低，但Lenet 模型输出置信度更能够代表真实的概率估计。

### 定义
* acc(Bm) = 1/|Bm| * ∑ 1(yi' = yi)
* conf(Bm) = 1/|Bm| * ∑ pi'
* 完美模型就是 acc = conf
* ![ECE](images/on_cali/ece.png)
* ![MCE](images/on_cali/mce.png)
