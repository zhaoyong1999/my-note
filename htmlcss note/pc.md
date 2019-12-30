# pc端
##css笔记

## 标签的特点
+ 关键词是有尖括号括起来
+ 成对出现
+ 结束标签比开始标签多了一个反斜杠

> 绝大多数的标签都符合以上原则，但是也有特殊标签比如img，这一类标签叫做“单标签”或者“自闭和标签”
> 在开始标签里除了关键词，你看到的比如img的title或者alt这都叫做“属性”，属性于属性之间用空格隔开。


## 常用的标签
+ 标题标签：h1-h6，快捷键：h${$级标题}*6+enter
+ 段落标签：p
+ 图片标签：img
    + src:这个图片代表路径
    + title：我们设置这个属性后，当鼠标滑上图片的时候，旁边会出现文字提示
    + alt:当网络比较慢或者图片路径不正确，造成图片加载失败，如果我们设置了alt这个属性，会在裂的图片旁边出现alt里面的文字，这样更有利于用户的体验。
+ 超链接：a 
    + href：链接地址
    + target：_blank(在新窗口打开)_self(在当前窗口打开)

+ 划分大区域：div
+ 划分小区域：span
+ 格式化标签
 + 加粗： b或者strong
 + 斜体： i或者em
 + 删除线： del
 + 增大字号： big
 + 减小字号： small
+ 预格式标签：pre
+ video 视频
+ audio 音乐
 + controls：控制器
 + autoplay：自动播放
 + loop：无限循环
+  ** 注释 ctrl+/**
+ ** 快速向下复制 alt+shift+↓**
+  **快速格式化 shift+alt+f**


##常用的样式
+ 清楚默认的margin值和padding值
  ```
  *{
          margin: 0;padding: 0;  
    }
  ```
  + a标签有默认文字颜色，控制文字颜色
  ```
  a{
      color:#333;
  }
  ```
  + 清除a标签的下划线
  ```
  a{
      text-decoration:none;
  }
  ```
  + 加上a标签的下划线
    ```
    a{
      text-decoration:underline;
    }
    ```
+ 清除列表前面的默认样式
```
ul,ol{
        list-style: none;
    }
```
+ 控制文字粗细用：font-weight
如果想让文字加粗用bold或者bolder，变细，比如说h1标题本身就是加粗的；如果想要变成正常font-weight:normal(400)

+ 文字缩进 text-indent：20px;如果想要首行缩进两个字的距离text-indent：2em;

+ 行高 line-height    例子：   /* 行高 */line-height: 40px;

+ 文字颜色  color     例子： color: aqua;

+ 字体大小   font-size   例子：font-size: 50px;

+ 鼠标滑上的状态
```
 li:hover{
            background-color: blueviolet
        }
```
+ 边框，边框的粗细，边框的样式：solid实线 dashed虚线，颜色
        border: 5px solid lightgrey;
+ 控制字体大小 
        font-size: 50px;

## 三大列表
 + 无序列表： <ul>
        <li>zzz</li>
        <li>xxx</li>
        <li>ccc</li>
    </ul>

 + 有序列表：<ol>
        <li>zzz</li>
        <li>xxx</li>
        <li>ccc</li>
           </ol>

 + 自定义列表 <dl>
     <dt>早餐</dt>
        <dd>豆浆</dd>
        <dd>鸡腿</dd>
            </dl>



       
## 标签的划分
+ 块级元素
 + 【特点】  
  + 独占一行  排列方式：从上到下
  + 写宽，高起作用
  + 可以设置css盒子模型(width/height/border/margin/padding)
  + 在不设置宽高时，宽是继承父级的宽度，高是由内容决定的
  + 可以嵌套其他标签
   + p标签不能嵌套p标签
 + 【html标签】
  div、p、h1-h6、ul、li、ol、dl、dt、dd、table>tr>td（表格>行>列）
 + [html新增标签]
   header 头部
   footer 尾部
   nav 导航
   section 区别大模块（div）
   article 文章

 + 行内元素
  + 【特点】
    + 允许其它元素共占一行
    + 写宽，高不起作用，它的宽高是由自身内容决定的
    + 排列方式：从左到右
     + 间隙问题
    + 基线对齐问题
  + 可以嵌套行内标签(不可以嵌套块级标签)
  + 【html标签】
  a 超链接、锚点、span 区分行内小模块、格式化标签： strong(强调作用)/b 加粗、em(强调作用)/i 斜体

+ 行内块元素
 + 【特点】
  + 允许其它元素共占一行
  + 写宽，高起作用
  + 排列方式：从左到右
  + 可以设置css盒子模型的所有属性（宽高）
  + 间隙问题
  + 基线对齐问题
 + 【html标签】
 img 图片、input 添加表单类的功能、select 下拉框
 + [html新增标签]
 audio 音频
 video 视频


## html标签的分类以及特点
 + 行内标签分为 **行内块级标签**、 **行内标签**
 + **行内块级标签和行内标签的特点**
  + 不同点：行内块级标签可以设置宽高、行内标签不可以设置宽高
  + 相同点：1.在一行显示，从左到右排
           2.在编辑代码时，行内标签和行内标签之间出现空格和换行时，会有间隙问题(4px)
            + 解决办法：给父级元素设置font-size：0；有css继承问题，导致子元素字体大小也为0，再给子元素设置font-size值就可以了
           3.基线对齐问题(不规则的基线对齐方式叫做基线对齐)
            + 解决办法：给所有html标签加一个css属性，
            `vertical-align`
             + `top`去找所有html标签中最高的顶部对齐
             + `middle`去找所有HTML标签中高度最高的中部对齐
             + `bottom`去找所有HTML标签中高度最高的底部对齐


## display的几个值(属性)
 + display:inline;转换成行内元素
 + **display:inline-block**;转换成行内块元素
  + 特点：既可以在一行显示，又可以设置宽高
 + **display:block**;转换成块级元素（出现）
 + **display:none**;让元素消失隐藏
  + 让html元素在页面(在浏览器中)消失不见，可以给标签设置display：none；这个属性。再想让这个标签显示出来，给这个标签设置display：block;

## 块级标签转化为行内块标签有几种方式？
> 行内块:在一行显示，可以设置宽高
- display:inline-block 行内块
  - 在一行显示，从左向右排布
  - 间隙
  - 基线对齐
- float:left/right 行内块
   - float:left;左浮动，从左向右排布
   - float:right;右浮动，从右向左排布
   - 特点：没有基线对齐和间隙问题

## float 浮动
> 浮动值：**left左浮动/right右浮动**/none不浮动
### 浮动的特点
+ 没有间隙和基线对齐问题
+ 所有的标签都可以设置浮动这个属性(行内标签和块状标签都可以设置)
+ 浮动元素不设置宽高时，宽高由内容决定的
+ 行内标签、行内块级标签和文字会围绕着浮动标签排布(图文混编)
 + 给图片设置浮动，文字会在图片周围环绕
脱离文档流(父元素找不到子元素，高度为0)，相当于来到了第二层级，平行于默认的文档


### 清除浮动带来的影响(面试题--清除浮动)
> 浮动带来什么影响？ 子元素设置浮动属性，父元素找不到子元素了，父元素高度为0(脱离文档流)
+ 给父元素设置一个固定的高度
+ 给父级元素设置一个css属性
`overflow：hidden；溢出隐藏`
+ 给子元素设置浮动属性的最后面加一句话
`<div style="clear:both;">`
+ **利用伪元素来清楚浮动带来的影响**
 + 给子元素设置完浮动后，需要给父元素加一个类名`class="clear"`
 + 需要把清除html默认样式的css样式表引入进来`reset.css`
```
.clear:after{
display:block;
content:"";
clear:both;
height:0;
visibility: hidden;
}
当前的.clear{zoom:1} //让它自己有独立的布局，兼容IE6以下
```
## 补充
### 伪元素
> 用css代码向指定的元素内添加假的(html中不存在)的内容
> ：before 在所有的div内容之前添加
> ：after 在所有的div内容之后添加

** 用伪元素的两个前提**
- 需要带有display:block;这个css属性
- 需要带有content:"";这个css属性，content内容可以为空
```
.box::before{
    display: block;
    content: "000";
    color: green;
}
.box::after{
    display: block;
    content: "111";
    color: blue;
}
```


## css盒子模型
 在HTML页面中相当于一个大仓库，盒子和盒子之间的间距是外边距(margin)，盒子内有白色泡沫相当于内边距(padding)，盒子内的物品有宽高(width/height),盒子的厚度是边框(border)
 + width 宽度
 + height 高度
 + border 边框
   + `border:1px solid red;` 
   + `border-top:1px solid red; 上边框线                `
  + `border-bottom:1px solid red; 下边   框线`
  + `border-left:1px solid red; 左边框线`

  + border-width:1px; 边框的宽度
  + border-style:solid; 边框的样式(风格)
  + border-color:red; 边框的颜色
 + margin 外边距
  **第一种写法：当设置多个值时**
  + margin:1px 2px 3px 4px;上 右 下 左(顺时针)
  + margin：1px 2px 3px;上 左右 下
  + margin:1px 2px; 上下 左右
  + margin:1px;代表四个方向的值
  **第二种写法：当设置一个值或两个值**
  + margin-left:1px;左外边距
  + margin-top:1px;上外边距
  + margin- right:1px;右外边距
  + margin-bottom:1px;下外边距
 + padding 内边距
  **第一种写法：当设置多个值时**
  + padding:1px 2px 3px 4px;上 右 下 左(顺时针)
  + padding：1px 2px 3px;上 左右 下
  + padding:1px 2px; 上下 左右
  + padding:1px;代表四个方向的值
  **第二种写法：当设置一个值或两个值**
  + padding-left:1px;左内边距
  + padding-top:1px;上内边距
  + padding- right:1px;右内边距
  + padding-bottom:1px;下内边距

 **什么情况下使用margin外边距**
 一般常用在盒子与盒子之间的间距，块级标签与块级标签之间的间距，这时候可以使用margin外边距

**什么情况下使用padding内间距边距**
 一般常用在盒子内(里面)的间距，行内标签与行内标签之间的间距，这时候可以使用padding内边距

**盒模型的计算公式**
 allwidth = 本身内容的宽度 + 左右padding + 左右border
 
 allheight = 本身内容的高度 + 上下padding + 上下border

**用border制作实心的三角形**
 > `border-width`来控制实心三角形的大小
 头部
  <style>
    .box{
        width: 0;
        border-width: 50px;
        border-style: solid;
        border-color: transparent transparent blue transparent;
    }
    /* transparent 透明 */
    </style>
 身体
     <div class="box"></div>


## CSS属性之background
> 如果需要使用背景图片时，需要给这个元素设置宽高
- background-color: yellow; 背景颜色
- background-image: url(1.jpg); 背景图片
- background-size:100% 100%; 设置背景图片的大小
- background-repeat: no-repeat; 设置背景图片是否平铺
    - 默认值  repeat 平铺
    - no-repeart 不平铺
- background-position: 70px 50px; 改变背景图片的位置
    - 第一个值代表的是x轴，水平方向的值
    - 第二个值代表的是y轴，垂直方向的值
    - 单位：px(像素)、英文单词(center\left\bottom..)
    - 让背景图片在盒子的水平垂直方向(x\y轴的中心点)
        - `background-position:center center;`

**综合写法**
- background: yellow url(icon1.png) no-repeat 40px 50px;
- background-size: 50%;
> 如果想要设置背景图片的大小，需要另起一行设置


## css属性定位
> 定位是结合四个方向值来用的(left/right/top/bottom)
### 相对定位(`position:relative`)
**特点：**
+ **不脱离文档流**(原来的位置还占用着)
+ **参照物是本身**(自己)
+ 相对定位的元素比其他元素权重大，会盖在其他元素上面
+ 当设置四个方向值时，left和top生效
+ **给绝对定位当参照物来用**

**相对定位在什么情况下使用**
+ 想改变自己位置时，又不影响其他元素，可以使用相对定位

### 绝对定位(position:absolute)
**特点**
+ 脱离文档流(原来的位置不在了)
+ 不设置参照物时，参照物是body
+ 人为设置参照物时，需要满足两个条件
 + 必须是绝对定位元素的父级元素(曾祖父)
 + 必须给这个父元素设置一个定位属性(相对、绝对、固定)
+ 当绝对定位元素不设置宽高时，宽高是由内容决定的
**什么情况下使用绝对定位**
> 想让元素脱离文档流(原来的位置不占用了)，让它在哪就在哪的时候，可以使用绝对定位
### 固定定位(position:fixed)
+ 参照物是浏览器的可视窗口
+ 在不设置宽高时，宽高由内容决定的
+ 脱离文档流(原来的位置不在了)
```
回到顶部效果：当href值为空或为#使，可以实现回到顶部效果
<a href="">回到顶部</a>
<a href="#">回到顶部</a>
```
> 当给元素设置`绝对定位`、`固定定位`属性时，是行内块的效果




## css引入的几种方式
 + 行内式： 在标签后面加一个style属性
 ```
 <div style="width:100px;height:100px;background:darkorange">box</div>
 ```
 
 + 内嵌式：将css代码放在style标签中，再通过css选择器来获取html标签，并给他添加css样式
  + 一般放在head标签中(title下面)
 ```
 <style>
         div{
             width:100px;
             height:100px;
             background:darkcyan; 
         }
 </style>
 ```

 + **外链式**：将css代码单独放在一个文件中，再通过link标签进行引入
  + 一般放在head头部中，title下面
  + 特点：一个单独的CSS样式表，可以用在不同的HTML页面中
 ```
 <link rel="stylesheet" href="index.css">
 ```
 
 + 导入式
 ```
 <style>
        @import url("index.css");
 </style>
 ```


### css选择器
> 作用：是为了获取html标签，并给html标签添加css样式的

+ 标签选择器
 + 权重：1
 + 特点：当使用标签选择器时，会在html页面中，查找所有是div标签的，并给它添加css样式

+ 类选择器
 + 特点：在标签名的后面加一个class属性，再通过类名当做选择器来用，在css样式中类名前面加一个"."
 + 权重：10
 + 类名可以重复
 + 类名可以有多个 例如：<div class="div1 title">333</div>

+ 后代选择器
 + 特点：在一个大的范围内，去查找其他标签
 + 权重：所有选择器相加之和
 + 语法：.last ul span{} 选择器之间都是以空格隔开
 + 后代选择器可以跨辈（祖辈选择器 后代选择器{}）

+ 分组选择器
 + 特点：将同一份css样式分别给了不同的html标签
 + 权重：独立计算的不会叠加
 + 语法：选择器，选择器，选择器{}
  + 每个选择器用 **，** 隔开

+ id选择器
 + 特点：在标签名的后面加一个id属性，用id名当做选择器来用，在css样式中，在id名前面要加一个"#"
 + 权重100
 + id选择器在html页面中，具有唯一性，不能同名（不能重复）
 + id选择器配合js来使用的
   ```
    <style>
        div{}
        .div1{}
        #div2{}
    </style>
    <div class="div1" id="div2">大盒子</div>
    ```

+ 伪类选择器
 + 权重：10
 + ：hover鼠标经过时的状态


### css样式属性
+ /* 宽度 */
  width:200px;
+ /* 高度 */
  height: 100px;
+ /* 文字垂直居中  行高 垂直居中*/
  /* line-height: 100px; */
+ /* 背景颜色 */
  background-color: green;
+ /* 字体大小 */
  font-size: 24px;
+ /* 字体颜色 */
  color: red;
+ /* 文字水平居中 */
  text-align: center;  left 居左； right 居右
+ /* 字体加粗 */
  font-weight: bold;
+ /* 字间距 */
  letter-spacing:1px;
+ /* 溢出隐藏 */
  overflow: hidden;
+ /* 溢出变... */
  text-overflow:ellipsis;
+ /* 首行缩进 */
  text-indent: 2em;
  + /* 背景图 */
    background:url("网址")
    + /* 大盒子水平居中 */
    margin:0 auto;
+   /* 去掉加粗 */
    font-weight: normal;
+ 鼠标滑过变成手
.header .login .box .gwc:hover{ cursor: pointer; }
+ 图形变成圆
border-radius: 50%;
+ 文本框
<input type="text">
+ 阴影代码
(内容)text-shadow： 2px 2px 6px rgba(0, 0, 0,0, .4);
<!-- 水平x 垂直y 模糊程度 模糊距离 颜色 -->
 (框)box-shadow: 2px 2px 6px rgba(0, 0, 0, .4);
+ 行内块设margin没用
 + 解决办法 给父级设
 + 转成块状元素
+ 选择第几个
.quan header .nav li:nth-child(3){
    margin-bottom: 0;
}

+ li:nth-child(odd){
            background: red;
            偶数行变红
        } 
        li:nth-child(even){
            background: green;
            奇数行变红
        } 

+ <!-- 通过角度添加渐变色   -->
    background:linear-gradient(45deg,red,blue,green) ;



## 色值
+ 英文单词 red/green
+ **16进制** #000fff/#ff2244   缩写：#ffffff 缩写成#fff，#ff2244 缩写成#f24
+ rgb，红色 绿色 蓝色
+ **rgba** r红色 g绿色 b蓝色 a透明的（值0到1）
 + rgb（255，255，255） 白色
 + rgb(0,0,0,) 黑色
 + rgba(0,0,0,0.3)



## 在项目中需要哪些文件和文件夹
zhufeng(项目的名称-文件夹)
+ css文件夹
 + index.css
 + reset.css

+ image文件夹
 + 里面都是图片(.jpg/.png)

+ js文件夹
 + xxx.js 文件(实现动态效果，交互))

+ index.html
+ xxx.html



## 路径
**相对路径**
+ 如果是同级(兄弟)关系，可以直接写文件(文件夹)的名字
+ 下一级 /
+ 返回上一级../
> 一般用在引入图片地址、css样式表中、、、

**绝对路径**
>指带域名文件的完整路径或磁盘中指定文件的全部路径
http://www.baidu.com/
D:\2019\17电子商务\20190917PM\zhufeng\image\logo.png
> 一般用在网站的尾部、**友情链接**上


