+ "use strict"; 严格模式

+ alt+f 格式化

+ try catch 如果try中的代码报错了，那么就会立即执行catch中的代码；不会影响下面的代码执行  如果不报错，那么就不走catch

+ alert 的结果都要加''，弹出的值都是字符串
  
+ alert alert会在浏览器描绘dom之前执行
  
+ 等号赋值都是三步 1.创建变量 2.创建值 3.关联
  
+ 属性值一定得是数据类型的一种，不然就报错
  
+ console.log(name) 不报错，虽然name不是数据类型的一种但是windom中有个name的属性名，属性值是空字符串
  
+ DOM 树--> CSS树---> render树 --> pait(描绘)
  
+ debugger 断点：让代码执行停止到这一行
  
+ 在代码执行的过程中，遇到函数直接跳过，因为在变量提升时函数已经赋值了
  
+ 当函数执行的时候，才会对函数体中的代码进行变量提升
  
+ 支持es6的浏览器，会把这个if的大阔号解析成一个块级作用域；
  
+ 在全局作用域下定义的函数，也会给window新增键值对；属性名是函数名，属性值时函数的空间地址；
  
+ 如果属性的属性值是一个自执行函数，那么当代码以键值对储存的时候(当代码执行到这一行时，自执行函数就会运行)，并且把自执行函数的执行结果赋值给属性名
  
+ 如果变量名重名，不再进行重复声明，但是要重新赋值
  
+ function add(){}这种写法叫做函数声明      var add=function(){}这种写法叫做函数表达式      function(){}这种是匿名函数  
    
+ 函数声明和匿名函数自执行需要加()或+或-或!
  
+ Object.keys()  :将对象中所有的属性名放到一个数组中

+ Object.values() :将对象中所有的属性值放到一个数组中
  
+ 
```
num = 1;
let a = num++;
console.log(a); //1
//a=1  num=2  先赋值再运算
```

+ let 声明变量在for循环中，每一轮循环都会形成一个自作用域(块级作用域)，

+ 函数每执行一次，都会形成一个新的栈内存；

+ setAttribute(attributename,attributename) 方法添加指定的属性，并为其赋指定的值。
    属性可以是自定义的属性，如果这个指定的属性已存在，则仅设置/更改值

+ getAttribute(attributename);获取某个属性的值；返回值为string类型
    注：attributename，value都是字符串类型
 
+ 一个函数的参数是另一个函数的执行，那么就说另一个函数(执行的函数)是函数的回调函数

+ this不能放在等号左边

+ jquery的源码的外层就是采用了这种高级单例的模式；

+ 用取整要加10进制  parseInt(a,radix:10);

+  <textarea type='text' id="num1">输入数字</textarea>  实时获取文字方法  名字.value

+ 在全局作用域中存在n，windom中也存在n，会先找全局，再找windom

+ eval可以将字符串去掉，让里面的表达式运行

+ 在call的内置方法中，会校验call的this是否是一个函数，不是则不会运行

+ window.onscroll 页面划过就会触发

+ newImg.onload=function(){} onload 事件：当图片加载成功之后，会执行该函数，如果路径不成功，该函数不执行；

+  box.onmouseover = function () {}  移入事件

+ box.onpointerout = function () {}  移出事件