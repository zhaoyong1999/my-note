# 移动端
## 了解移动端
### 产品形态
+ pc端和移动端是分离开的,两套项目,两个域名
 
  + 结构复杂,内容多
  + pc端:京东 www.jd.com
  + wab端: 京东 www.m.jd.com
  + 以m/i为开头的,都是移动端的网站
+ pc端和移动端共用一套项目,一个域名.被称为**响应式布局**
 + 结构简单,内容少
 + 苹果官网 华为 猎豹 摩拜...

### pc端和移动端的区别
+ 效果
 + PC端:hover 伪类选择器
 + 移动端：没有鼠标经过的效果，有滑屏切换的效果

+ 浏览器
 + PC端：谷歌、火狐、IE(7-11) CSS hack 解决页面的兼容性问题
 + 移动端：-webkit- 内核(高版本浏览器)，需要适配所有机型(iphone4/4s/5/5s/6/6s/6Plus)
### html5新增标签
标签	描述
header	头部
footer	尾部
nav	导航
aside	侧边栏
video	视频
audio	音频
article	文章
section	区分大模块
figure	配图
figcaption	配图说明

### 音视频

+ video 视频 audio 音频
+ src=”” 路径、地址
+ autoplay 自动播放
+ controls 控件是否显示
+ loop 循环播放
`<video src="dongbei.mp4" autoplay controls loop></video>`

HTML5新增标签是块级元素的有哪些？
header/footer/nav/artcile/section/aside/figure/figcaption

HTML5新增标签是行内块级元素的有哪些？
video/audio

### 如何让HTML5新增标签兼容低版本(IE7/8)浏览器
直接引入这个html5.js文件即可
```
<!--[if lt IE 9]>
<script src="html5.js" type="text/javascript"></script>
<![endif]-->
```

## 媒体查询
```
    @media all and (max-width:600px){}
    <!-- 注意:单词之间空格隔开 -->
```
+ 1.@media 媒体 媒介
+ 2.媒体类型
 + all 所有类型
 + screen 设备类型
+ 3.连接符 and
+ 4.判断条件()
 + max-width:600px 最大宽度600,小于等于600
 + min-width:600px 最小宽度600,大于等于600
+ 5.{}css样式代码


## 移动端需要适配那些手机机型?
+ iphone5/5s 320
+ iphone6/6s/7/7s/8/8s/x/xr 375
+ iphone6plus 414

## viewport 视口
> html页面的宽度等于设备的宽度(不加这句话,默认是980)
> Vscode默认生成这句话,换成其他编辑器,需要手动加这句话
`<meta name="viewport" content="width=device-width, initial-scale=1.0">`

## 做响应式项目有那些步骤?
+ 加viewport 视口
+ 写html结构
+ 写css样式
 + reset.css
 + index.css
  + 先写pc端,再写移动端
  + 移动端css样式(媒体查询,条件给一个范围值)
   + `@media all and (max-width:600px){}
> 移动端没有版心
> 移动端的css样式要比pc端css样式权重大或者相等

## REM布局
rem=root element 根元素
```
rem是为了获取根元素(html)的fontsize值

参照iphone5/5s 320
html{
    font-size:100px;
    /** 1rem=100px **/
}
iphone6/6s/7/7s 分辨率：375
@media all and (min-width:375px){
    html{
        font-size: 117.1875px;
    }
}
iphone6Plus 分辨率：414
@media all and (min-width:414px){
    html{
        font-size: 129.375px;
    }
}
```

**移动端最终版**
> 因为设计稿的尺寸是乘两倍，所以整体让font size缩小一半

```
/* iphone5/5s 320 */
html{
    font-size: 50px;
    /* 1rem=100px */
}
/* 375 */
@media all and (min-width:375px){
    html{
        font-size: 58.59375px;
    }
}
/* 414 */
@media all and (min-width:414px){
    html{
        font-size: 64.6875px;
    }


**参照iphone6/6s 分辨率：375  750**
```
/* iphone6/6s 375 */
html{
    font-size:50px;
}
/* 375 */
@media all and (min-width:320px){
    html{
        font-size: 42.66px;
    }
}
/* 414 */
@media all and (min-width:414px){
    html{
        font-size: 55.2px;
    }
}
}
```
### 移动端设计稿的尺寸
+ 参照iphone5/5s 分辨率：320*2 设计稿的尺寸是640
+ 参照iphone6/6s 分辨率：375*2 设计稿的尺寸是750