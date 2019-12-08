# jQuery
 > jQuery是一款用原生js封装的，操作dom的类库，他里面封装这大量的方法，基于这些方法，可以使我们快速的去操作dom和构建我们的项目

## jQuery的基础
 > 如何学习它
  1. 看api(说明书)  http://jquery.cuishifeng.cn/index.html
  2. 做案例
  3. 看源码 (可以提高你自己封装插件的能力，也可以提高你阅读其他代码的能力)
 > jQuery的版本：
  + v1.xxx:它可以兼容所有的浏览器，所以他一般用在兼容浏览器的pc端页面(这是用的最多的版本)
  + v2.xxx:它支持移动的操作，但是2版本刚出生就死掉了，因为它生不逢时，这时候就有了zepto
  + v3.xxx变化不大，但是也没有火起来，因为jQuery是操作dom的，但是在这时，市场上一些主流的框架(vue、react开始逐渐火爆起来)，vue和react不直接操作dom(生不逢时)

## jQuery的语法
 1. 获取dom的方式
    + $('选择器')  jQuery选择器
    + eq(索引)  找到索引对应的元素
    + gt(索引)  找到大于索引对应的元素
    + lt(索引)  找到小于索引对应的元素
    + find('选择器')  找到对应的后代元素
    + filter('选择器')  把符合条件的过滤出来
    + 如果你是用jQuery获取的东西，那变量接收时，那这个变量名前一般加上$，这是大家约定俗成的规范，别人一看就知道你是用jQuery获取的
```
let $box = $('#box')
$('.box li').eq(0)
$('.box li:gt(2)')
$('.box li:lt(2)')
$('.box').find('li').filter('.active')
```

 2. 节点之间的属性
    + prev() 获取上一个同辈元素
    + prev('span') 获取上一个标签名为span的同辈元素
    + prevAll() 获取当前元素之前所有的同辈元素
    + next() 获取下一个同辈元素
    + next('span') 获取下一个标签名span的同辈元素
    + nextAll 获取当前元素之后所有的同辈元素
    + parent() 获取父亲元素
    + parents() 获取所有的祖先元素
```
$('.box').prev() //获取上一个同辈元素
$('.box').prev('span') //获取上一个标签名为span的同辈元素
$('.box').prevAll() //获取当前元素之前所有的同辈元素

$('.box').next() //获取下一个同辈元素
$('.box').next('span') //获取下一个标签名为span的同辈元素
$('.box').nextAll() //获取当前元素之后所有的同辈元素
$('.box').siblings() //获取所有的同辈元素

$('.box').parent() //获取父级元素
$('.box').parents() //获取所有的父级元素，直到document
```

 3. dom的增删改
    + $('.box').append('<p>333</p>') //往指定的元素末尾插入元素
    + $('.box').html() //获取innerHTML内容
    + $('.box').html('2222') //设置innerHTML内容
    + $('.box').text() //获取innerText内容
    + $('.box').text('2222') //设置innerText内容

 4. 自定义属性
    + $('.box').attr('data-time') //获取自定义属性
    + $('.box').attr('data-time'，11) //设置自定义属性
    + $('.box').attr({
        'data-type':1,
        'data-time':2,
     }) //设置一组自定义属性
    + $('.box').removeAttr('data-time') //移除自定义属性

 5. css
    + $('.box').css('width') //获取css样式
    + $('.box').css('width',100) //设置css样式
    + $('.box').css({
        width:100,
        height:100
     }) //设置一组css样式。
    + $('.box').addClass('active') //添加指定的类名。
    + $('.box').removeClass('active') //删除指定的类名
    + $('.box').hasClass('active') //检测当前元素是否拥有当前的class名，如果有就是true，没有就是false
    + $('.box').toggleClass('active') //自动判断当前元素是否拥有这个class名，如果有就是删除，没有就是增加

 6. js盒子模型
    + $('.box').offset() //和咱自己封装的一样，距离body的上、左偏移量，这个方法只对可见元素有效
    + $('.box').position() //获取父级参照物

 7. 工具、事件
    + box.onclick = fn;
      - $('.box').on('eventType',fn) //增加事件
      - $('.box').on('click', fn)
      - $('.box').click(fn) //点击事件
      - $('.box').off('click',fn) //移除事件
    + forEach
      - $('.box li').each(function(index,item){})
        //可以遍历数组，类数组，对象
        //index是每一项的索引
        //item是每一项
        //如果遍历的是对象，那index是属性名，item是属性值
    + $('.box li').toArray() //转数组
    + $.uniqueSort() //数组的去重排序