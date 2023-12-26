---
layout: page
permalink: /notes/biovolcano/index.html
title: 生信火山图（转载）
---

## 火山图注释
**火山图，是形如火山喷发的一种图形展示方法，常被用于展示差异，比如差异基因、差异微生物等等。**  
&emsp; 火山图描述了差异基因的情况。该火山图的y轴是-log10(Qvalue)，即qvalue（pvalue校正后的值）取-log10，因此数值越高说明qvalue越小即越显著。横坐标是Log2 fold change，即对fold change取log2，所以越靠两侧的点（每个点代表一个基因），其基因表达量上调或者下调幅度越大。  
**一般来说在差异基因分析过程中，我们通常认为qvalue小于0.05且foldchange的绝对值大于2为差异基因。** 当然在差异基因数量过多的时候，我们可以调整筛选标准以获得相对适合数量的差异基因再进行下游的富集分析，比如要求qvalue小于0.001，或者要求foldchange的绝对值大于5等等。当差异基因数量过少的时候，我们可以考虑将foldchange的绝对值变为1.5，或者考虑选择pvalue小于0.05。  
**而图中的虚线就是根据自己的筛选标准确定添加。** 其中两条竖线（x=-2和x=2）说明该筛选标准是要求foldchange的绝对值大于4。横线（大胆猜测是在y=2处），说明要求qvalue小于0.01。  
当Foldchange没有那么明显的时候，我们的横轴也可以选择展示Foldchange，不取log2。
```
作者：jlyq617  
链接：https://www.jianshu.com/p/e2828ef9c7e5  
来源：简书  
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```
1. 使用文件夹中volcano2.R
2. 准备好数据文件，计算*P*adj
3. FDR=false discovery rate（伪发现率）
+ 对*P*值排序，从小到大
+ FDR=*P*×总数÷排序号
+

第一列是基因名，第二列是计算好的log2FoldChange（通常我们用DESeq等软件分析得到的结果里包含这一个值），第三列是pvalue，第四列是校正后的p即padj。  
如果你已经确定要画pvalue或者padj那只要三列即可。

**（2）如何使用ggpot2做火山图**  
能够做火山图的方法有很多，有一些RNA-seq分析的包中自带了画火山图的函数。利用R自带的基础画图函数也可以画，但是鉴于之后我们都几乎都选择ggplot2包进行作图，所以只展示如何用ggplot2包画图。
```xml
#加载包
library(ggplot2)
#读取数据
Dat<-read.table('./results.txt',header = T,stringsAsFactors = F,check.names = F,sep=' ')
#作图
ggplot(Dat,aes(x=log2FoldChange,y=-log10(padj)))+
  geom_point()

```
通过简单的几行代码我们就能够得到一个最基本（简陋）的火山图。
然后我们来美化这张火山图。

```php
#加载包
library(ggplot2)
library(ggrepel)
#读取数据
Dat<-read.table('./results.txt',header = T,stringsAsFactors = F,check.names = F,sep=' ')
#确定是上调还是下调，用于给图中点上色）
Dat$threshold = factor(ifelse(Dat$padj < 0.05 & abs(Dat$log2FoldChange) >= 1, ifelse(Dat$log2FoldChange>= 1 ,'Up','Down'),'NoSignifi'),levels=c('Up','Down','NoSignifi'))


ggplot(Dat,aes(x=log2FoldChange,y=-log10(padj),color=threshold))+
  geom_point()+
  scale_color_manual(values=c("#DC143C","#00008B","#808080"))+#确定点的颜色
  geom_text_repel(
    data = Dat[Dat$padj<0.05&abs(Dat$log2FoldChange)>1,],
    aes(label = Gene),
    size = 3,
    segment.color = "black", show.legend = FALSE )+#添加关注的点的基因名
  theme_bw()+#修改图片背景
  theme(
    legend.title = element_blank()#不显示图例标题
  )+
  ylab('-log10 (p-adj)')+#修改y轴名称
  xlab('log2 (FoldChange)')+#修改x轴名称
  geom_vline(xintercept=c(-1,1),lty=3,col="black",lwd=0.5) +#添加横线|FoldChange|>2
  geom_hline(yintercept = -log10(0.05),lty=3,col="black",lwd=0.5)#添加竖线padj<0.05

```


**一张精致的火山图就做好啦。**

其中说明一下lty是用于描述添加线的类型，数字对应不同的类型，具体的可以参考下图：
<p align="center">
<img src= "/notes/火山图.png" width="80%">
</p><br>
