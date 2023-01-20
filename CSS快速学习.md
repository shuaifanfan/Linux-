> [b站视频](https://www.bilibili.com/video/BV1YJ411a7dy/?p=5&share_source=copy_web&vd_source=1a5ac5d55ef25e33a1c36c75b3fe43f0),[博客笔记位置](https://www.kuangstudy.com/bbs/1582696151428526082)

# 1、CSS是什么

如何学习

1.CSS是什么

2.CSS怎么用（快速入门）

**3.CSS选择器（重点 ， 难点）**

4.美化网页（文字，阴影，超链接，列表，渐变...）

5.盒子模型

6.浮动

7.定位

8.网页动画（特效效果）

## 1.1什么是CSS

Cascading Style Sheet  层叠级联样式表

## 1.2 发展史

CSS1.0

CSS2.0	DIV(块) + CSS,	HTML与CSS结构分离的思想	网页变得简单

CSS2.1	浮动，定位

CSS3.0	圆角，阴影，动画....	浏览器兼容性~

## 1.3 快速入门

**style**

**基本入门**

代码示例

```html
&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;en&quot;&gt;
&lt;head&gt;
    &lt;meta charset=&quot;UTF-8&quot;&gt;
    &lt;title&gt;Title&lt;/title&gt;

    &lt;!--规范，&lt;style&gt; 可以编写CSS代码 每一个声名使用分号结尾
    语法：
        选择器{
            声名1;
            声名2;
            声名3;
        }
    --&gt;
    &lt;style&gt;
        h1{
            color: aquamarine;
        }
    &lt;/style&gt;
    
&lt;/head&gt;
&lt;body&gt;

&lt;h1&gt;这是一个标题&lt;/h1&gt;

&lt;/body&gt;
&lt;/html&gt;
```

css的优势

1、内容和表现分离

2、网页结构表现统一，可以实现复用

3、样式十分的丰富

4、建议使用独立于HTML的css文件

5、利用SEO，容易被搜索引擎收录

## 1.4 CSS的3种导入方式

优先级：就近原则

```html
&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;en&quot;&gt;
&lt;head&gt;
    &lt;meta charset=&quot;UTF-8&quot;&gt;
    &lt;title&gt;导入方式&lt;/title&gt;

&lt;!-- 内部样式 --&gt;
    &lt;style&gt;
        h1 {
            color: black;
        }
    &lt;/style&gt;

    &lt;!-- 外部样式 --&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;css/style.css&quot;&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;!-- 行内样式：在标签元素中，编写一个style属性，编写样式即可 --&gt;
&lt;h1 style=&quot;color: aqua&quot;&gt;标签&lt;/h1&gt;

&lt;/body&gt;
&lt;/html&gt;
```

拓展：外部样式两种写法

1.链接式

HTML

```html
 &lt;!-- 外部样式 --&gt;
 &lt;link rel=&quot;stylesheet&quot; href=&quot;css/style.css&quot;&gt;
```

2.导入式

@import是CSS 2.1特有的

```html
&lt;!-- 导入式 --&gt;
&lt;style&gt;
    @import url(&quot;css/style.css&quot;);
&lt;style&gt;
```

# 2、选择器

---

&gt; 作用：选择页面上的某一个或某一类元素

## 2.1 基本选择器

### 1.标签选择器

**特点：选择一类标签   标签{}**   

```html
&lt;head&gt;
    &lt;meta charset=&quot;UTF-8&quot;&gt;
    &lt;title&gt;标签选择器&lt;/title&gt;

    &lt;style&gt;
        /* 标签选择器,会选择到页面上所有的这个标签的元素 */
        h1{
            color: #aa1133;
        }
    &lt;/style&gt;

&lt;/head&gt;
&lt;body&gt;

&lt;h1&gt;学Java&lt;/h1&gt;
&lt;h1&gt;学CSS&lt;/h1&gt;

&lt;/body&gt;
```

### 2.类选择器

**特点：选择所有class属性一致的标签，跨标签  .类名{}**

```html
&lt;head&gt;
    &lt;meta charset=&quot;UTF-8&quot;&gt;
    &lt;title&gt;类选择器&lt;/title&gt;

    /* 类选择器的格式   .class的名称{} */
    &lt;style&gt;
        .唐建华{
            color: aqua;
        }
    &lt;/style&gt;


&lt;/head&gt;
&lt;body&gt;

    &lt;h1 class=&quot;唐建华&quot;&gt;学Java&lt;/h1&gt;
    &lt;h1 class=&quot;tjh&quot;&gt;我学Java&lt;/h1&gt;

```

### 3.ID选择器

**特点：全局唯一  #id{}**

```html
&lt;style&gt;
    /* ID选择器 ： ID必须保证全局唯一
    #id名称{}
    不遵循就近原则，固定的
    id选择器 &gt; class选择器 &gt; 标签选择器
    */
    #tangjianhua {
        color: #aa1133;
    }
&lt;/style&gt;
```

## 2.2 层次选择器

 ### 1、后代选择器

&gt;在某个元素的后面、祖爷爷，爸爸，儿子

```css
/* 后代选择器 */
&lt;style&gt;
body p{
    background: red;
}
&lt;/style&gt;
```



### 2、子选择器

&gt;一代，儿子

```css
/** 子选择器 **/
&lt;style&gt;
body &gt; p{
    background: aquamarine;
}
&lt;/style&gt;
```

### 3、相邻兄弟选择器

&gt; 同辈、相邻（对下不对上）、只有一个

```css
/* 相邻选择器 */
&lt;style&gt;
.active + p{
    background: red;
}
&lt;/style&gt;
```

### 4、通用选择器

&gt; 当前选中元素的向下的所有兄弟元素

```css
/* 通用兄弟选择器 */
&lt;style&gt;
.active ~ p{
    background: red;
}
&lt;/style&gt;
```

## 2.3 结构伪类选择器



## 2.4 属性选择器

&gt; 把ID + class结合 	
&gt;
&gt; = 绝对等于
&gt;
&gt; *= 选择所有属性
&gt;
&gt; ^= 选择以什么开头的属性
&gt;
&gt; $= 选择以什么结尾的属性

```html
&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;en&quot;&gt;
&lt;head&gt;
    &lt;meta charset=&quot;UTF-8&quot;&gt;
    &lt;title&gt;Title&lt;/title&gt;

    &lt;style&gt;
        .demo a{
            float: left;
            display: block;
            height: 50px;
            width: 50px;
            border-radius: 10px;
            background: aquamarine;
            text-align: center;
            text-decoration: none;
            margin-right: 5px;
            font: bold 20px/50px Arial;
        }
        /*属性选择器    属性名 = 属性值（正则）
          存在ID属性的元素   a[id = ]{}
        */
        a[href $= g]{
            background: red;
        }

    &lt;/style&gt;

&lt;/head&gt;
&lt;body&gt;

&lt;p class=&quot;demo&quot;&gt;
    &lt;a href=&quot;http://www.baidu.com&quot; class=&quot;links itme&quot; id=&quot;first&quot;&gt;1&lt;/a&gt;
    &lt;a href=&quot;http://www.bilibili.com&quot; class=&quot;links itme itme&quot;&gt;2&lt;/a&gt;
    &lt;a href=&quot;images/123.html&quot; class=&quot;links itme&quot;&gt;3&lt;/a&gt;
    &lt;a href=&quot;images/456.jpg&quot; class=&quot;links itme&quot;&gt;4&lt;/a&gt;
    &lt;a href=&quot;sad&quot; class=&quot;links itme itme&quot;&gt;5&lt;/a&gt;
    &lt;a href=&quot;adc&quot; class=&quot;links itme&quot;&gt;6&lt;/a&gt;
&lt;/p&gt;

&lt;/body&gt;
&lt;/html&gt;
```


# 3、美化网页元素

## 3.1 为什么要美化网页

1、有效的传递页面信息

2、美化网页，页面漂亮，才能吸引用户

3、凸显页面的主题

4、提高用户的体验

span标签：重点要突出的字，使用span套起来

```html
&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;en&quot;&gt;
    &lt;head&gt;
        &lt;meta charset=&quot;UTF-8&quot;&gt;
        &lt;title&gt;Title&lt;/title&gt;

        &lt;style&gt;
            .title1{
                font-size: 50px;
                background: aquamarine;
            }
        &lt;/style&gt;

    &lt;/head&gt;
    &lt;body&gt;

        &lt;span class=&quot;title1&quot;&gt;学习的人最帅&lt;/span&gt;

    &lt;/body&gt;
&lt;/html&gt;
```

## 3.2 字体样式

```html
&lt;!--
font-family: 字体
font-size：  字体大小
font-weigth：字体粗细
color：      字体颜色
--&gt;
&lt;style&gt;
    body{
        font-family: 仿宋_GB2312;
    }
&lt;/style&gt;
```

## 3.3 文本样式

1、颜色	color	rgb	rgba

**2、文本对齐的方式	text-align = center**

**3、首行缩进	text-indent: 2em**

**4、行高	line-heigth:**		单行文字上下居中 line-heigth = heigth 

5、装饰	text-decoration

**6、文本图片水平对齐：vertical-align:middle**

```html
&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;en&quot;&gt;
&lt;head&gt;
    &lt;meta charset=&quot;UTF-8&quot;&gt;
    &lt;title&gt;Title&lt;/title&gt;
    &lt;!--
    颜色：
        单词
        RGB: 0~F
        RGBA  A: 0~1
        text-align：排版，居中（center）
        text-indent: 首行缩进
        line-heigth：行高 （和快点高度一致，就可以上下居中）
    --&gt;
    &lt;style&gt;
        h1{
            color: rgba(0,255,255,0.8);
            text-align: center;
        }
        .p1{
            text-indent: 2em;
        }
    &lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;h1&gt;背景故事&lt;/h1&gt;
&lt;p class=&quot;p1&quot;&gt;天地初开，太古混乱。&lt;/p&gt;
&lt;p&gt;灵长之战后，时空人祖、九巫、始佛、幽冥、大魔神相继出世，开创道法，威临八方，众生朝迎，世人尊为始祖。&lt;/p&gt;
&lt;p&gt;天尊无敌当世，始祖名传古今。&lt;/p&gt;
&lt;p&gt;但，皆不可得长生……&lt;/p&gt;
&lt;p&gt;…………&lt;/p&gt;
&lt;p&gt;张若尘自逆境中崛起，从平凡中非凡，在这一条满是英才、妖魔、美人的长生路上，走出一个崭新的大世。&lt;/p&gt;

&lt;/body&gt;
&lt;/html&gt;
```

## 3.4 列表

```css
/*
list-style
none	去掉原点
circle	空心圆
decimal	数字
square	正方形
*/
```

## 3.5 背景

```css
&lt;style&gt;
div{
    width: 1000px;
    height: 1000px;
    border: 1px solid red;
    background-image: url(&quot;images/OIP-C.jpg&quot;);
}
/*沿X平铺*/
.div1{
    background-repeat: repeat-x;
}
/*沿Y平铺*/
.div2{
    background-repeat: repeat-y;
}
/*不平铺*/
.div3{
    background-repeat: no-repeat;
}
&lt;/style&gt;
```

# 4 浮动

## 4.1 父级边框塌陷问题

解决方案：

1、增加父级元素高度

```css
#father{
    border:1px #000 solid;
    height:800px;
}
```

2、增加一个空DIV标签，清除浮动

```css
&lt;div class = &quot;clear&quot;&gt;&lt;/div&gt;
.cleal{
    clear:both;
    margin:0;
    padding:0;
}

3、overflow

在父级元素中增加一个	overflow：hidden

4、父类添加一个伪类：after

```css
#father:after{
    content:&#39;&#39;;
    display:block;
    clear:both;/*消除浮动*/
}
```