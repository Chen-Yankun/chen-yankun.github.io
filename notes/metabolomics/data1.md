---
layout: page
permalink: /notes/metabolomics/data1/index.html
title: 代谢组学的原始数据
---
## 代谢组学的原始数据
---

### 刚拿到代谢组的数据
刚拿到代谢组的数据一头雾水，打开excel一看是密密麻麻的数据，不知从何入手。<br>
这个笔记是用来记录分析代谢组数据的步骤。<br>


### 最后要呈现的数据
<p align="center">
<img src= "/notes/metabolomics/代谢组数据表头.png" width="90%">
</p><br>

### ORA富集分析和
使用<a href="https://www.metaboanalyst.ca/MetaboAnalyst/ModuleView.xhtml" target="_blank">MetaboAnalyst 6.0网页版</a>基于SMPDB数据库进行ORA富集分析和通路分析，将VIP大于1的代谢化合物HMDB编号输入网站数据框，执行过度表示分析（Over Representation Analysis, ORA）。ORA是使用超几何测试来评估特定代谢物组在给定化合物列表中的表现是否超出预期。在对多次测试进行调整后，提供单尾P值。将代谢物映射到生物通路，了解代谢通路的变化情况。