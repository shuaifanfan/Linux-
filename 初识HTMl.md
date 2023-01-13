[toc]

## https://www.kuangstudy.com/bbs/1497183162231918593#header17

## 初识HTMl

**<font color=&quot;red&quot;>;HTML---全名是 Hyper Text Markup Language---（超文本标记语言）</font>;**

**<font color=&quot;blue&quot;>;超文本包括：文字、图片、音频、视频、动画等。</font>;**

HTML5的优势：

- 世界知名浏览器厂商对HTML5的支持
  - 微软
  - Google
  - 苹果
  - Opera
  - Mozilla
- 市场的需求
- 跨平台

**<font  size=5 color=&quot;red&quot;>;W3C标准：</font>;**

- W3C
  - World Wide Web Consortium(万维网联盟)
  - **<font color=&quot;blue&quot;>;成立与1994年，Web技术邻域最权威和具有影响力的国际中立性技术标准机构</font>;**
  - [W3C国际网](http://www.w3.org)
  - [W3C中国区域网](http://www.chinaw3c.org)
  - **<font color=&quot;red&quot;>;URL地址中以org结尾就表示开源的意思</font>;**
- <font size=5 color=&quot;blue&quot;>;W3C标准包括</font>;
  - **<font color=&quot;red&quot;>;结构化标准语言（HTML、XML）</font>;**
  - **<font color=&quot;red&quot;>;表现标准语言（CSS）</font>;**
  - **<font color=&quot;red&quot;>;行为标准（DOM、ECMAScript），DOM是文档对象模型！</font>;**

**<font color=&quot;blue&quot;>;创建第一个HTML文件：</font>;**

- **<font color=&quot;red&quot;>;首先在IDE工具中先建一个项目，可以就直接选择第一个的java项目，然后命名好后，打开其项目结构，其中默认生成的src包可以删去用不到它，在项目下自己创建一个html目录即可！</font>;**

效果图：

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudyac36b84a-976a-46ba-a81b-4b7af19bec15.png)

<body>; 、</body>; 等成对的标签，分别叫**<font color=&quot;red&quot;>;开发标签</font>;**和**<font color=&quot;red&quot;>;闭合标签</font>;**

单独呈现的标签（空元素），如<hr/>;;意为用 / 来关闭空元素，单个出现的标签称为**<font color=&quot;red&quot;>;自闭和标签</font>;**

点击右上角的响应浏览器查看效果：

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudyc92ec856-7f92-472d-9cea-9b03e5b4db27.png)

## 网页基本信息

eg:

<!--HTML中的注释结构，在IDE中注释的快捷生成键是 CTRL + / -->

<!DOCTYPE html><!--DOCTYPE:文档类型，其作用就是: 告诉浏览器，我们要使用什么规范！浏览器默认的就是html规范！-->
<!--html中的所有代码必须都在<html></html>标签里面，在该标签外面写的东西不会被显示，只会被当成一段文本！-->
<html lang="en">
<!--head标签代表网页头部！
<head> 标签用于定义文档的头部，它是所有头部元素的容器。<head> 中的元素可以引用脚本、指示浏览器在哪里找到样式表、提供元信息等等。
文档的头部描述了文档的各种属性和信息，包括文档的标题、在 Web 中的位置以及和其他文档的关系等。绝大多数文档头部包含的数据都不会真正作为内容显示给读者。
下面这些标签可用在 head 部分：<base>, <link>, <meta>, <script>, <style>, 以及 <title>。
<title> 定义文档的标题，它是 head 部分中唯一必需的元素。
-->
<head>
<!--meta描述性标签，它用来描述我们网站的一些信息，一般用来做SEO（搜索引擎优化）。charset="UTF-8"表示字符编码是UTF-8格式！-->
    <meta charset="UTF-8">
<!--title网页标题！-->
    <title>IDE生成的第一个HTMl文件</title>
</head>
<!--body标签代表网页主体！-->
<body>
夏黄杰，你好！
</body>
</html>

## 网页基本标签

- 标题标签
- 段落标签
- 换行标签
- 水平线标签
- 字体样式标签
- 注释和特殊符号

eg:

**<font color=&quot;red&quot;>;在写代码学习的过程中，如果碰到代码被默认加上白色横线的话，既代表该方法或者标签等被废弃或者淘汰了。虽然不影响使用，仍然会有效果，但是最好不要继续使用而是使用更好的方法来实现！注意：以后在企业开发中，不到万不得已一定不要使用这些被废弃掉的标签啊，如果一定要使用，一般情况下都是用来作为CSS的钩子来使用。</font>;**

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>网页基本标签学习</title>
</head>
<body>
<!--使用style属性设置文本居中-->
<h1 style = "text-align:center"> 网页基本标签学习</h1>
<!--标题标签-->
<h1>一级标签</h1>
<h2>二级标签</h2>
<h3>三级标签</h3>
<h4>四级标签</h4>
<h5>五级标签</h5>
<h6>六级标签</h6>
<!--段落标签,其快捷键是：写一个p 然后按一下tab便一键生成了，其他标签也可以类似这样快捷键生成！-->
<p>斯蒂芬·库里（Stephen Curry），全名沃德尔·斯蒂芬·库里二世（Wardell Stephen Curry II），1988年3月14日出生于美国俄亥俄州阿克伦（Akron, Ohio），美国职业篮球运动员，司职控球后卫，绰号“娃娃脸刺客（Baby-Faced Assassin）”，效力于NBA金州勇士队。 [1]  [332]</p>
<p>斯蒂芬·库里于2009年通过选秀进入NBA后一直效力于金州勇士队，新秀赛季入选最佳新秀第一阵容；2014-15、2016-17、2017-18赛季三次夺得NBA总冠军；两次荣膺常规赛MVP；2015-16、2020-21赛季两次当选NBA常规赛得分王； [308]  7次入选最佳阵容（4次一阵、2次二阵、1次三阵）； [311]  7次入选全明星西部首发阵容； [3-4]  2021年12月成为NBA历史三分王。 [345]</p>
<p>斯蒂芬·库里于2010年随美国队获土耳其世锦赛冠军，2014年随美国队获西班牙篮球世界杯冠军。2019福布斯100名人榜，斯蒂芬·库里排名第23位。</p>
<!--水平线标签  hr标签同样可以 hr + tab 一键生成<hr> 但最好习惯性地在后面加上/,养成良好的编码规范！-->
<hr/>
<!--换行标签 br + tab 可一键生成，默认生成换行标签<br>,属于自闭和标签，习惯性也加上/,但可加可不加，只是利于观看理解罢了！-->
斯蒂芬·库里（Stephen Curry），全名沃德尔·斯蒂芬·库里二世（Wardell Stephen Curry II），1988年3月14日出生于美国俄亥俄州阿克伦（Akron, Ohio），美国职业篮球运动员，司职控球后卫，绰号“娃娃脸刺客（Baby-Faced Assassin）”，效力于NBA金州勇士队。 [1]  [332]<br>
斯蒂芬·库里于2009年通过选秀进入NBA后一直效力于金州勇士队，新秀赛季入选最佳新秀第一阵容；2014-15、2016-17、2017-18赛季三次夺得NBA总冠军；两次荣膺常规赛MVP；2015-16、2020-21赛季两次当选NBA常规赛得分王； [308]  7次入选最佳阵容（4次一阵、2次二阵、1次三阵）； [311]  7次入选全明星西部首发阵容； [3-4]  2021年12月成为NBA历史三分王。 [345]<br>
斯蒂芬·库里于2010年随美国队获土耳其世锦赛冠军，2014年随美国队获西班牙篮球世界杯冠军。2019福布斯100名人榜，斯蒂芬·库里排名第23位。<br>
<!--根据效果显示可以看出，段落标签所产生的效果比换行标签所产生的文本间距要大一些，仅是通过换行符后文本间距很小！这是它们俩之间一个小小的区别！-->
<hr/>
<!--字体样式标签，例如： 粗体、斜体-->
使用strong标签使字体加粗---粗体: <strong>夏黄杰</strong><br/>
使用b标签使字体加粗---粗体: <b>夏黄杰</b> <br/>
使用em标签使字体成为斜体---斜体: <em>夏黄杰</em> <br/>
使用i标签使字体成为斜体---斜体: <i>夏黄杰</i> <br/>
<!--在HTML中通过font标签设置文本字体、大小、颜色-->
<font face="SimHei" size="5" color="red">夏黄杰,黑体</font> <br/>
<!---->
<font face="SimHei" size="5" color="red"><b>夏黄杰,黑体,加粗</b></font> <br/>
<font face="LiSu" size="8" color="yellow">夏黄杰，隶书</font> <br/>
<font face="LiSu" size="8" color="yellow"><i>夏黄杰，隶书，斜体</i></font> <br/>
<!--当前font标签其实被废弃了，逐渐被淘汰，所以会被IDE默认加上白横线。虽然不影响使用，仍然会有效果。但最好不要使用，在以后企业开发中，更是不建议使用这些被淘汰的标签！-->
<!--虽然font标签被HTML废弃了，但可以使用style属性来设置字体、大小、颜色-->
<p style = "font-family:STXingkai;color:blue;font-size:50px;">夏黄杰</p>
<hr/>
<!--特殊符号-->
空格在HTML中也是一个特殊符号！<br/>
<!--在HTML中，编写代码时隔开很多空格在网页上是显示不了的！相比于正常的文字间距只会隔开一个位置！-->
空     格 <br/>
空&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;格 <br/>
<!--通过&nbsp;来实现HTML中的多空格实现！！！，必须要记住比掌握，平时应用的较多！！！-->
<!--大于号、小于号-->
&gt;
<br/>
&lt;
<br/>
<!--&copy;版权符号-->
&copy;版权所有学@凡
<br/>
<!--$符号-->
&dollar;
<br/>
<!--¥符号-->
&yen;
<!--
特殊符号记忆方式:
&     ;
既&开头,;结尾!
写下一个&后再加上一个字母就可以看到HTML中所有以该字母开头的特殊符号，右侧是特殊符号的样式，左侧便是特殊符号对应的代码！！！
-->
</body>
</html>

## 图像标签

常见的图像格式：

- JPG
- GIF（动图形式）
- PNG
- BMP
- ....

在HTML中的图像标签用到的是img标签：

```html
<img src="../resources/images/ouwen.jpg" alt="欧文海报" title="凯里.欧文" width="1366" height="768">
```

- **<font color=&quot;red&quot;>;src(必填项)表示的是图像地址,可以填图像的相对地址和绝对地址，../   表示上一级目录,推荐使用相对地址！！！</font>;**
- **<font color=&quot;red&quot;>;alt（必填项）表示图像的替代文字，既当图片没有被加载处理时，便显示该图像的替代文字</font>;**
- title表示鼠标悬停提示文字
- width表示图像宽度
- height表示图像高度

eg:



<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>图像标签学习</title>
</head>
<body>
<!--
img标签学习:
src:图片地址    一般分为: 相对地址（推荐使用）  绝对地址
../   表示上一级目录！！！
-->
<img src="../resources/images/ouwen.jpg" alt="欧文海报" title="凯里.欧文" width="1366" height="768">
</body>
</html>

## 超链接标签及应用、锚链接（重点掌握）

链接标签：

```html
<a href="path" target="目标窗口位置">链接文本或图像</a>
```

- **<font color=&quot;red&quot;>;href属性表示的是链接路径</font>;**
- **<font color=&quot;red&quot;>;target属性表示的是链接在哪个窗口打开，一般分为俩种：</font>;**
  - **<font color=&quot;red&quot;>;当target属性的值为_blank时，既点击跳转后新打开一个窗口，不覆盖当前的网页窗口</font>;**
  - **<font color=&quot;red&quot;>;当target属性的值为_self时（默认的就是self值），既点击跳转后在当前网页打开链接，既覆盖了当前的网页窗口</font>;**
- **<font color=&quot;blue&quot;>;a标签中可以链接文本也可以链接图像，简单来说就是可以通过点击文本提示语跳转也可以通过设置图片来点击跳转！！！</font>;**

超链接：

- 页面间链接

  - 从一个页面链接到另一个页面

- **<font color=&quot;red&quot;>;锚链接（重点理解并掌握）可以实现页面间的跳转，也可以实现不同页面之间的具**置跳转！！！</font>;**

  - ```html
    锚链接:可以实现页面间的跳转，也可以实现不同页面之间的具**置跳转!
    例如: 从别的页面点击跳转到另一个页面的顶部或者尾部等等都能实现！！！
    1.需要一个锚标记，<!--使用a标签中的name属性作为标记！！！-->
    eg:
    <a name="top">
        <img src="../resources/images/top.jpg" alt="头部图片" width="1412" height="125">
    </a>
    2.跳转到标记，通过a标签中的href属性等于 #+标记名
    <a href="#top">
        <img src="../resources/images/top.png" alt="回到顶部" title="点击回到顶部" width="50" height="50">
    </a>
    如果是不同页面之间的具**置跳转，跳转到标记有一点不同,既 #+标记名 加在跳转的页面路径后面！！！
    eg:
    <a href="Hyperlink-tags.html#down" target="_blank">
        <img src="../resources/images/down.png" alt="跳转到超链接标签网页底部" title="点击跳转到超链接标签网页底部" width="50" height="50">
    </a>
    #
    ```

- **<font color=&quot;red&quot;>;功能性链接</font>;**

  - ```html
    1.邮件链接: mailto:  eg: <a href=&quot;mailto:2822527270@qq.com&quot;>;点击联系我！</a>;
    2.QQ链接: 在百度搜索QQ推广后进入官网，登入后选择推广工具，输入自己想要的提示语已经组件样式后，复制代码过来就可   以直接使用了!
      (代码中的图片地址可能过期了可以直接右键图片复制图片链接过来更改即可！)
    ```

eg:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>超链接标签及应用</title>
</head>
<body>
<!--使用a标签中的name属性作为标记！！！-->
<a name="top">
    <img src="../resources/images/top.jpg" alt="头部图片" width="1412" height="125">
</a> <br/>
<!--
a标签:
herf: 必填，表示要跳转到哪个页面
target: 表示跳转的窗口在哪里打开
       _blank  表示会在新的网页中打开，既不覆盖当前网页
       _self   表示在当前的网页中打开，既覆盖住当前网页
-->
<a href="images-tags.html">点击跳转到图像标签网页</a> <br/>
<a href="https://www.baidu.com" target="_self">点击跳转到百度</a> <br/>
<a href="https://www.baidu.com"  target="_blank">
    <img src="../resources/images/搜索.png" alt="搜索" title="点击跳转到百度搜索" width="200" height="200">
</a>
<p>
    <img src="../resources/images/ouwen.jpg" alt="欧文海报" title="凯里.欧文" width="1366" height="768">
</p>
<p>
    <img src="../resources/images/ouwen.jpg" alt="欧文海报" title="凯里.欧文" width="1366" height="768">
</p>
<p>
    <img src="../resources/images/ouwen.jpg" alt="欧文海报" title="凯里.欧文" width="1366" height="768">
</p>
<p>
    <img src="../resources/images/ouwen.jpg" alt="欧文海报" title="凯里.欧文" width="1366" height="768">
</p>
<p>
    <img src="../resources/images/ouwen.jpg" alt="欧文海报" title="凯里.欧文" width="1366" height="768">
</p>
<p>
    <img src="../resources/images/ouwen.jpg" alt="欧文海报" title="凯里.欧文" width="1366" height="768">
</p>
<p>
    <img src="../resources/images/ouwen.jpg" alt="欧文海报" title="凯里.欧文" width="1366" height="768">
</p>
<p>
    <img src="../resources/images/ouwen.jpg" alt="欧文海报" title="凯里.欧文" width="1366" height="768">
</p>
<p>
    <img src="../resources/images/ouwen.jpg" alt="欧文海报" title="凯里.欧文" width="1366" height="768">
</p>
<p>
    <img src="../resources/images/ouwen.jpg" alt="欧文海报" title="凯里.欧文" width="1366" height="768">
</p>
<!--锚链接:可以实现页面间的跳转，也可以实现不同页面之间的具**置跳转！
例如: 从别的页面点击跳转到另一个页面的顶部或者尾部等等都能实现！！！
1.需要一个锚标记
2.跳转到标记
#
-->
<a href="#top">
    <img src="../resources/images/top.png" alt="回到顶部" title="点击回到顶部" width="50" height="50">
</a> <br/>
<!--功能性链接
邮件链接: mailto:
QQ链接: 在百度搜索QQ推广后进入官网，登入后选择推广工具，输入自己想要的提示语已经组件样式后，复制代码过来就可以直接使用了!
(代码中的图片地址可能过期了可以直接右键图片复制图片链接过来更改即可！)
-->
<!--邮件链接-->
<a href="mailto:2822527270@qq.com">点击联系我！</a> <br/>
<!--QQ链接-->
<a target="_blank" href="http://wpa.qq.com/msgrd?v=3&uin=&site=qq&menu=yes">
    <img border="0" src="https://pub.idqqimg.com/wpa/images/counseling_style_53.png" alt="你好，加我领取视频会员!" title="你好，加我领取视频会员!"/>
</a> <br/>
<!--使用a标签中的name属性作为标记！！！-->
<a name="down">
    <img src="../resources/images/down.jpg" alt="底部图片" width="1412" height="125">
</a>
</body>
</html>
```

```html
<!DOCTYPE html>;
<html lang=&quot;en&quot;>;
<head>;
    <meta charset=&quot;UTF-8&quot;>;
    <title>;图像标签学习</title>;
</head>;
<body>;
<!--
 img标签学习:
 src(必填项):图片地址    一般分为: 相对地址（推荐使用）  绝对地址
 ../   表示上一级目录！！！
 alt（必填项）表示图像的替代文字，既当图片没有被加载处理时，便显示该图像的替代文字
 title表示鼠标悬停提示文字
 width表示图像宽度
 height表示图像高度
-->;
<img src=&quot;../resources/images/ouwen.jpg&quot; alt=&quot;欧文海报&quot; title=&quot;凯里.欧文&quot; width=&quot;1366&quot; height=&quot;768&quot;>;

<!--锚链接还可以实现不同页面直接的具**置跳转！！！
 a标签的herf属性中输入了跳转页面的地址后再加上 # + 对应锚链接标记的name属性的值 （这里是 # + down ）
 target属性选择_blank既点击跳转后打卡一个新的页面，默认的是_self既在当前页面跳转，覆盖了当前网页！-->;
<a href=&quot;Hyperlink-tags.html#down&quot; target=&quot;_blank&quot;>;
    <img src=&quot;../resources/images/down.png&quot; alt=&quot;跳转到超链接标签网页底部&quot; title=&quot;点击跳转到超链接标签网页底部&quot; width=&quot;50&quot; height=&quot;50&quot;>;
</a>;

</body>;
</html>;
```

效果图：

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudy62e3e2ba-5a70-4260-9e5e-d4e82f90a1ae.png)

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudy9eb8bde2-a082-438d-bfae-75475d912fd2.png)

## 行内元素和块元素

- 块元素
  - 无论内容多少，该元素独占一行
  - 例如：p、（h1-h6...）
  - 如果你新写了一个标签，它新开辟了一块空间，自动换了一行！它就属于块元素！！！
- 行内元素
  - 内容撑开宽度，左右都是行内元素的可以排在一行
  - 例如：a、strong、em...
  - 如果在行内没有主动换行的，它就属于行内元素！！！

eg：

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudy59372762-84d1-4b3c-8f8a-38e4fd476f3a.png)

## 列表

什么是列表：

- 列表就是信息资源的一种展示形式。它可以使信息结构化和条理化，并以列表的样式显示出来，以便浏览者能更快捷地获得相应的信息！

**<font size=&quot;5&quot; color=&quot;red&quot;>;列表的分类：</font>;**

- 无序列表

  - 无序列表是一个没有顺序的列表项目，在各条列前面使用●□◇◆等符号以示区隔。
  - HTML无序列表始于<ul>;标签，每个列表项始于<li>;标签；
  - **<font color=&quot;red&quot;>;无序列表中的<li>;标签的type属性有三个数值可选，默认属性是disc实心园。</font>;**
    **<font color=&quot;red&quot;>;分别为:disc为实心园、</font>;**
                 **<font color=&quot;red&quot;>;circle为空心园、</font>;**
                 **<font color=&quot;red&quot;>;square为实心小方块.</font>;**

- 有序列表

  - 有序列表是一列按照字母或数字等顺序排列的列表项目，注意有序列表的结果是带有前后顺序之分的编号,如果插入和删除一个列表项，编号会自动调整。
  - html有序列表始于<ol>;标签，每个列表项始于<li>;标签。
  - **<font color=&quot;red&quot;>;在有序列表中的<ol>;标签中:</font>;**
    **<font color=&quot;red&quot;>;type属性: 表示有序列表项目符号的类型！如果是用数字1、2、3类型来排序表示可以省略不写！</font>;**
    **<font color=&quot;red&quot;>;start属性: 表示列表从多少开始编号排序显示！如果是1开始可以省略不写！</font>;**

- 自定义列表

  - 自定义列表不仅仅是一列项目，而是项目及其注释的组合。

  - **<font color=&quot;red&quot;>;HTML自定义列表以<dl>;标签开始，每个自定义列表项以<dt>;开始。每个自定义列表项的定义以<dd>;开始。用于对术语或名称进行解释和描述。</font>;**

  - ```html
    <dl>;</dl>;: 自定义列表的规定标签!
    <dt>;</dt>;: 自定义列表的名称！
    <dd>;</dd>;: 自定义列表的内容！
    ```

  - **<font color=&quot;blue&quot;>;自定义列表的列表项前没有任何项目符号！</font>;**

eg:

```html
<!DOCTYPE html>;
<html lang=&quot;en&quot;>;
<head>;
    <meta charset=&quot;UTF-8&quot;>;
    <title>;列表学习</title>;
</head>;
<body>;
<!--有序列表 -----  html有序列表始于<ol>;标签，每个列表项始于<li>;标签。
应用范围: 试卷，问答...
-->;
<ol>;
    <li>;JAVA</li>;
    <li>;Python</li>;
    <li>;HTML</li>;
    <li>;CSS</li>;
    <li>;C/C++</li>;
</ol>;

<hr/>;

<!--在有序列表中的ol标签中:
type属性: 表示有序列表项目符号的类型！如果是用数字1、2、3类型来排序表示可以省略不写！
start属性: 表示列表从多少开始编号排序显示！如果是1开始可以省略不写！
-->;
<ol type=&quot;A&quot; start=&quot;2&quot;>;
    <li>;JAVA</li>;
    <li>;Python</li>;
    <li>;HTML</li>;
    <li>;CSS</li>;
    <li>;C/C++</li>;
</ol>;

<hr/>;

<ol type=&quot;I&quot; start=&quot;3&quot;>;
    <li>;JAVA</li>;
    <li>;Python</li>;
    <li>;HTML</li>;
    <li>;CSS</li>;
    <li>;C/C++</li>;
</ol>;

<hr/>;

<!--无序列表 -----  无序列表是一个没有顺序的列表项目，在各条列前面使用●□◇◆等符号以示区隔.
html无序列表始于<ul>;标签，每个列表项始于<li>;标签。
应用范围: 导航栏，侧边栏...
-->;
<ul>;
    <li>;JAVA</li>;
    <li>;Python</li>;
    <li>;HTML</li>;
    <li>;CSS</li>;
    <li>;C/C++</li>;
</ul>;

<hr/>;

<!--无序列表中的li标签的type属性有三个数值可选，默认属性是disc实心园。
分别为:disc为实心园、
      circle为空心园、
      square为实心小方块.
-->;
<ul>;
    <li type=&quot;circle&quot;>;JAVA</li>;
    <li type=&quot;circle&quot;>;Python</li>;
    <li type=&quot;circle&quot;>;HTML</li>;
    <li type=&quot;circle&quot;>;CSS</li>;
    <li type=&quot;circle&quot;>;C/C++</li>;
</ul>;

<hr/>;

<ul>;
    <li type=&quot;square&quot;>;JAVA</li>;
    <li type=&quot;square&quot;>;Python</li>;
    <li type=&quot;square&quot;>;HTML</li>;
    <li type=&quot;square&quot;>;CSS</li>;
    <li type=&quot;square&quot;>;C/C++</li>;
</ul>;

<hr/>;

<!--自定义列表
dl: 自定义列表的规定标签!
dt: 自定义列表的名称！
dd: 自定义列表的内容！

应用范围: 公司或者大型网站的底部...
-->;

<dl>;

    <dt>;课程名</dt>;
    <dd>;JAVA</dd>;
    <dd>;C/C++</dd>;
    <dd>;JAVAEE</dd>;
    <dd>;Python</dd>;
    <dd>;Linux</dd>;

    <dt>;前端学习内容</dt>;
    <dd>;用于画界面的标记语言:HTML</dd>;
    <dd>;用于美化界面:CSS</dd>;
    <dd>;用于处理业务逻辑:JavaScript</dd>;

</dl>;
</body>;
</html>;
```

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudyf35bbc83-563c-4a84-aafb-147328e737ef.png)

## 表格

为什么使用表格：

- 简单通用！
- 结构稳定

表格的基本结构：

- 单元格
- 行  tr
- 列   td
- **<font color=&quot;blue&quot;>;边框  border</font>;**
- **<font color=&quot;blue&quot;>;单元格间距   cellspacing     前提：没有设置边框合并！！！</font>;**
- **<font color=&quot;blue&quot;>;单元格边距   cellpadding    ——   既单元格边框和单元格内容之间的空白部分(以像素为单位)！</font>;**
- **<font color=&quot;red&quot;>;整个表格字段居中  style=&quot;text-align: center&quot;   一般在创建表格的table标签中就声明！</font>;**
- **<font color=&quot;red&quot;>;表格边框合并     style=&quot;border-collapse: collapse&quot; </font>;**
- **<font color=&quot;red&quot;>;表格边框颜色    bordercolor</font>;**
- **<font color=&quot;blue&quot;>;跨行  rowspan</font>;**
- **<font color=&quot;blue&quot;>;跨列  colspan</font>;**

**<font color=&quot;red&quot;>;注意点：table标签默认不会直接显示出表格的边框，可以通过table标签的border属性来添加边框，并赋值边框的宽度！</font>;**

eg:

```html
<!DOCTYPE html>;
<html lang=&quot;en&quot;>;
<head>;
    <meta charset=&quot;UTF-8&quot;>;
    <title>;表格学习</title>;
</head>;
<body>;
<!--
表格table
行   tr
列   td
边框  border
表格的整体宽度   width
单元格间距   cellspacing   如果该表格已经用style=&quot;border-collapse: collapse&quot;实现了表格的边框合并的话，那再怎么调整单元格间距的值也不会发生改变！！！
单元格边距   cellpadding   既单元格边框和单元格内容之间的空白部分(以像素为单位)。 cellpadding属性值越大，单元格中的内容到单元格边框的距离也就越大。
整个表格字段居中  style=&quot;text-align: center&quot;   注意: text-align 并不控制块元素自己的对齐，只控制它的行内内容的对齐!!!
表格边框合并     style=&quot;border-collapse: collapse&quot;  可以实现表格的边框合并！！！
表格边框颜色    bordercolor  例如: bordercolor=&quot;red&quot; 设置边框颜色为红色，默认边框颜色是黑色！！！

table标签默认不会直接显示出表格的边框，可以通过table标签的border属性来添加边框，并赋值边框的宽度！

-->;
<table border=&quot;1px&quot;  cellspacing=&quot;5px&quot; cellpadding=&quot;5px&quot;>;
    <tr>;
        <td>;1-1</td>;
        <td>;1-2</td>;
        <td>;1-3</td>;
        <td>;1-4</td>;
    </tr>;
    <tr>;
        <td>;2-1</td>;
        <td>;2-2</td>;
        <td>;2-3</td>;
        <td>;2-4</td>;
    </tr>;
    <tr>;
        <td>;3-1</td>;
        <td>;3-2</td>;
        <td>;3-3</td>;
        <td>;3-4</td>;
    </tr>;
</table>;

<hr/>;

<table border=&quot;1px&quot; style=&quot;text-align: center&quot;>;
    <tr>;
<!--td标签（列标签）的colspan属性表示: 跨列  ， 后面是值代表跨几列！-->;
<!--注意点: 在进行跨列后，行内内容不会自动居中，可以通过style属性来设置居中，style=&quot;text-align: center&quot; -->;
        <td colspan=&quot;4&quot; >;1-1</td>;
        <!--<td>;1-2</td>;
         <td>;1-3</td>;
         <td>;1-4</td>;-->;
    </tr>;
    <tr>;
<!--td标签（列标签）rowspan属性表示: 跨行  ， 后面是值代表跨几行！-->;
<!--注意点: 不管是跨行还是跨列都要注意是否会将后序的单元格挤出去！从而不美观，故要对多余出来的单元格进行删除！！-->;
        <td rowspan=&quot;2&quot;>;2-1</td>;
        <td>;2-2</td>;
        <td>;2-3</td>;
        <td>;2-4</td>;
    </tr>;
    <tr>;
        <td>;3-1</td>;
        <td>;3-2</td>;
        <td>;3-3</td>;
<!--<td>;3-4</td>;-->;
    </tr>;
</table>;

<hr/>;
<!--style=&quot;border-collapse: collapse&quot;可以实现表格的边框合并！！！-->;
<!--只需要给table添加bordercolor属性就可以给表格设置边框颜色了。-->;
<table border=&quot;1px&quot;  bordercolor=&quot;red&quot; style=&quot;text-align: center;border-collapse: collapse&quot; cellpadding=&quot;5px&quot;  >;
    <tr>;
        <td colspan=&quot;3&quot; style=&quot;color: brown&quot;>;<b>;学生成绩</b>;</td>;
    </tr>;
    <tr>;
        <td rowspan=&quot;2&quot;>;狂神</td>;
        <td>;语文</td>;
        <td>;100</td>;
    </tr>;
    <tr>;
        <td>;数学</td>;
        <td>;100</td>;
    </tr>;
    <tr>;
        <td rowspan=&quot;2&quot;>;夏黄杰</td>;
        <td>;语文</td>;
        <td>;100</td>;
    </tr>;
    <tr>;
        <td>;数学</td>;
        <td>;100</td>;
    </tr>;
</table>;
</body>;
</html>;
```

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudy8c322704-bbdb-4924-86d6-94cc376ddea1.png)

## 媒体元素

视频和音频

- 视频元素     ——   video
- 音频元素     ——   audio
- **<font color=&quot;blue&quot;>;loop 循环播放</font>;**
- **<font color=&quot;red&quot;>;controls: 控制条  一般都需要设置！不然无法点击播放除非设置了自动播放，但也少了调节音频，控制暂停与播放已经是否全屏、下载等等控制条所具备的功能！！！</font>;**
- **<font color=&quot;blue&quot;>;autoplay: 自动播放</font>;**
  - **<font color=&quot;red&quot; size=&quot;5&quot;>;注意点：在给audio标签和video标签添加上autoplay属性后，如果还是没有实现自动播放时，请去检查一下其浏览器是否支持自动播放，如果不支持请设置添加好URL从而实现该站点被浏览器允许媒体自动播放！！！</font>;**
- **<font color=&quot;blue&quot;>;style=&quot;display: none;&quot;  ——  隐藏控制条，例如在使用音频标签时，想让其作为背景音乐需要隐藏播放控制条时，可以通过去掉controls属性并添加style来实现！！！</font>;**

举Microsoft Edge 浏览器为例，解决浏览器没有实现autoplay属性自动播放功能！如图，在站点权限中添加了我们自己HTML所使用的URL后，该浏览器便运行我们的代码效果图在该站点中实现自动播放！：

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudy75b25167-6670-403d-bcaa-60336ecf1234.png)

eg:

```html
<!DOCTYPE html>;
<html lang=&quot;en&quot;>;
<head>;
    <meta charset=&quot;UTF-8&quot;>;
    <title>;媒体元素学习</title>;
</head>;
<body>;
<!--
音频和视频:
src(必填项，建议使用相对地址！): 资源路径
controls: 控制条  一般都需要设置，不然无法点击播放除非设置了自动播放，但也少了调节音频，控制暂停与播放已经是否全屏、下载等等控制条所具备的功能！！！
autoplay: 自动播放  注意点: 在给audio标签和video标签添加上autoplay属性后，
如果还是没有实现自动播放时，请去观察一下其浏览器是否支持自动播放，如果不支持请设置添加好URL从而实现该站点允许媒体自动播放！！！
loop 循环播放
style=&quot;display: none;&quot;  隐藏控制条，例如在使用音频标签时，想让其作为背景音乐需要隐藏播放控制条时，可以通过去掉controls属性添加style来实现！！！
-->;
<video src=&quot;../resources/video/海贼王.mp4&quot;  width=&quot;500px&quot; height=&quot;500px&quot; controls autoplay>;</video>;
<audio src=&quot;../resources/audio/清空.mp3&quot;  style=&quot;display: none;&quot; autoplay loop>;</audio>;
</body>;
</html>;
```

## 页面结构分析（重点掌握）

| 元素名  |                        描述                        |
| :-----: | :------------------------------------------------: |
| header  |  标题头部区域的内容（用于页面或页面中的一块区域）  |
| footer  | 标记脚部区域的内容（用于整个页面或页面的一块区域） |
| section |              Web页面中的一块独立区域               |
| article |                   独立的文章内容                   |
|  aside  |           相关内容或应用（常用于侧边栏）           |
|   nav   |           导航类辅助内容（例如 导航栏）            |

## iframe 内联框架

**<font color=&quot;blue&quot;>;对于iframe内联框架的使用要谨慎，虽然优点很多但缺点也比较明显。仍然要着重掌握并了解，因为iframe的强大功能的无可争议的，当前也不凡公司使用！！！</font>;**

```html
<iframe src=&quot;path&quot; name=&quot;mainFrame&quot;>;</iframe>;
```

- 其中src表示的是引用页面地址
- name表示的是框架标识名，自定义！

**<font color=&quot;blue&quot;>;iframe是一个内联框架，可以在当前HTML页面中嵌入另一个文档，一般情况下使用iframe直接在页面嵌套iframe标签再指定src就可以了！</font>;**

**<font color=&quot;blue&quot;>;iframe标签规定一个内联框架，一个内联框架被用来在当前HTML文档中嵌入另一个文档！！！</font>;**

**<font size=&quot;4&quot;>;所有的主流浏览器都支持<iframe>;标签。你可以把提示的文字放到<iframe>;和</iframe>;里面，这样不支持<iframe>;的浏览器就会出现提示的文字！！！</font>;**

**<font color=&quot;red&quot; size=&quot;4&quot;>;iframe的常用属性:</font>;**

- name： 规定<iframe>;的名称
- width： 规定<iframe>;的宽度
- height：规定<iframe>;的高度
- src：规定在<iframe>;中显示的文档的URL
- frameborder：规定是否显示<iframe>;周围的边框。（0为无边框，1为有边框）
- align：规定如何根据周围的元素来对齐,既改动的是框架的位置！<iframe>;。（left、 right、top、middle、bottom）
- scrolling：规定是否在<iframe>;中显示滚动条。（yes、no、auto）—— 一般都显示出来，不然只会显示你设置的内联框架大小一样的内容，从而影响浏览！！！

**<font color=&quot;red&quot; size=&quot;4&quot;>;iframe的优缺点：</font>;**

- 优点

  - **<font color=&quot;red&quot; size=&quot;5&quot;>;(最显著的作用：)重载页面时不需要重载整个页面，只需要重载页面中的一个框架页（减少数据的传输，减少网页的加载时间）</font>;**
  - 技术简单，使用方便，主要应用于不需要搜索引擎来搜索的页面
  - 方便开发，减少代码的重复率（比如页面的header，footer）

- 缺点

  - 会产生很多的页面，不易于管理
  - 不易打印
  - 多框架的页面会增加服务器的http请求

  **<font size=&quot;5&quot; color=&quot;red&quot;>;这里尤其注意：name 和 target属性经常用到，两个属性需结合使用，name是当前iframe内联框架定义的名称，a标签中的target 属性指定将要显示的内容到什么位置，可以选择iframe标签中的name属性的值！！！。</font>;**

具体看案例代码—— eg：

```html
<!DOCTYPE html>;
<html lang=&quot;en&quot;>;
<head>;
    <meta charset=&quot;UTF-8&quot;>;
    <title>;iframe 内联框架</title>;
</head>;
<body>;
<!--iframe标签的属性:
- name： 规定<iframe>;的名称
- width： 规定<iframe>;的宽度
- height：规定<iframe>;的高度
- src：规定在<iframe>;中显示的文档的URL
- frameborder：规定是否显示<iframe>;周围的边框。（0为无边框，1为有边框）
- align：规定如何根据周围的元素来对齐,既改动的是框架的位置！<iframe>;。（left、 right、top、middle、bottom）
- scrolling：规定是否在<iframe>;中显示滚动条。（yes、no、auto）—— 一般都显示出来，不然只会显示你设置的内联框架大小一样的内容，从而影响浏览！！！

iframe标签最显著和实用的作用是:
重载页面时不需要重载整个页面，只需要重载页面中的一个框架页（减少数据的传输，减少网页的加载时间）!!!
-->;
<iframe src=&quot;https://www.bilibili.com&quot; name=&quot;hello&quot; frameborder=&quot;0&quot; width=&quot;1520px&quot; height=&quot;800px&quot; scrolling=&quot;yes&quot; align=&quot;top&quot;>;<p>;iframe标签</p>;</iframe>;
<br/>;
<a href=&quot;https://www.csdn.net&quot; target=&quot;hello&quot;>;点击跳转</a>;
<!--这里将iframe标签中的name属性与a标签中的target属性想结合使用，
name 表示 iframe内联框架名称
target 表示将要跳转出来的内容显示到什么位置。 这里选择hello既表示点击跳转到CSDN的界面内容在iframe内联框架中显示！
这样一来，点击跳转后重载页面就不会重载整个页面，只需要重载内联框架中的内容。（减少数据的传输，减少网页的加载时间）！！！
-->;
<hr/>;
<p>;iframe 的优缺点 </p>;

    <p>;优点:</p>;

    <p>;重载页面时不需要重载整个页面，只需要重载页面中的一个框架页（减少数据的传输，减少网页的加载时间）</p>;

    <p>;技术简单，使用方便，主要应用于不需要搜索引擎来搜索的页面</p>;

    <p>;方便开发，减少代码的重复率（比如页面的header，footer）</p>;

    <p>;缺点:</p>;

    <p>;会产生很多的页面，不易于管理</p>;

    <p>;不易打印</p>;

    <p>;多框架的页面会增加服务气得http请求</p>;

    <p>;这里尤其注意：name 和 target属性经常用到，两个属性需结合使用，name是当前位置的名称，target 指定将要显示的内容到什么位置。</p>;
</body>;
</html>;
```

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudyb4205de4-e17c-4e17-a2de-bac2259d97e2.png)

**<font color=&quot;red&quot; size=&quot;4&quot;>;点击跳转后，只是重载了该页面中上面定义的iframe内联框架页跳转到CSDN，而非重载整个页面！！！</font>;**

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudyd6454317-5eae-4556-b121-364f63420f01.png)

## 初识表单post和get提交

```html
<form method=&quot;post&quot; action=&quot;Success.html&quot;>;</form>;
```

**<font color=&quot;blue&quot;>;在HTML中的表单标签为form，其中必填的俩个属性为methoc和action</font>;**

- method：规定如何发送表单数据  ——  常用值为: get / post
  -   **<font color=&quot;blue&quot;>;get方式: 用户可以在url中看到用户提交的信息所以不安全而且不能传输大文件，但该提交方式高效！</font>;**
  -   **<font color=&quot;blue&quot;>;post方式: 比较安全，在url看不到用户提交的信息，并且可以传输大文件！</font>;**
- action： 表单提交的位置，可以是网站，也可以是一个请求处理地址！
  - **<font size=&quot;5&quot; color=&quot;red&quot;>;如果是网站的话，对应的提交方式method要改成get才行！
    因为post提交方式会将数据提交到网站对应的数据库中，简单而言就是会改变其网站的数据，这是不被网站允许的，会报错！！！</font>;**

其中在form标签中常用的input标签:

- <input>; 标签规定了用户可以在其中输入数据的输入字段。
- <input>; 元素在 <form>; 元素中使用，用来声明允许用户输入数据的 input 控件。
- 输入字段可通过多种方式改变，取决于 type 属性。
  - 例如：
  - text  ——  表示文本框
  - password  —— 表示密码框，输入内容不会直接显示
  - submit  —— 提交按钮
  - reset  —— 重置按钮

eg:

```html
<!DOCTYPE html>;
<html lang=&quot;en&quot;>;
<head>;
    <meta charset=&quot;UTF-8&quot;>;
    <title>;表单学习</title>;
</head>;
<!--
表单form
action: 表单提交的位置，可以是网站，也可以是一个请求处理地址！如果是网站的话，对应的提交方式method要改成get才行！
因为post提交方式会将数据提交到网站对应的数据库中，简单而言就是会改变其网站的数据，这是不被网站允许的，会报错！！！
method: post,get 提交方式
     get方式: 用户可以在url中看到用户提交的信息所以不安全而且不能传输大文件，但该提交方式高效！
     post方式: 比较安全，在url看不到用户提交的信息，并且可以传输大文件！
input标签用于搜集用户信息
<input>; 标签规定了用户可以在其中输入数据的输入字段。

<input>; 元素在 <form>; 元素中使用，用来声明允许用户输入数据的 input 控件。

输入字段可通过多种方式改变，取决于 type 属性。
根据不同的 type 属性值，输入字段拥有很多种形式。输入字段可以是文本字段、复选框、掩码后的文本控件、单选按钮、按钮等等。
例如:
text  ——  表示文本框
password  —— 表示密码框，输入内容不会直接显示
submit  —— 提交按钮
reset  —— 重置按钮
-->;
<body>;
<form action=&quot;https://www.bilibili.com&quot; method=&quot;get&quot;>;
    <p>;名字: <input type=&quot;text&quot; name=&quot;username&quot;>;</p>;
    <p>;密码: <input type=&quot;password&quot; name=&quot;pwd&quot;>; </p>;
    <p>;
        <input type=&quot;submit&quot; value=&quot;提交&quot;>;
        <input type=&quot;reset&quot; value=&quot;重置&quot;>;
    </p>;

</form>;
</body>;
</html>;
```

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudyd0cc5345-00b6-4a60-b71c-33004d6f3e73.png)


### post提交方式下查看密码

如果想在提交方式method为post的情况下查看密码框的内容，可以通过以下操作：

首先在输入好数据后，在提交前鼠标右键选择检查，并选择到网络既得下图结果：

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudy51173cfc-553c-4640-803e-ca107a640a0e.png)

点击提交后，可以看到图中多了一个请求，虽然我这是报错的因为我的提交方式是post不被B站允许！

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudy425883ae-2c6c-43fe-b6ca-b7f35c21bf2a.png)

接着点击该请求，并选择到Payload即可查看到用户输入的数据！！！

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudyc3d7b914-0798-479f-a691-ba2ba1548a19.png)

同时，也可以选择标头选项来查看其他相关的信息！！！

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudy5aa34743-7a32-4e89-a9a4-d776f907cdb3.png)
## 文本框和单选框

**<font color=&quot;red&quot; size=&quot;5&quot;>;表单元素格式：</font>;**

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudy583de590-ef5b-46d6-903e-325a465cd4b2.png)

- **<font color=&quot;blue&quot;>;如果要提交表单的话，name属性是必填项！！！在表单提交时会附带name属性，之后JAVA程序读取时就是根据name属性来读取数据！！！</font>;**
- **<font color=&quot;red&quot; size=&quot;5&quot;>;name 属性用于对提交到服务器后的表单数据进行标识，或者在客户端通过 JavaScript 引用表单数据.只有设置了 name 属性的表单元素才能在提交表单时传递它们的值，因为服务端获取表单提交的数据是通过表单元素的 name 属性的值而得到的，没有 name 属性就无法得到表单元素提交给服务端的值</font>;**
- **<font color=&quot;blue&quot;>;至于size属性一般不会在HTML中来用，因为在CSS中会重点来设置宽度、高度等属性！！！</font>;**

**<font size=&quot;4&quot;>;文本框标签：</font>;**

- 文本输入框: input type=&quot;text&quot;
- **<font color=&quot;red&quot;>;value=&quot;杰哥&quot;  设置文本输入框的默认初始值</font>;**
- maxlength=&quot;8&quot;  设置文本框可输入的最大字符数
- size=&quot;30&quot;  设置文本框的长度  ———— 该属性一般不怎么用，因为CSS里会具体来设置！！！
- **<font color=&quot;red&quot; size=&quot;5&quot;>;placeholder=&quot;请输入姓名&quot; 设置提示信息，在文本框中以浅灰色的样式显示，但如果设置了value默认初始值则该提示信息不会显示！！！注意点: 该属性适用于 多行文本框和 type 属性值为 text, password, search, tel, url 或者 email 等的 <input>;表单元素。</font>;**

**<font size=&quot;4&quot;>;单选框标签：</font>;**

- 单选框按钮：input type=&quot;radio&quot;
- **<font color=&quot;blue&quot;>;value: type为checkbox或者radio时，此时value属性的值表示的是提交给服务器的值！！！</font>;**
- **<font color=&quot;red&quot; size=&quot;4&quot;>;在单选框中想要设置哪个选项为默认值，既添加上checked属性即可！！！</font>;**
- **<font color=&quot;red&quot; size=&quot;5&quot;>;name: 表示表单元素的名称.
  这里特别注意一下的是:
  当type为radio时，需要给所有的单选框设置name属性并且要设置相同的一个值，从而意思就是它们是同一个组的，既不能被同时选中。这样才能正确的表现为单选框！！！</font>;**

eg:

```html
<!DOCTYPE html>;
<html lang=&quot;en&quot;>;
<head>;
    <meta charset=&quot;UTF-8&quot;>;
    <title>;表单学习</title>;
<!--
在HTML中获取表单的数据有以下俩种方式:
1.在表单的input标签中指定id属性值，在script脚本中可以通过 “表格的名称.id名称.value”来访问表单中的值，
例如：register_form.username.value
2.因为一个文档中的 name 属性可能不唯一（如 HTML 表单中的单选按钮通常具有相同的 name 属性），所以 getElementsByName() 方法返回的是元素的数组，而不是一个元素。
例如该代码可以获得form中第一个name为“username”的元素:： var name = document.getElementsByName(&quot;username&quot;)[0].value;
-->;
    <script type=&quot;text/javascript&quot;>;
        function check() {
            var name = document.getElementsByName(&quot;username&quot;)[0].value;
            // 因为一个文档中的 name 属性可能不唯一（如 HTML 表单中的单选按钮通常具有相同的 name 属性），
            // 所以 getElementsByName() 方法返回的是元素的数组，而不是一个元素。
            //如下可以获得form中第一个name为“username”的元素!
            if(document.getElementsByName(&quot;username&quot;)[0].value==&quot;夏黄杰&quot;){
                alert(&quot;老铁，你又来了！&quot;);
             return;
            }else {
               alert(name+&quot;欢迎登入！&quot;);
            }
        }
    </script>;
</head>;
<!--
表单form
action: 表单提交的位置，可以是网站，也可以是一个请求处理地址！如果是网站的话，对应的提交方式method要改成get才行！
因为post提交方式会将数据提交到网站对应的数据库中，简单而言就是会改变其网站的数据，这是不被网站允许的，会报错！！！
method: post,get 提交方式
     get方式: 用户可以在url中看到用户提交的信息所以不安全而且不能传输大文件，但该提交方式高效！
     post方式: 比较安全，在url看不到用户提交的信息，并且可以传输大文件！
input标签用于搜集用户信息
<lt;input>; 标签规定了用户可以在其中输入数据的输入字段。

<input>; 元素在 <form>; 元素中使用，用来声明允许用户输入数据的 input 控件。

输入字段可通过多种方式改变，取决于 type 属性。
根据不同的 type 属性值，输入字段拥有很多种形式。输入字段可以是文本字段、复选框、掩码后的文本控件、单选按钮、按钮等等。
例如:
text  ——  表示文本框
password  —— 表示密码框，输入内容不会直接显示
submit  —— 提交按钮
reset  —— 重置按钮
-->;
<body>;
<!--
文本输入框: input type=&quot;text&quot;
value=&quot;杰哥&quot;  设置文本输入框的默认初始值
maxlength=&quot;8&quot;  设置文本框可输入的最大字符数
size=&quot;30&quot;  设置文本框的长度  ———— 该属性一般不怎么用，因为CSS里会具体来设置！！！
placeholder=&quot;请输入姓名&quot; 设置提示信息，在文本框中以浅灰色的样式显示，但如果设置了value默认初始值则该提示信息不会显示！！！
注意点: 该属性适用于 多行文本框和 type 属性值为 text, password, search, tel, url 或者 email 等的 <input>;表单元素。
-->;
<form  name=&quot;login&quot; action=&quot;Success.html&quot; method=&quot;get&quot;>;
    <p>;姓名: <input type=&quot;text&quot; name=&quot;username&quot;  maxlength=&quot;8&quot; placeholder=&quot;请输入姓名&quot;>;</p>;
<!--密码框:   input type=&quot;password&quot;  -->;
    <p>;密码: <input type=&quot;password&quot; name=&quot;pwd&quot; placeholder=&quot;请输入密码&quot;>; </p>;
<!--
单选框标签: input type=&quot;radio&quot;
value: type为checkbox或者radio时，此时value属性的值表示的是提交给服务器的值！！！
name: 表示表单元素的名称.
这里特别注意一下的是:
当type为radio时，需要给所有的单选框设置name属性并且要设置相同的一个值，从而意思就是它们是同一个组的，既不能被同时选中。这样才能正确的表现为单选框！！！
-->;
    <p>;性别:
        <input type=&quot;radio&quot; value=&quot;boy&quot; name=&quot;sex&quot;>;男
        <input type=&quot;radio&quot; value=&quot;girl&quot; name=&quot;sex&quot;>;女
    </p>;
    <p>;
        <input type=&quot;submit&quot; value=&quot;提交&quot; onclick=check()>;
        <input type=&quot;reset&quot; value=&quot;重置&quot;>;
    </p>;

</form>;
</body>;
</html>;
```

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudyc2189daa-95fa-41a5-b024-cb00f2199e2f.png)

## input标签的value属性详解(重点掌握)

**<font size=&quot;5&quot;>;在讲述input标签的value属性前，我们先了解一下input标签的name属性：</font>;**

- name 属性规定 input 元素的名称

- **<font color=&quot;red&quot; size=&quot;4&quot;>;name 属性用于对提交到服务器后的表单数据进行标识，或者在客户端通过 JavaScript 引用表单数据</font>;**

- **<font color=&quot;red&quot; size=&quot;5&quot;>;只有设置了 name 属性的表单元素才能在提交表单时传递它们的值，因为服务端获取表单提交的数据是通过表单元素的 name 属性的值而得到的，没有 name 属性就无法得到表单元素提交给服务端的值</font>;**

**<font size=&quot;5&quot;>;接下来，我们来仔细了解一下input标签的value属性：</font>;**

- **<font color=&quot;red&quot; size=&quot;4&quot;>;input 标签的 value 属性的作用是由 input 标签的 type 属性的值决定的</font>;**

- 当 type 的取值为 **<font color=&quot;blue&quot;>;button、reset、submit </font>;**中的其中一个时，此时 value 属性的值表示的是**<font color=&quot;blue&quot;>;按钮上显示的文本</font>;**

- 当 type 的取值为 **<font color=&quot;blue&quot;>;text、password、hidden</font>;** 中的其中一个时，此时 value 属性的值表示的是**<font color=&quot;blue&quot;>;输入框中显示的初始值</font>;**，此初始值可以更改，并且在提交表单时，value 属性的值会发送给服务器（**<font color=&quot;blue&quot;>;既是初始值，也是提交给服务器的值</font>;**）

- 当 type 的取值为**<font color=&quot;blue&quot;>; checkbox、radio</font>;** 中的其中一个时，此时 value 属性的值表示的是**<font color=&quot;blue&quot;>;提交给服务器的值</font>;**

- 当 type 的取值为**<font color=&quot;blue&quot;>; image</font>;** 时，**<font color=&quot;red&quot;>;点击它提交表单后，会将用户的点击位置相对于图像左上角的 x 坐标和 y 坐标提交给服务器</font>;**

- **<font color=&quot;blue&quot;>;type=&quot;checkbox&quot; </font>;**时，其 value 属性的值表示**<font color=&quot;blue&quot;>;在复选框呈勾选状态时</font>;**提交给服务器的数据值，**<font color=&quot;blue&quot;>;默认为 on</font>;**

- **<font color=&quot;blue&quot;>;type=&quot;image&quot;</font>;** 定义图像形式的提交按钮，此时必须把 src 属性 和 alt 属性 与 **<font color=&quot;blue&quot;>;<input type=&quot;image&quot;>; </font>;**结合使用（alt 属性表示图片未正常显示时，用于替换图片的提示；如果不写这个属性，当图片未正常显示时，会默认显示**<font color=&quot;blue&quot;>;提交</font>;**这两个字）

**<font color=&quot;red&quot; size=&quot;4&quot;>;特别的注意点：</font>;**

- **<font color=&quot;red&quot; size=&quot;4&quot;>;checkbox 型的 input 标签的不足之处在于：提交表单时，只有处于勾选状态的复选框的数据值才会发送给服务器。也就是说，如果没有任何一个复选框被选中，那么服务器就不会收到与其相关的数据项</font>;**

- **<font color=&quot;blue&quot; size=&quot;blue&quot;>;当设置 input 标签的 type 属性值为checkbox 或者 radio 时，必须同时设置 input 标签的 value 属性</font>;**

- **<font color=&quot;blue&quot; size=&quot;blue&quot;>;当 type=&quot;file&quot; 时，不能使用 value 属性</font>;**

## 按钮和多选框

**<font size=&quot;4&quot;>;在HTML中普通按钮标签创建为:</font>;**

```html
 <input type=&quot;button&quot; name=&quot;btn&quot; value=&quot;发送信息&quot;>;
```

要想实现该按钮的效果，需要在后面的js中去实现，这里不多加说明！

**<font size=&quot;4&quot;>;在HTML中多选框标签创建为:</font>;**

```html
 <input type=&quot;checkbox&quot; value=&quot;sleep&quot; name=&quot;hobby&quot;>;睡觉
 <input type=&quot;checkbox&quot; value=&quot;code&quot; name=&quot;hobby&quot;>;编程
 <input type=&quot;checkbox&quot; value=&quot;chat&quot; name=&quot;hobby&quot;>;聊天
 <input type=&quot;checkbox&quot; value=&quot;game&quot; name=&quot;hobby&quot;>;游戏
```

- **<font color=&quot;red&quot;>;在type取值为checkbox属性时，此时的value属性的值表示的是提交给服务器的值！！！ —————— 所以在定义value属性值时最好见名知意！！！</font>;**
- **<font color=&quot;red&quot; size=&quot;4&quot;>;多选框与单选框一样，当你想设置哪个选项为默认值时，便在哪个选项中添加上checked属性即可！！！</font>;**
- **<font color=&quot;red&quot; size=&quot;4&quot;>;对于多选框按钮的name属性没有强制性的要求要一致，但为了简便后面的数据处理。建议与单选框radio一样设置相同的name属性！！！</font>;**

**<font size=&quot;4&quot;>;除了普通按钮之外，在HTML中type还可以定义为image，既创建图像按钮！！！</font>;**

```html
<input type=&quot;image&quot; src=&quot;../resources/images/top.png&quot; height=&quot;100px&quot; width=&quot;100px&quot;>;
```

- **<font color=&quot;blue&quot; size=&quot;4&quot;>;input type=&quot;image&quot;  图像按钮 ， 点击它提交表单后，会将用户的点击位置相对于图像左上角的 x 坐标和 y 坐标提交给服务器</font>;**

## 列表框、文本域、文件域

**<font size=&quot;4&quot;>;在HTML中的列表框标签创建为:</font>;**

```html
<select name=&quot;select1&quot; >;
    <option value=&quot;china&quot;>;中国</option>;
    <option value=&quot;US&quot;>;美国</option>;
    <option value=&quot;JaPan&quot;>;日本</option>;
    <option value=&quot;Kr&quot; selected>;韩国</option>;
</select>;
```

- **<font color=&quot;red&quot;>;列表框的创建不使用input标签而是select标签</font>;**
- name属性是为了设置或获取对象的名称，简单说就是列表的名称！
- id属性是为了获取标识对象的字符串

**<font size=&quot;4&quot;>;在HTML中的文本域标签创建为:</font>;**

```html
<textarea name=&quot;textarea&quot; id=&quot;&quot; cols=&quot;30&quot; rows=&quot;10&quot; placeholder=&quot;输入内容:&quot;>;</textarea>;
```

- **<font color=&quot;red&quot; size=&quot;4&quot;>;其中的placeholder属性在文本框章节有提及过，既以浅灰色提示语的形式显示出来！</font>;**
- **<font color=&quot;blue&quot;>;文本域简单来说就是文本框的升级版，实现了多行多列的输入框！并且在网页中可以拖动右下角来改变形状大小！！！</font>;**
- cols属性表示列
- rows属性表示行

**<font size=&quot;4&quot;>;在HTML中的文件域标签创建为（这里提及的比较浅只是提一下！）:</font>;**

```html
<input type=&quot;file&quot; name=&quot;files&quot;>;
```

- 既较常见的上传文件标签，但要真正地实现上传需要对上传按钮提供方法等等！！！
- 简单效果图如下:

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudyf862a8c9-a2c5-49c4-acb4-febfbca44d96.png)

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudy44dc656e-6331-49b2-8e9b-69ccc9e70ae9.png)

## 搜索框滑块和简单验证

**<font color=&quot;blue&quot;>;上面的一些标签都没有强制性的验证消息功能，所以全由此类的标签建立的表单就算用户什么都不填依旧可以提交！！！</font>;**

**<font color=&quot;red&quot; size=&quot;5&quot;>;接下来我们学习一些带功能、带验证信息的标签：</font>;**

- **<font color=&quot;red&quot;>;邮件验证：</font>;**

  ```html
  <input type=&quot;email&quot; name=&quot;email&quot;>;
  ```

  <email并不是一个强制请求，所以name属性可以取其他名字！！！>;

- **<font color=&quot;red&quot;>;URL验证:</font>;**

  ```html
  <input type=&quot;url&quot; name=&quot;url&quot;>;
  ```

  URL跟email同理，其name属性可以任意取值！！！

- **<font color=&quot;red&quot;>;数字验证:</font>;**

  ```html
  <input type=&quot;number&quot; name=&quot;num&quot; max=&quot;100&quot; min=&quot;0&quot; step=&quot;1&quot;>;
  ```

  **<font color=&quot;red&quot;>;<与上同理，该数字验证标签的name属性可以任意取值，max与min可以设置数字输入的最大值与最小值，step则是设置步长既控制通过点击上下按钮来进行增加或删减的数字间隙！！！>;</font>;**

- **<font color=&quot;red&quot;>;滑块:</font>;**

  ```html
   <input type=&quot;range&quot; name=&quot;voice&quot; min=&quot;0&quot; max=&quot;100&quot; step=&quot;5&quot;>;
  ```

  **<font color=&quot;red&quot;>;<滑块的实现既input标签中type=range，其常用于音量滑块等实现，name属性可以任意取值，max与min设置滑块的最大值与最小值，step设置步长，它与数字验证有些不同，它没有上下按钮显示此时的步长用于控制的是用户通过键盘来移动滑块的单次滑块间隙！！！>;</font>;**

- **<font color=&quot;red&quot;>;搜索框:</font>;**

  ```html
   <input type=&quot;search&quot; name=&quot;search&quot;>;
  ```

  **<font color=&quot;blue&quot;>;<搜索框与普通的文本框表面看起来没有什么不同，唯一不同的就是在搜索框里输入内容后，在搜索框内部最右侧会有一个叉号❌可以用来一键删除搜索框内的内容！！！>;</font>;**

  eg:   效果图

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/25/kuangstudyf692c0d2-de6b-410a-9561-7f5acafa20f0.png)

## 表单的应用(重点掌握)

这里例举一些表单的简单应用：

- **<font size=&quot;5&quot;>;隐藏域</font>;**

  - **<font color=&quot;red&quot;>;要想将某些表单元素隐藏起来，不让用户看到，只需要在input标签里加上hidden属性即可！但要注意，这里只是将其隐藏起来，该表单元素本身还是存在的！！！eg：当你想将某一表单数据始终默认为某一个值时，不仅仅只有使其只读还可以通过先设置一个默认值再将其隐藏起来从而实现效果！！！</font>;**

  - ```html
    密码: <input type=&quot;password&quot; name=&quot;pwd&quot; value=&quot;123456&quot; hidden >;
    ```

- **<font size=&quot;5&quot;>;只读</font>;**

  - **<font color=&quot;red&quot;>;要想让某些表单元素变为只读，不让用户更改，只需要在input标签里加上readonly属性便可！</font>;**

  - ```html
    姓名: <input type=&quot;text&quot; name=&quot;username&quot;  maxlength=&quot;8&quot;  value=&quot;夏黄杰&quot; readonly>;
    ```

- **<font size=&quot;5&quot;>;禁用</font>;**

  - **<font color=&quot;red&quot;>;要想让某些表单元素变为禁用，不让用户选择时，只需要在input标签里加上disabled属性即可！</font>;**

  - ```html
    <input type=&quot;radio&quot; value=&quot;boy&quot; name=&quot;sex&quot; checked disabled>;男
    <!--该案例中的checked属性是将该按钮设置为默认选项-->;
    ```

- **<font size=&quot;5&quot;>;增强鼠标可用性（实用性很强）</font>;**

  - **<font color=&quot;red&quot;>;在html中，<label>;标签通常和<input>;标签一起使用，<label>;标签为input元素定义标注（标记）。 <label>;标签在单选按钮和复选按钮上经常被使用，使用该标签后，你点击单选按钮或复选按钮的文本也是可以选中的。其中label标签的for属性要与对应跳转的表单元素id属性值相等才能实现点击文本也能跳转！！!</font>;**

  - ```html
    <label for=&quot;search&quot;>;搜索（可直接点击）</label>;
    <input type=&quot;search&quot; id=&quot;search&quot;>;
    ```

## 表单初级验证（重点验证）

表单初级验证的常用方法：

- **<font size=&quot;4&quot;>;placeholder 提示信息</font>;**

  - ```html
    姓名: <input type=&quot;text&quot; name=&quot;username&quot;  maxlength=&quot;8&quot; placeholder=&quot;请输入姓名&quot;  >;
    <!--placeholder属性常用于某些输入框的控件中，属性值内容以提示信息的状态显示，从而提示用户输入！！！-->;
    ```

- **<font size=&quot;4&quot;>;required 非空判断</font>;**

  - ```html
    姓名: <input type=&quot;text&quot; name=&quot;username&quot;  maxlength=&quot;8&quot; placeholder=&quot;请输入姓名&quot; required >;
    <!--required属性的作用是非空判断，既添加了该属性的控件不允许为空！！！-->;
    ```

- **<font size=&quot;4&quot;>;pattern 正则表达式验证</font>;**

  - ```html
    <p>;自定义邮箱:
            <input type=&quot;text&quot; name=&quot;diyemail&quot; pattern=&quot;\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*&quot;>;
    </p>;
    <!-- pattern属性后面接着的是 正则表达式  通过正则表达式来判断输入框中的内容是否符合标准 ，在实际开发中经常被用到！！！经常需要用到的正则表达式可以在网上查询！-->;
    ```

  - **<font color=&quot;red&quot; size=&quot;4&quot;>;pattern属性后面接着的是 正则表达式  通过正则表达式来判断输入框中的内容是否符合标准 ，在实际开发中经常被用到！！！经常需要用到的正则表达式可以在网上查询！</font>;**

**<font color=&quot;blue&quot; size=&quot;4&quot;>;这里提到的都是一些简单的表单初级验证方法，高级一点的表单验证就需要JS来完成，后面再详细学习！</font>;**

