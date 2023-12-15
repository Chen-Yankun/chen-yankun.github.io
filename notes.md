---
layout: page
permalink: /notes/index.html
title: Notes
---

<h2 id="dingbu">Paper Notes</h2>

- 个人网站要添加什么东西
    - 个人对外的资料
    - 画作，表情包，形成系统
    - 记录生活
        - 旅行
        - 拍照
        - 和婷婷一起
    - 学术内容

---
### markdown网页的一些实用语法：

回车：&lt;br&gt;  

<span style="font-family: 'Arial'; font-size: 18px; color: #3498db;">自定义字体样式αβγδ</span>  
```<span style="font-family: 'Arial'; font-size: 18px; color: #3498db;">自定义字体样式αβγδ</span>```
<br>
<span style="font-family: 'Times New Roman'; font-size: 18px; color: #3778db;">自定义字体样式αβγδ</span>  
```<span style="font-family: 'Times New Roman'; font-size: 18px; color: #3778db;">自定义字体样式αβγδ</span>```
<br>
<span style="font-family: '宋体'; font-size: 18px; color: #3778db;">自定义字体样式αβγδ</span>  
```<span style="font-family: '宋体'; font-size: 18px; color: #3778db;">自定义字体样式αβγδ</span>```
<br>

#### 外置网页的超链接：
```[这里写要点击的内容](https://这里放网址.点击内容就跳转到网址/)```
<br>
点击网站后弹出新窗口：
```<a href="https://这里放网址.点击内容就跳转到新窗口网址/" target="_blank">这里写要点击的内容</a>```

<br>

#### 页内跳转：

首先设置
```<p id="jump">跳转到的地方</p>```
再设置
```[点击跳转](#jump)```<br>
点击上面的“点击跳转”，就会跳转到“跳转到的地方”了。<br>

#### 图片
在Jekyll中，你可以使用Markdown语法结合HTML标签来控制照片的排列和大小。以下是一些示例：
##### 控制照片排列
###### 水平排列
```markdown ![Image 1](/path/to/image1.jpg) ![Image 2](/path/to/image2.jpg)```
这将在网页上水平排列两张图片。

###### 垂直排列
```markdown
![Image 1](/path/to/image1.jpg)
![Image 2](/path/to/image2.jpg)
```
这将在网页上垂直排列两张图片。

##### 控制照片大小

###### 使用HTML的`<img>`标签

```markdown
<img src="/path/to/image.jpg" alt="Image" width="300" height="200">
```

上述示例将显示一张宽度为300像素、高度为200像素的图片。你可以根据需要调整 `width` 和 `height` 的值。

##### 图片居中显示

```markdown
<p align="center">
  <img src="/path/to/image.jpg" alt="Image" width="300" height="200">
</p>
```

这将使图片在网页上水平居中显示。

##### 图片靠左显示

```markdown
<img src="/path/to/image.jpg" alt="Image" style="float: left; margin-right: 10px;">
```

这将使图片靠左显示，并在图片右侧留有一定的空白（10像素），使文字不会紧贴在图片边缘。

##### 图片靠右显示

```markdown
<img src="/path/to/image.jpg" alt="Image" style="float: right; margin-left: 10px;">
```

这将使图片靠右显示，并在图片左侧留有一定的空白，避免文字与图片重叠。

##### 图片浮动于文字之上

```markdown
<div style="position: relative;">
  <img src="/path/to/image.jpg" alt="Image" style="position: absolute; top: 0; left: 0;">
  <p>这是一些文字。</p>
</div>
```

这将使图片浮动于文字之上。通过设置`position: relative;`和`position: absolute;`，可以实现图片相对于其包含块的绝对定位。通过调整`top`和`left`属性，可以控制图片的位置。

请注意，上述示例中的路径 `"/path/to/image.jpg"` 应该替换为你实际图片的路径。在实际应用中，你可以根据需要调整样式和数值。


<br>
<div class="third">
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
</div>

<br>

<div class="fifth">
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
</div>

<br>
<div class="third">
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
</div>

<br><br>
<div class="second">
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
<div><img src="/images/profile.jpg"></div>
</div>

<br>
[回到顶部](#dingbu)