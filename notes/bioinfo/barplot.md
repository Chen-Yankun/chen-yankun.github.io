---
layout: page
permalink: /notes/bioinfo/barplot/index.html
title: 差异基因柱状图绘制
---

```
#install.packages("forcats")
#install.packages("cluster")
#install.packages("ggplot2")

library(ggplot2)


mydata <- read.csv("data2.csv",header = T,row.names = 1)


mydata$T <- mydata$log2FC > 0 # 增加一个新变量
head(mydata, 10) # 查看数据前十行

P1<-ggplot(mydata, aes(x = reorder(Name, log2FC), y = log2FC, fill = T)) +
  geom_bar(stat = "identity", position = "identity", width = 0.8) +
  scale_fill_manual(values = c("steelblue2", "firebrick1"), guide = "none") +
  

  #annotate("segment", x = 0, y = 0, xend = 40, yend = 0, size = 0.3) + # “0”位置上的直线
  coord_flip(ylim = c(-6.9, 7), expand = 0, clip = "off") + # 颠倒x与y轴,在这里设置x轴量程
  theme_classic() + # 主题
  theme(
    axis.line = element_line(size = 0.2),      # 修饰坐标轴
    axis.ticks = element_line(size = 0.3),
    axis.text.y = element_text(face = "italic", colour = "black"),
    axis.text.x = element_text(colour = "black"),
    plot.margin = unit(c(1, 1, 1, 1), "cm")) + # 修饰图片四周空白
  labs(x = "",      # 修饰x与y上的标签
       y = "log2(FC)")

ggsave("results.pdf",plot=P1,height=20,width=10)
```