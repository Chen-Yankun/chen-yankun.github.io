---
layout: page
permalink: /notes/log2FC/index.html
title: log2FC和FDR
---
## log2FC的意义
<br>
&emsp; FC是fold change，表示两组样本表达值（均值）的比值。
&emsp; log2FC是对FC取以2为底的对数。
&emsp; 一般默认取log2FC绝对值大于1为差异基因的筛选标准。  
`|log2FC|>1`<br>

### FDR
&emsp; FDR即False Discovery Rate，错误发现率，是通过对差异显著性p值（p-value）进行校正得到的。由于转录组测序的差异表达分析是对大量的基因表达值进行独立的统计假设检验，会存在假阳性问题，因此在进行差异表达分析过程中，采用了公认的Benjamini-Hochberg校正方法对原有假设检验得到的显著性p值（p-value）进行校正，并最终采用FDR作为差异表达基因筛选的关键指标。一般取FDR<0.01或者0.05作为默认标准。
FDR=false discovery rate（伪发现率），计算方法：<br>
- 对*P*值排序，从小到大
- FDR=*P*×总数÷排序号


