# js笔记


## web前端发展史
- web1.0时代(2013)：网页制作
- web2.0时代
  + 弱前端时代(服务器渲染)
  + 客户端渲染
- 全面进军移动端
- node.js

## 浏览器
- 打开控制台(f12, 右击、检查元素, ctrl+shift+j/i(谷歌))
- Elements: 显示页面中的结构和样式(还可以临时修改)
- Console: 可以运行代码，可以打印页面中代码的内容
- Sources: 存放的是页面的静态资源文件
- Network: 里面是所有的数据请求

# 浏览器的分类
QQ、360、火狐(FireFOX)、谷歌(Chrome)、IE、朋克(Opera)、safair
- webkit(v8引擎)
  + Chrome
  + safari
  + 手机浏览器
  + 国产浏览器
- Gecko
  + FireFox
- Prosto
  + Opera
- Trident
  + IE
  + IE EDGE (Chrome mini)

## js
> js作为一门客户端开发语言，不仅要操作浏览器的某些功能，还要操作页面中的dom元素
- ECMAScript3/5(老版本) (6/7)新版本：规定了js的语法、变量、操作语句等
- DOM: (document object model)提供一些js的属性和方法，用来操作页面中的dom元素
- BOM: (browser object model)提供了一些js的属性和方法，用来操作浏览器

## js创建变量的几种形式
- 1、var 创建一个变量
- 2、let 创建一个变量
- 3、const 创建常量(不允许被修改) （es6）
- 4、function 创函数变量
- 5、import 导入
- 6、class 创建类
- 7、symbor 创建唯一值

## js中的命名规范
- 严格区分大小写
- 变量名由数字，字母，$，_组成，不能以数字开头
- 遵循驼峰命名法(变量名的第一个单词首字母小写，以后每一个有意义的单词大写) (起的变量名一定要有意义)
- 不能以关键字或者保留字作为变量名

## js的数据类型
- 基本数据类型
  + number 数字类型 2，1.2，-2，+4
  + string 字符串'' "" ``
  + boolean 布尔(判断) true false
  + null 空对象指针
  + undefined 未定义
- 引用数据类型
  + objest 对象
    + 普通对象 {nam................e:'xxx'} object
    + 数组 [] array                                                                                                       
    + Math 数学对象
    + Date 日期对象的实例
    + /^$/ 正则
  + function 函数 
> 有效数字 3，5.5 ，-4.4，0，+7
> NaN (not a number)不是一个数，但是它是number的一种数字类型

**NaN和谁也不相等（包括自己）**

 ### 把其他数据类型转数字类型 Number(val)
    - 把字符串转数字：
        + 只要字符串中出现了非有效数字，那结果就是NaN（第一个小数点不算，第一个-、+不算）
        +  如果左右有空格，会自动去掉(中间的空格不会去)
        +  空字符串转数字是0
        +  不改变原参数，返回一个新的数字

    - 把布尔转数字
        + true转数字是1
        + false转数字是0
    - 把null和undefined转数字
        + null转数字是0
        + undefined转数字是NaN

    - 把对象还转数字

        + 把普通对象转数字，先把值转换为字符串，在把字符串转换为数字
            + 所有的普通对象转字符串都是 '[object Object]'
            + 所有的普通对象转数字都是NaN
            
        + 把数组转数字先把值转换为字符串，在把字符串转换为数字
            + 数组转字符串=> 把中括号去掉，然后把数组的每一项都去做toString处理，然后拼接到一起  (，不能丢)


# number
## parseInt(val)和parseFloat(val)
    > (系统默认)把字符串转换为数字
    > 从左到右依次查找有效数字，一旦发现非有效数字，立即停止查找，把找到的数字返回出去（paeseInt不可以识别小数点，parseFloat可以识别小数点）
    > 如果你要转换的值不是字符串类型的，先转换为字符串类型，在查找
    > true、false、null、undefined、{}、NaN 转都是NaN
    > (系统默认)数组是先转换为字符串，在进行查找
```
 let num = '3.141.5926';
    console.log(parseInt(num)) // 3
    console.log(parseFloat(num)) // 3.141
    let s = true;
    console.log(parseInt(s)) // 'true' // NaN
    
    console.log(parseInt([])) // '' NaN
    //因为数组不是字符串所以会把数组转成字符串，但是不会继续把字符串转化为数字，从左到右空数组没有有效数字，所以为NaN
    
    console.log(parseFloat({})) // '[object Object]' NaN
    // 因为普通对象不是字符串所以要把普通对象转成普通对象，普通对象转字符串固定为'[object Object]',从左到右没有有效数字，所以为NaN
```

## isNaN(val)
> 检测一个值是否是一个非有效数字，如果是就是true，反之就是false
    (这个值如果是有效数字，那结果就是false，反之就是true)
> 如果你要检测的值不是数字类型的，(系统默认)先转换为数字类型，在检测
```
 console.log(isNaN(3)); // false
        console.log(isNaN(NaN)); // true
        console.log(isNaN(true)); // console.log(isNaN(1)) --> false
        console.log(isNaN(false)); // console.log(isNaN(0)) --> false
        console.log(isNaN(undefined)); // console.log(isNaN(NaN)) --> true

        console.log(isNaN( Number(isNaN(NaN)))); //console.log(isNaN( Number(true))) --> console.log(isNaN( 1)) --> false

        console.log(isNaN(Number(parseFloat(isNaN({}))))); // console.log(isNaN(Number(parseFloat(true)))) --> console.log(isNaN(Number(NaN))) --> console.log(isNaN(NaN)) --> true
```

# string 字符串
> 所有 单引号、双引号、反引号(ES6的模板字符串)包起来的都是字符串 
## val.toString()      字符串拼接

### val.toString() 
    > 把number、boolean（true，false）转字符串都是直接加引号
    > null 和undefined不能使用toString方法
    > 把普通对象转字符串 =>  '[object Object]'   (把普通对象转字符串 普通对象要拿小括号包起来)
     > 数组转字符串=> 把中括号去掉，然后把数组的每一项都去做toString处理，然后拼接到一起  (，不能丢)
    ```
    <script>
    console.log([true, false].toString()); // 'true,false'
    //数组中的每一项都要变成字符串然后拼接在一起

    console.log(1+[{}]); // 1+ '[object Object]' -->'1[object Object]'

    console.log([{}, []].toString()); // '[object Object],'

    console.log([null, undefined].toString()); // ','

    console.log([{} , {}] .toString());//'[object Object], [object Object]'
    </script>
    ```
    ```
    <script>
        /* 1.string
        把number、boolean、(true，false)转字符串都是直接家引号
        (1) val.toString() */

        console.log((1).toString()); // '1'
        //数字要加括号，因为怕点和小数点混淆，所以加括号区别

        console.log((3.1415962).toString()); // '3.1415962'

        console.log(true.toString()); // 'true'

        console.log(false.toString()); //'false'

        console.log(null.toString()); // 报错
        console.log(undefined.toString()); // 报错
        //空对象指数和未定义为空，所以无法转字符串

        console.log(''+null); // 'null'
        //这是加法运算，空字符串''+空对象指数null，加号和''相遇会发生字符串拼接

        console.log([].toString()) // ''
        //因为[]转字符串直接换成''

        console.log(({}).toString()); // '[object Object]'
        //{}转字符串固定为'[object Object]'  数字和普通对象{}必须加括号，普通对象如果不加括号会和函数混淆
    </script>
    ```



### 字符串拼接
    > 四则运算：在四则运算中，除了加法，其余的都是正常的运算
    > 在运算中过程中，如果相运算的值不是数字类型的，先转为数字类型，在运算
    > 在运算过程当中，如果出现了NaN，那结果就是NaN

    > 在加法中有两种情况:
        + 正常运算
        + 字符串拼接：如果加号一旦跟引号相遇了，那就是字符串拼接，不再是正常的运算(基本数据类型的这样的)
        + 如果拼接的过程当中，引用数据类型要转数字（一旦字符串和加号相遇了，就是字符串拼接）

(拼接时顺序为从左到右不能更改出现的顺序)

(在字符串拼接时要注意，比如console.log([ ]+[ ]);  数组转数字时要先转为字符串 就会形成' ' + ' ' , 这个时候就会出现字符串拼接 而不是转成数字再运算)

(当字符串拼接时，像数组[ ]，普通对象{ }要先转换为字符串然后再开始拼接)
```
 console.log(true+true); // 1+1=2
     //因为true转数字为1，所以为2

     console.log(undefined + true); // NaN+1=NaN

     console.log(1 + true + null + undefined + 35 +null) // NaN
     // 运算结果中出现了NaN  结果就是NaN

     console.log(1 + 'wer'); // '1wer'

     console.log(true + '1'); // 'true1'

     console.log(1 + true + null + undefined + 'erya' + true); // console.log(NaN + 'erya' + true) --> console.log('NaNerya' + true)   --> 'NaNeryatrue' 
     //因为运算的顺序为从左往右，并不是同时进行，所以在'NaNerya'+true的时候 ''和+先相遇所以直接拼接而不是转为数字再拼接

    console.log(1 + true + null + undefined + 'erya' + [] + {}) // console.log(NaN + 'erya' + [] + {}) --> console.log('NaNerya' + [] + {}) --> console.log('NaNerya' + {}) --> console.log('NaNerya' + '[object Object]') --> 'NaNerya[object Object]'
    // 当字符串拼接时，像数组[]，普通对象{}要先转换为字符串然后再开始拼接

    console.log(1 + []); // console.log(1 + '') // '1'

    console.log({} + NaN); // console.log('[object Object]' + NaN)  //'[object Object]NaN'
    
    console.log(true + 10 / true + []) //--> console.log(true + 10 + []) --> console.log(11 + []) --> console.log(11 + '') --> '11'

    console.log(true - [11]); // 1-11
    //注意只有加法才会字符串拼接，减法乘除不会
```

## boolean布尔 (true false)
> > 把其他数据类型转布尔 Boolean  !/!!
- Boolean(val)
    + 把其他数据类型转布尔有且只有NaN、null、undefined、0、''这五种是false，其余的都是true
    + 把布尔转布尔还是本身

    ```
    <script>
        // 把其他数据类型转布尔有且只有NaN、null、undefined、0、''这五种是false，其余的是true

        console.log(Boolean(true)); // true
        console.log(Boolean(false)); // false
        //因为布尔boolean转布尔还是本身

        console.log(Boolean(NaN)); // false
        console.log(Boolean(null)); // false
        console.log(Boolean(undefined)); // false
        console.log(Boolean(0)); // false
        console.log(Boolean('')); // false

        console.log(Boolean('    ')); // true 
        //空字符串''转布尔为false，但'   '其中有空格不为空字符串，所以为true

        console.log(Boolean([])) // true
        console.log(Boolean({})) // true
   </script>
    ```


    - !/!!
        + !:把其他数据类型转布尔，然后取反
        + !! 把其他数据类型转布尔，然后取反再取反
        ```
     <script>
         console.log(!null) // true
        console.log(!0) // true
        console.log(!11) // false
        console.log(!!null) // fasle
     console.log(!!11) // true
     //单个！是把其他数据类型转布尔，然后取反； ；两个！是把其他数据类型转布尔，然后取反再取反，相当于转布尔

     if(!!0){
         console.log(111);
         //括号里的东西会转布尔，如果是true就执行大阔号里的代码，反之就不执行
     }
    </script>
        ```
       

## null和undefined
> 他俩都代表空
- null：他一般都是意料之中的（一开始我们不知道值，先手动赋值为null，但是以后知道了，再给他重新赋值）

```
// 一开始我买了一辆夏利，但是有邮箱里没有油，我先给他手动赋值为null，经过我几个月的努力，我挣钱了，我拿着5毛钱买了一升油，现在我在给邮箱赋值为1
let gasoline = null;
    gasoline = 10000;
```
- undefined：他也是空，但是一般都是浏览器的默认机制定义的(意料之外的)
    // 获取属性名所对应的属性值获取不到就是undefined
    // 如果属性名重复，那下面的会覆盖上面的
```
// 孙悟空本身就没有父亲，他是石头缝里蹦出来的，但是你还是去找他的爸爸，这就是意料之外的事，找不到就是undefined
// 猪无能我们大家都知道有父亲，但是不知道具体是哪头猪，先说动赋值为null；
经过我五个月的打听，张岩告诉我了，他的父亲是隔壁村的老母猪的对象小花，然后我再把小花重新赋值给猪无能的父亲
let pigFather = null;
    pigFather = 'xiaoHua';
    console.log(pigFather)
```
# 引用数据类型（[],{}）
- 每一个对象都由大括号包裹，里面是0到多个键值对组成，而且拿逗号隔开
- 每个键值对由属性名和属性值组成（中间拿冒号连接）[key:value]
- 属性名是由字符串和数字组成（''可以省略）
- 属性值就是js数据类型一种

- 增删改查
    + 查询属性名所对应的属性值：
        对象名.属性名/对象名['属性名']；如果属性名是数字，不能用对象名.属性名的方式去获取对应的值
    + 新增和修改   对象名.属性名 = 'xxx'
        新增的属性名如果存在，就是修改属性值，如果没有就是新增
    + 删除
        + 假删除   对象名.属性名 = null;
        + 真删除   delete 对象名.属性名
（以上的操作 “对象名.属性名”都可以改为对象名['属性名']；两种方式，用哪个都可以）
## 普通对象
> 对象的定义
  1. 开辟一个堆内存；这个堆内存对应十六进制的地址
  2. 把对象中的键值对储存到堆地址中
  3. 把这个空间地址赋值给变量名 
```
<script>
        let monkey = {
            'name': 'sunWuKong',
            'age': null,
            'speed': 10000,
            'ifantName': 'badMonkey',
            3: 'xxx'
        };
        console.log(monkey);
        
        console.log(monkey.name);
        console.log(monkey['name']);
        //意思是显示变量monkey中普通对象属性名为name的值，以上两种写法都可以

        console.log(monkey[3]);
        console.log(monkey['3']);
        //意思是显示变量monkey中普通对象属性名为3的值，当属性名为数字的时候只能用中括号的方式，中括号中的引号可有可无

        monkey.ss = '3333';
        monkey.speed = '6666';
        //对象名.属性名 = 'xxx' 新增的属性名如果存在，就是修改属性值，如果没有就是新增

        monkey.name = null;
        //这是假删除，用空对象指针null替换了原来的名字

        delete monkey.name;
        //这是真删除，monkey中的name将消失

        let a = 12, b = 13;
        let a = 12; let b = 13;
        // 这两个是相同的
 </script>
```

## 数组 []
> 数组由中括号包裹，里面存放的是每一个属性值，属性名是浏览器内定的，从0开始，依次递增，他代表属性值的位置=>索引
> 天生自带一个length属性，属性值是数组的长度

```
<script>
        /* > 数组由中括号包裹，里面存放的是每一个属性值，属性名是浏览器内定的，从0开始，依次递增，他代表属性值的位置 => 索引
        > 天生自带一个lenght属性，属性值是数组的长度 */

        let ary = ['2',2,true,false,null,undefined,{},[]];
        console.log(ary);
        console.log(ary.length);

        console.log(ary[0]);
        //获取数组第一项

        console.log(ary[ary.length-1]);
        ary.length--
        //获取数组最后一项

        console.log(ary[ary.length]='sss');
        //给数组新增一项属性值为sss 属性名为原有的lenght值加1的项

        console.log(ary.length-1);
        //删除最后一项

        // ary.length = 0;
        //删除全部项

        console.log(ary[2]);
        //获取第三个属性值
    </script>
```


## 数字类型比较
    > == ： 是两个值进行比较，会默认进行数据类型之间的转换再比较；比较的结果是一个布尔值
    
    1. 数字 ==字符串 字符串调用Number转换成数字，然后和数字进行比较；

    2. 数字 ==布尔  布尔转数字，然后进行比较

    3. 数字 == 对象（对象数据类型） 对象先转成字符串，然后再转成数字；

    4. 对象==对象 比较的是空间地址，空间地址不同，就false；

    5. 对象==字符串 :对象转成字符串，然后进行比较

    6. 对象==布尔 : 对象转字符串，字符串转数字，布尔直接转数字，然后进行比较；

    7. 布尔==字符串  : 布尔值转数字 字符串转数字

    8. null == undefined  : true

    9. NaN ==NaN  : false

    10. null == 0  : false

    11. undefined == 0 : false

```
<script>
 // 1.数字==字符串  字符串调用Number转换成数字，然后和数字进行比较；
        console.log(1 == '1'); // true

        console.log(0 == '');  // true

        console.log(1 == '1px'); // console.log(1 == NaN) => false

        console.log(1 == '[1]'); // console.log(1 == NaN) => false

        // 2. 数字==布尔  布尔转数字，然后进行比较
        console.log(1 == true);  //  console.log(1 == 1) => true

        console.log(0 == false);  //console.log(0 == false) => true

        // 3.数字 == 对象 (对象数据类型) 对象先转成字符串 然后转成数字
        // NaN 和自己不相等
        console.log(NaN == {}); //  console.log(NaN == NaN) => true

        // 4. 对象==对象 比较的是空间地址，空间地址不同，就false；
        // 在JS中，只要遇到{}，就会开辟一个新的空间地址
        //当浏览器解析代码时，会形成两个虚拟的内存，分别是栈内存和堆内存
        // 栈内存提供代码的运行环境，并且储存基本数据类型值
        //堆内存存储引用数据类型的值；
        //(如果空间地址相等那么对象也可以等于对象，但是如果空间地址不相等，那么即使对象内容完全一致也不会相等)

        let c = 100;
        let a = {};
        let b = {};
        console.log(a == b); // console.log(({}) == ({}));  => flase

        console.log([] == []); // flase

        //5. 对象 == 字符串 :对象转成字符串，然后进行比较
        console.log(({name:1}).toString()); //'[object Object]'
        console.log('' == ' '); //false
        // 空字符串和字符串加空格不相等，空格算字符

        // 6.对象==布尔：对象转字符串，字符串转数字，布尔直接转数字，然后进行比较；
        //!:先将后面的值转为布尔值，然后再取反；
        console.log([] == false); // true

        console.log(![] == false); // true
        // 有！直接转布尔值，然后再转数字

        console.log([] == ![]); //console.log(0 == false) => console.log(0 == 0) => true

        console.log([] !== []); //true
        //这是对象转对象所以不等于是对的   !==是不等于的意思

        //7.布尔==字符串：布尔值转数字 字符串转数字
        console.log(false == ''); //true

        console.log(true == '1px'); //false


 </script>
```

## 三个判断
  + function 判断语句 循环语句
    三个判断：
    1. if else
       > 逻辑且：&&左右两边都成立，这个条件成立；只要左右两边一个是false，整体结果就是flase。     
	     &&：如果前边的值转布尔是true，那就取后面的值，如果不是就反之，取前面的
	         
       > 逻辑或：|| 只要左右两边有一个成立的，整体结果就是true
         || ：如果前面的值转布尔是true，那就取前面的值；false就取后面的值
            
       > %：取余数
       > += / -=
            
    2. 三元运算符
    3. switch case

    + 等号的含义
     = : 赋值

     == : 会比较值是否相同，返回一个布尔值；会默认进行数据类型之间的转换

     === : 绝对比较，会比较数据类型和值；不进行数据类型转换，只要数据类型不一样或者值不相同，返回false

1. if else;
    ```
        if (条件) {
            条件成立执行的代码
        }else{
            条件不成立执行的代码
        }

        (1).如果条件括号中只有一个值，会默认转布尔值；
    
    let obj = {age:10};
        //如果在对象中，属性名不存在，那么获取的属性值永远是undefined；
        if (obj.name) {
            console.log(100);
        }else{
            console.log(200);
        }
        //最后输出的是200，因为obj.name这个条件中obj对象名中没有叫name的属性名，所以条件为undefined，条件括号只有一个值就转布尔为flase，条件不成立执行下面的代码
    ```

2. 三元运算符：适合简单的if else；
        ```
        // 构造： 条件 ？ 条件成立执行的代码 ：后面是不成立执行的代码；
        []==false ? console.log(100) : console.log(200);

        //多个判断时
        []==false ? ([]==[]?console.log(100):console.log(200)): console.log(300);
        ```

3. switch case
    ```
        switch (num) {
            // num会和case后面的值进行绝对比较
            case '100':
                // 当条件成立时就会输出这个值
                console.log(100);
                // break为中断代码执行，到这里停止，如果switch不加这个命令的话会输出下面的所有结果
                break;
		    case 1:
                console.log(200);
                break;

	        // default为以上所有比较结果都为false时输出
             default:
                console.log(300);
                break;
       };
        
        let num = 80;
        switch (num) {
            case 80:
            case 200:
              console.log(999);
        };
        // 输出结果为999，因为没有加break所以会输出下面全部的结果，但是如果加上break的话就不会输出
    ```

## 元素
> 在html中叫标签，在js叫元素；js中的元素都是对象数据类型的；
   + 要想操作谁，就要先获取谁
   + document.getElementById: 在document文本下，通过id获取元素
        document: 上下文文本
        get:获取
        Element:元素
        By:通过
        Id:id名
```
<body>
    <div id="box" style="background: red;"></div>

    <script>
        let div1 = document.getElementById('box');
        div1.onclick = function () {
            // 这里面的元素不会运行；当点击元素的时候，这个函数就会执行。 因为onclick（事件函数），它的意思是点击这个元素开始干什么
            if (div1.style.background==='red') {
                div1.style.background==='black';
            }else{
                div1.style.background==='red';
            }
            console.log(div1.style.background);
        }
        //点击盒子变色
    </script>
</body>
```

> 三个循环：for、 for in、 while
 1. for循环
    四部曲：
    1. 初始化一个变量i=0；
    2. 判断条件是否成立；
    3. 执行循环体；
    4. 执行i++   (i++:在自身基础上+1，是先取值在运算，意思是先循环然后再加1；    ++i：在自身基础上+1是先运算再取值，意思是先加1再循环)
        for循环的过程： 1-->2-->3-->4-->2-->3-->4
        当条件不成立时，中止循环；
		> break 终止代码运行
        > continue 中止本轮循环
		> 逻辑且：&&左右两边都成立，这个条件成立；只要左右两边一个是false，整体结果就是flase。
        > 逻辑或：|| 只要左右两边有一个成立的，整体结果就是true
```
/*  let arr=[100,2,7,8,3,4,5];
        for (let i = 0; i < arr.length; i++) {
            console.log(i);
            
        };
        // 输出结果为6，因为i++为先循环再加1当到了第七次是，7=7，停止循环所以为6

        let a=100;
        let b= a++;
        console.log(b); //输出为100
        //因为a++为先运算再赋值，在输出后加1
        let a = 100;
        let b = ++a;
        console.log(b); //输出为101
        //因为++a为先赋值在输出，所以加1在输出

        let i = 1;
        console.log((i++)+(++i)); // 4
        // 1+2+1 --> 4 */

        let a = 10;
        console.log(a -= 1); // 9
        console.log(a); // 9
        //a -= 1的意思是 a-1=a

        // 求1-10000的和
        let total = 0;
        for (let i = 0; i < 10001; i++) {
            total+=i;  
        };
        console.log(total);
        // i为每次需要加的数，total为已经加的数的和 结果50005000

        for (let i = 0; i < 6; i++) {
            if (i>4) {
                break;
            }
            console.log(100); //5
            // 因为5大于4所以到5的时候运行break会终止代码的运行
        }

        for(let i=0; i<6; i++){
            console.log(100);
            continue;
            console.log(200);
        } //100
        // continue:终止本轮循环，continue下面的代码不执行；

        for(var i=0; i<11; i++){
            if(i<5){
                i+=1
                continue;
            }  //6
            if(i>8){
                i+=2;
                break;
            } //12
            i+=1; //10
        }
        console.log(i);  //  12


        /* 逻辑且：&& 左右两边都成立，这个条件成立；只要左右两边一个是false，整体结果就是flase。 */
        if(1=='1' && 2=='2'){
            console.log(100);
        }; // 100

        if(1=='1' && 2=='ajd'){
            console.log(100);
        }; // 只要有一个错了就不会输出任何值

        /* 逻辑或：|| 只要左右两边有一个成立的，整体结果就是true */
        if(1==true || 2==3){
            console.log(200);
        } // 200
```
  
 2. while 循环
    (1). 当不知道循环多少次时，会使用到while；
    (2). while 阻塞线程；
    ```
    let num = 10;

    while(num>5){
    console.log('s'); // 's'
    <!-- num-- -->
    }   
    ```

 3. for in (一般用来对象)循环
    + 会把对象中属性名是数字的先输出，并且按照从小到大的顺序输出
    + 在for in里获取每一项属性名所对应的属性值，必须用obj[key]的形式 
    + 每一项属性名对应的属性值  
    + for in可以遍历出公有属性和私有属性

```
let obj = {
    name: name,
    age: 'age',
    name: 'name',
    3: 'erYa'
};
// (key:value)  一般key代表属性名 value代表属性值

for(var key in obj) // 属性名为obj{
    console.log(key) // 每一项的属性名
    // 在for in里获取每一项属性名所对应的属性值，必须用obj[key]的形式 
    console.log(obj[key]) // 每一项属性名对应的属性值  
}
```
 4. for of
> 循环数组或者类数组的每一项值
```
let ary = [1, 2, 3, 4, 1, 1];
let ary1 = new Set([100, 200, 300, 4, 1, 1]);
      
for (let key of ary1) {
    console.log(key); //数组的成员，可以和set搭配使用
} 
for (let key of ary.values()) {
    console.log(key); //数组的成员
}
for (let key of ary.keys()) {
    console.log(key); //循环数组的索引
}
for (let key of ary.entries()) {
    console.log(key); //循环数组的成员和索引 放在一个空数组里
}
```


# 2、数据类型检测
- typeof 检测数据类型的属性
- instanceof 检测当前实例是否属于某个类
- constructor 基于构造函数检测数据类型
- Object.prototype.toString.call()：检测数据类型最好的方式 他的返回值是一个字符串，里边是'[object 你当前实例的所属类]'，不能检测基本数据类型

## typeof 检测数据类型的属性
- 他的返回值是一个字符串
- 字符串里存放的就是他的数据类型
- typeof 检测数组、普通对象、null返回的都是'object',所以用typeof检测数据类型无法细分出普通对象、数组、null
- 只要超过两个typeof，那最后的结果就是 'string'

```
    console.log(typeof 12) // 'number'
    console.log(typeof '12')// 'string'
    console.log(typeof undefined) // 'undefined'
    console.log(typeof true)  // 'boolean'
    console.log(typeof null) // 'object'
    console.log(typeof []) // 'object'
    console.log(typeof ({})) // 'object'

    // 只要超过两个typeof，那最后的结果就是 'string'
    console.log(typeof typeof typeof 12) // 'string'
```

# 3、元素也是对象
- style：操作的是元素的行内样式
- className：操作的是元素的class名
- innerHTML：操作的是元素的内容（可以识别标签）
- innerText：操作的是元素的内容（不可以识别标签）

# 4、函数
    - 函数就是一个方法，把实现某些功能的代码封装到一起，以后执行这个方法，就直接运行函数就好了，他可以减少页面重复的代码，提高代码的复用率（高内聚低耦合）
    
    - （创建函数）[ 函数创建的小括号里放的就是形参变量,实参跟形参是一一对应的]，（把实现某些功能的代码封装到一起），（在函数里叫形参变量），
    （在函数里叫return）

    - （函数执行）[函数名加括号就是函数执行,函数执行的时候，传的是实参]，（在函数运行时放的变量就是实参）

    + 出现undefined的情况
        + 出现变量没有赋值，获取这个变量是undefinde
        + 获取对象里的属性名所对应的属性值获取不到，是undefinde
        + 函数里实参没有给形参变量赋值，是undefinde
        + 函数里，没有return（没有返回值），函数执行结果是undefinde

    + null的情况
        + 手动赋值为null
        + 通过id去获取元素获取不到，那就是null

```
 函数表达式
      let fn = function(n,m){
          console.log(n,m) // undefined undefined
      }

		   console.log(fn()) // undefined

 自执行函数
         (function(m){
             console.log(m)
	        })(1)
	      //括号里的数就是实参
``` 

# 1、讲解函数的运行原理（画图）
- 外边拿不到函数体里边的东西
- 在函数体里边可以拿到外边的东西

    ```
    let num = 12;
    function fn(n,m){
        console.log(num);
        let name = 'xxx'
        let total = n+m;
        total = total/2;
        return total;
    }
    let res = fn(12, 13);
    console.log(res);
    console.log(name);
    //把函数中的代码以字符串的形式存储进去,存到堆内存

    //函数每执行一次就会形成私有栈内存，把堆内存中的字符串拿过来转换为代码执行

    //外边拿不到函数体里边的东西，在函数体里边可以拿到外边的东西

    ```  

# 3、函数中的arguments
    - 在这里列举一个任意数求和的例子
    1、用户到底传递多少个实参不定
    2、我们还得给每一个参数转数字

    1、arguments是一个类数组，是函数的实参集合，他里面存放着所有的实参
    2、不管写不写形参变量，arguments都存在，
    3、不管写不写实参，arguments都存在
    4、arguments.callee存储的是函数本身，在严格模式下已经禁止使用   
    ```
    <script>
        function fn(){
            console.log(arguments);
            let total = n+m;
            total = total/2;
            return total;
        }
        let num = fn ()
        console.log(num);

        // arguments:他是函数的实参集合，代表了所有实参，是一个类数组，他不受实参和形参的影响

        //1. 任意数的的求和
        function fn() {
            let total = null;// 创建一个变量，用来累计求和
            for (let i = 0; i < arguments.length; i++) {
               let item = arguments[i]//代表数组的每一项
                item = Number(item); //把item转数字
                //验证item是否是一个非有效数字，如果是有效数字，这个条件就成立
                if (!isNaN(item)) {
                    total+=item;
                    //total = total+item;和total+=item;相同，进行数字累计求和
                }
            }
            return total; //把最后的总和return出去
        }
        let num = fn(12,34,trun,'12',NaN);
        console.log(num);

        //callee 代表函数本身

        //function fn(){
            console.log(111)
            arguments.callee()//他就是函数本身，在严格模式下已经禁止使用
        }
        fn()

        //函数表达式
        let fn = function () {}
        fn()
    </script>
    ```

# 4、箭头函数
 - 如果实参只有一个，可以省略函数的小括号
 - 如果函数的return后面只有一句话可以省略函数的大括号和return
 - 箭头函数中没有this和arguments
 - 如果箭头函数return的是一个对象，那就加上括号

```
	<script>
function fn() {} //这是ES5的 =>
        let fn = () =>{}
        //1、如果只有一个形参，可以省略小括号
        let fn = m =>{
            console.log(m);
        }
        //2、如果函数中只有return{}一行代码，可以省略大括号和return
        function fn(m) {
            return m;
        } //转换后
        let fn =m => m;
        // 3、如果函数只有return{}一行代码要给{}加上()  例子：return({})
        let fn = () => {
            return {}
        } //转换成
        let fn = () => ({})
        //4、箭头函数没有this
        //5、箭头函数没有arguments

        function fn(m) {
            return function (n) {
                console.log(1);
            }
        }
        //从里往外一层一层转箭头函数
        function fn(m) {
            return (n)=>{
                console.log(1);
            }
        }
        
        let fn = (m) => {
            return (n) =>{
                console.log(1);
            }
        }

        let fn = m => n=>{console.log(1)}

        function fn() {
            return function () {
                return function () {
                    console.log(3)
                }
            }
        }
        console.log(fn()()())
        //显示3
    </script>
```

# 5、给形参赋默认值
      //如果函数执行不传实参，那就走默认值，如果函数执行传了实参，那就走实参的值
      function fn(n=0,m=0) {
          console.log(n,m);
          let total = n+m;
          return total;
      }
      fn(20,30);

# 6、收缩/展开运算符
```
 <script>
let fn = (...a) =>{
          //把所有的实参收集到变量a里(以数组的形式)
          console.log(a) //[1,2,3,4] 收缩运算符
            let ary = [1,2,3,4]
            console.log(...ary); //1 2 3 4 展开运算符
        }

        fn(1,2,3,4)
        let ary = [1,2,3,4,3];
        let ary1 = [...ary];
        console.log(ary1); //[1,2,3,4,3]
        console.log(ary == ary1) //false 空间地址发生了变化

        let fn = (...a) =>{
            console.log(a) // [1,2,3,4]
        }
        fn(1,2,3,4)

        let ary = [1,2,3,4];
        ary = [...a,12] //向数组末尾新增一项
        console.log(ary) //[1,2,3,4,12]
    </script>
```

# 7、数组的方法
 > 数组是特殊的对象，天生自带一个length属性，代表数组的长度（个数）
 > 大家学习数组的方法，一定要按照数组的几个维度去记忆
    - 方法的含义
    - 方法的参数
    - 方法的返回值
    - 原有数组是否发生改变

## 1、数组的增删改
- 1、push
    + 方法的含义：向数组末尾追加内容
    + 方法的参数：0到多个值
    + 方法的返回值：新数组的length
    + 原有数组是否发生改变：发生改变
```
 let ary = [12,23,45];
        console.log(ary.push(12,66,'erYa')) //返回值为6
        console.log(ary)//[12,23,45,12,66,'erYa']

        ary[ary.length] = 'xxx'; //末尾增加一项
        ary = [...ary,23,'erYa']; //末尾增加一项但原来地址发生变化
        console.log(ary);
```

- 2、unshift
    + 方法的含义：向数组开头加内容
    + 方法的参数：0到多个值
    + 方法的返回值：新数组的length
    + 原有数组是否发生改变：发生改变

```
let ary = [12,23,45];
        console.log(ary.unshift(23,34)); //5
        console.log(ary); //[23,34,12,23,45];
        ary=[23,34,...ary]; //开头增加内容
```

- 3、pop
    + 方法的含义：删除数组末尾最后一项
    + 方法的参数：不传
    + 方法的返回值：删除的那一项
    + 原有数组是否发生改变：发生改变

```
let ary = [12,23,45];
        console.log(ary.pop()) //45
        ary.length-- //删除数组末尾一项
        ary.length-=2;//删除数组末尾两项
        ary.length = 0; //清空数组
        console.log(ary); 
```

- 4、shift
    + 方法的含义：删除数组开头一项
    + 方法的参数：不传
    + 方法的返回值：删除的那一项
    + 原有数组是否发生改变：发生改变

```
let ary = [12,23,45];
        console.log(ary.shift()) //12
        console.log(ary);
```

- 5、splice
    + 方法的含义：实现数组的增删改
    + 方法的参数：不定
    + 方法的返回值：是一个新的数组，数组里是删除的那几项
    + 原有数组是否发生改变：发生改变

```
//(n,m):从索引n开始，删除m个
        //(n):如果只传一个参数，那就是从索引n开始，删除到末尾
        let ary = [12,23,45,'erYa'];
        console.log(ary.splice(1,2)); // [23,45]
        console.log(ary.splice(0,1)); // [12] 删除数组的开头一项
        console.log(ary.splice(ary.length-1,1));//'erYa' 删除数组最后一项
        console.log(ary.splice(0)); //清空数组，从索引0开始，删除到末尾
        console.log(ary.splice()); //返回[]，啥也不删
        console.log(ary.splice(3,0)); // 返回[]，啥也不删
        //数组返回值为删除后剩下的几项


        //(n,m,x):从索引n开始，删除m个，用x替换 x可以为多个值
        //(n,0,x):从索引n开始，删除0个，把x放到索引n对应的值前面
        console.log(ary.splice(1,2,'erGou','gouDan'));//返回值为删去的数组[23,45]
        console.log(ary.splice(0,0,'daDan'))// [] 在数组开头 增加一项
        console.log(ary.splice(ary.length,0,'huangRong')); // 向数组末尾增加一项
        console.log(ary.splice(-1,2)); //有两个参数时，第一个参数为负数时那么不管第二个参数是多少都只会删除最后一项，当两个参数都为负数时，返回空数组
        console.log(ary); //[12,'erGou','gouDan','erYa']
```

## 2、数组的截取和拼接
- 1、slice
    + 方法的含义：实现数组的截取
    + 方法的参数：(n,m)从索引n开始，截取到索引m（不包括索引m对应的那一项）
    + 方法的返回值：是一个新的数组，数组里是截取的那几项
    + 原有数组是否发生改变：不发生改变

```
let ary = ['siMao','sanMao','erYa',12,23,45];
        //(n,m):从索引n开始，截取到索引m(索引m对应的值不算)
        //我要实现截取数组的n项到m项 slece(n，m+1)
        console.log(ary.slice(1,2)); //['sanMao']
        console.log(ary.slice(2,5)); //['erYa',12,23]
        console.log(ary.slice(0,ary.length)) // 克隆数组
        console.log(ary.slice(0)); //克隆数组 从索引0开始，截取到末尾
        console.log(ary.slice(0,0))//没有任何作用

```

- 2、concat
    + 方法的含义：实现数组的拼接
    + 方法的参数：0到多个值
    + 方法的返回值：是拼接后的新数组
    + 原有数组是否发生改变：不发生改变

```
let ary = [12,23,45,45];
        console.log(ary.concat([12,23],[66],true))// [12,23,45,45,12,23,66,true]
        console.log(ary.concat()) // 克隆数组
```

## 3、数组的排序
- 1、reverse
    + 方法的含义：把数组倒排
    + 方法的参数：无
    + 方法的返回值：排序之后的新数组
    + 原有数组是否发生改变：原有数组发生改变

```
 let ary = [12,23,45,67,13];
        console.log(ary.reverse()); //[67,56,34,23,12]
        console.log(ary); // [67,56,34,23,12]
```

- 2、sort
    + 方法的含义：把数组排序
    + 方法的参数：不传或者传一个函数
    + 方法的返回值：排序之后的新数组
    + 原有数组是否发生改变：原有数组发生改变

```
//如果不传参，只能排列一位数的数组(按照左边第一位从大到小排列)
        let ary = [29,31,114,9,20];
        console.log(ary.sort()); // [114,20,29,31,9]  只会按照第一位排序

        //传一个函数
        console.log(ary.sort((a,b) =>{
            return a-b 
            //如果a-b那就是从小到大排列，反之b-a就是从大到小排列
        }))
```

## 4、检测数组中是否包含某一项
-1、indexOf和lastIndexOf
    + 方法的含义：检测数组是否包含某一项
    + 方法的参数：(n,m) n是检测的值，在indexOf中m是检测索引开始的位置，在lastIndexOf中m是检测索引结束的位置
    + 方法的返回值：所检测的值的索引（如果没有就是-1）
    + 原有数组是否发生改变：不发生改变

```
/* 10、indexOf和lastIndexOf
        方法的定义：检测数组中是否包含某一项
        方法的参数：不定
        方法的返回值：检测值的索引，如果没有就是-1
        是否改变原有数组：否 */

        //indexOf是找的检测的值第一次出现的位置
        //(n,m):n是被检测的值，m是开始检测的值
        //(n)：从头开始检测
        let ary = [12,23,45,23,45,36];
        console.log(ary.indexOf(23,2)) // 3
        console.log(ary.indexOf(23)) //1
        console.log(ary.indexOf(89)) //-1
        console.log(ary.indexOf()) // 不传参按没有找到处理  显示-1

        //lastIndexOf:是找的检测的值最后一次出现的位置
        
        //(n,m):n是被检测的值，m是检测到的位置
        //(n):检测到末尾
        console.log(ary.lastIndexOf(23,2)) //1
        console.log(ary.lastIndexOf(23)) // 1
```

- 2、includes
    + 方法的含义：检测数组是否包含某一项
    + 方法的参数：被检测的值
    + 方法的返回值：被检测的值如果在当前数组存在，那就返回true，否则返回false
    + 原有数组是否发生改变：不发生改变

```
let ary  =[12,23,45,66];
        console.log(ary.includes(12)) // true
        console.log(ary.includes(122)) //false
        console.log(ary.includes()) //不传参按没有找到处理
```

##  6、数组转字符串
- 1、join
    + 方法的含义：实现数组转字符串
    + 方法的参数：字符串类型的分隔符
    + 方法的返回值：转换后的字符串
    + 原有数组是否发生改变：不发生改变

```
let ary  =[12,23,45,67,34];
        console.log(ary.join()) //如果不传值，那分隔符就是逗号  显示'12,23,45,67,34'
        console.log(ary.join(' ')) // '12 23 45 67 34'
        console.log(ary.join('$')); //'12$23$45$67$34'
        eval() // 把字符串变为表达式
        console.log(eval(ary.join('+'))) // 求和之后的结果   eval运行里面的运算式enter code here
```

## 7、遍历数组的方法
- 1、forEach
    + 方法的含义：遍历数组
    + 方法的参数：函数
    + 方法的返回值：无
    + 原有数组是否发生改变：不发生改变
```
let ary = [1,true,2,NaN,3];
        ary.forEach((item,index) => {
            console.log(item,index);
            //item是数组的每一项
            //index是数组的每一项的索引
            //数组有多少项就会循环多少轮
        })
```

- 2、map
    + 方法的含义：遍历数组
    + 方法的参数：函数
    + 方法的返回值：是一个数组，数组的每一项是当前循环的返回值
    + 原有数组是否发生改变：不发生改变

```
ary.map((item,index) => {
            //数组有多少项就循环多少次
            //item为数组的每一项
            //index为每一项的索引
            return
        })
```
+ 3. some
  + some() 方法用于检测数组中的元素是否满足指定条件（函数提供）。
  + some() 方法会依次执行数组的每个元素：
    + 如果有一个元素满足条件，则表达式返回true , 剩余的元素不会再执行检测。
    + 如果没有满足条件的元素，则返回false。

  +  some() 不会对空数组进行检测。
  +  some() 不会改变原始数组。

+ 4. filter: 过滤，如果回调函数返回true，就把这一项放到新数组中返回，不改变原数组

+ 5. find:从左到右循环，找到满足条件的第一项，停止循环，并把这一项返回出去；如果没有找到返回undefined

+ 6. every：从左到右循环，找到不符合条件的第一项，停止循环，返回false；如果都满足条件，就返回true

+ 7. reduce: 收敛，一般用于求和

```
let arr = [{price:5,count:3,name:"苹果"},{price:3,count:2,name:"橘子"},{price:2,count:5,name:"香蕉"}]

        let title = arr.reduce(function (prev,next) {
            return prev+ next.price * next.count
        },0)
```

# 数组去重
+ 1.利用includes检测数组是否存在同样的数
```
   let ary = [12,23,34,12,23];
            
   function fn(ary) {
	   let newAry = [];
       //创建一个空数组
       for (let i = 0; i < ary.length; i++) {
       let item = ary[i];
       //获取数组中的每一项
       if (!newAry.includes(item)) {
			//把ary的数拿出来检测如果有就放 弃，没有就加入newAry
			newAry.push(item);
     }
     return newAry;
     //输出新数组
    }
 }
  closed.log(fn(ary));
```

2.循环数组每一项，拿当前项和后面的数一次作比较，如果后面的数和当前项相等了，那就在原数组里删除相等的数(splice)

```
 let ary = [1,1,23,2,3,1,2];

 function fn(ary) {
                //循环数组每一项
                for (let i = 0; i < ary.length; i++) {
                    let item = ary[i];
                    //数组的每一项
                    for (let j = i+1; j < ary.length; j++) {
                        let cur = ary[j];
                        //当前项后面的每一项
                        //如果当前项和后面的某一项相等了，条件成立
                        if (item === cur) {
                            ary.splice(j,1); //从原数组中删除重复的那一项
                            j--; //为了防止数组塌陷，删除之后要把j--
                            //从数组中删除一项，后面的每一项的索引都得往前挪一位(数组塌陷)
                        } 
                    }  
                }
            }
            console.log(fn(ary));
            console.log(ary);
```

3.利用对象的属性名存在不是undefined属性

```
      let ary = [1,1,2,3,1,2,3];
      //循环数组的每一项，然后把数组的每一项都放进对象里(让键值对的key和value都等于那一项)
      function fn(ary) {
         let newAry = {}//创建一个新对象用来储存键值对

         //循环数组每一项
         for (var i = 0; i < ary.length; i++) {
        //检测一下当前项在对象里有没有，如果有，那以下条件就成立
        //也就是说以前就存储过这一项(证明已经是重复项)
         if (newObj[ary[i]] !== undefined) {
		//ary.splice(i,1); //删除重复项
       //i--; //防止数组塌陷
       ary[i] = ary[ary.length-1];//用数组的最后一项替换重复的那一项
       ary.length--; //删除数组最后一项
       i-- //把替换的值还要检测一遍
 }else{
      // 如果对象中没有这个属性名对应的属性值，那就新增这个键值对
       newObj[ary[i]] = ary[i];
     }
  }
}
  fn(ary);
 console.log(ary);
```

# 字符串方法
字符串的方法
        let str = 'asdfgh';
        字符串有length代表字符串的长度  例子：str[0] =>'a'; str[str.length] =>6
        字符串不可以通过length进行增删改
        字符串的所有方法都不改变原字符串
        返回值都是处理之后的字符串

1.字符串的获取
    (1).charAt(n):通过索引获取对应的字符串
        let str = 'absdfgh'
        console.log(str.charAt(0)); //'a'
        console.log(str[0])  //'a'
        console.log(str.charAt(100)); //''  如果获取不到就是空字符串
        console.log(str[100]); //undefired

(2).charCodeAt:通过索引找到对应的ASCII码(Unicode码)
        console.log(str.charCodeAt(0)); //97
        console.log(str.charCodeAt(1)); //115
        console.log(String.fromCharCode(97));//'a'

2.字符串的截取
(3).substr(n,m):从索引n开始，查询m个;
        let str = 'asdfgh';
        console.log(str.substr(1,2)) //sd
        console.log(str.substr(0)) // 克隆 查询到底
        console.log(str.substr()) // 克隆 查询到底

(4).substring(n,m):从索引开始，查询到索引m(不包括m对应的那一项)
        let str = 'asdfgh';
        console.log(str.substring(1,3)) // sd
        console.log(str.substring(0)) // 克隆 查询到底
        console.log(str.substring()) // 克隆 查询到底

(5).slice(n,m):从索引n开始，查询到索引m(不包括m对应的那一项)，可以支持负数
        //> 如果你传的参数是负数，那就把负数加上length，在后再取值
        let str = 'asdfgh';
        console.log(str.slice(-1,-4));//(5，2) 返回空字符串 
        console.log(str.slice()); // 克隆 查询到底
        console.log(str.slice(0)); // 克隆 查询到底

 //检测某一项是否存在
        (6).indexOf(x,y):检测某个值开始的位置，把对应的索引返回出去(x是查找的值，y是开始查询的位置)
        (7).lastindexOf(x,y):检测某个值最后一次出现的位置，把对应的索引返回出去
        (8).includes：查询某个值有没有，如果有就是true，没有就是false

 //字符串转大小写
        (9).toUpperCase() //转大写
        (10).toLowerCase() //转小写
        let www = 'yangayng';
        console.log(www.substring(0,1).toUpperCase() + www.substring(1))
        console.log(www.replace('y', 'Y'))

//把字符串转数组
        (11).split():把字符串以指定的分隔符分割为数组，参数是字符串的分隔符
        let str = 'as|da|sd|asd'
        console.log(str.split('|')); //['as','da','sd','asd']
        console.log(str.split(''))//  ["a", "s", "|", "d", "a", "|", "s", "d", "|", "a", "s", "d"]
        //如果参数为空字符串会把每一项都变成字符串转换成数组

  let str = 'sasasasas';
        console.log(str.split('a').join('')) //["s", "s", "s", "s", "s"] => 'sssss'  利用转数组转字符串消除字符串不想要的

 //替换
        (12).replace(n,m):把字符串中的n替换为m(只替换第一个)
        let str = 'asdsfasgh';
        console.log(str.replace('s','$')); //正常只会替换第一个 返回值为'a$dsfsgh'
        console.log(str.replace(/s/g,'$')); //用正则全部替换
        console.log(str.replace('a','x').replace('a','x')); //可以加.一个一个替换
        console.log(str.replace('z','x'));//如果替换不成功，返回原字符串

(13).trim去空格 （trimLeft去左空格、trimRight去右空格）

# 数学对象 Math
        // - 1、PI：3.1415926 获取圆周率周派
        // - 2、abs():给一个数取绝对值
            console.log(Math.abs(-1)) // 1
        // - 3、ceil(): 向上取整
            console.log(Math.ceil(3.1)) //4
        // - 4、floor(): 向下取整
            console.log(Math.floor(3.01)) //3
        // - 5、round(): 四舍五入
        // - 6、max(): 一组数的最大值
            console.log(Math.max(...[12, 23,34 ,56])) //56
            console.log(Math.max(true, false, null,NaN))  //NaN 如果不是数字类型会先转数字再取最大数，有NaN会选NaN
        // - 7、min(): 一组数的最小值
            console.log(Math.min(...[12, 23,34 ,56])) //12
            console.log(Math.min(true, false, null,NaN))   ////NaN 如果不是数字类型会先转数字再取最小数，有NaN会选NaN
        // - 8、sqrt(): 开平方
            console.log(Math.sqrt(9)) //3
        // - 9、pow(n,m): 求一个数的多少次幂(n为幂的值，m为幂的次方)
            console.log(Math.pow(2,10)) // 1024
        //     + 1024b=>1kb
        //     + 1024kb=>1mb
        //     + 1024mb=>1Gb
        //     + 1024Gb=>1Tb
        // - 10、random: 获取一个随机数
            //取n到m之间的随机整数（包括n和m）
            //Math.round(Math.random()*(m-n)+n);
            //取3到5的随机整数，（包括3和5）
            console.log(Math.round(Math.random()*(2)+3))

# 日期
//new Date获取的是你的电脑的本地时间，不能用作比较重要的计时，或者获取时间等操作
        let time = new Date(); //获取当前时间
        let year = time.getFullYear(); //获取年
        let month = time.getMonth()+1; //获取月 (是从0到11，所以我们要给他加1)
        let date = time.getDate(); //获取日
        let day = time.getDay(); //获取星期几(0是星期日)
        let hour = time.getHours(); //获取小时
        let min = time.getMinutes(); //获取分钟
        let sec = time.getSeconds(); //获取秒
        let mill = time.getUTCMilliseconds();// 获取毫秒
        let sss = time.getTime(); //它是现在距离1970年1月1号00时00分00秒的时间差(单位是毫秒) [时间戳]

# 获取dom的方式
1、document.getElementById('id名') 在document上下文中获取元素(通过Id获取的元素是一个元素对象)
1、let box = document.getElementById('box')

2、context.getElementsByTagName('标签名')  在指定的上下文中通过标签名获取元素，获取的是一个元素集合，如果没有获取到元素，那就是空元素集合
2、let lists = nav.getElementsByTagName('i');

3、context.getElementsByClassName('')  在指定的上下文中通过class名获取元素，获取的是一个元素集合，如果没有获取到元素，那就是空元素集合【在IE6~8下不兼容】
        
4、document.body/document.head/document.documentElement(获取body、头部、html)
4、 console.log(document.body) // 获取body
    console.log(document.head) // 获取头部
    console.log(document.documentElement) // 获取html 

5、context.querySelector()  在指定上下文中通过选择器获取第一个元素，获取不到就是null【在IE6~8下不兼容】
   let ss =  box.querySelector('#navList .a');

6、context.querySelectorAll()  在指定上下文中通过选择器获取一组元素集合，获取不到就是空元素集合【在IE6~8下不兼容】
    let list = document.querySelectorAll('#navList li:nth-child(2)');


# 节点
节点（node）：页面中所有的东西都是节点，所有的节点都是对象

节点名      nodeType     nodeName        nodeValue
元素节点       1       大写的标签名          null
文本节点       3         '#text'         文本的内容
注释节点       8         '#comment'      注释的内容
文档节点       9         '#document'        null 
       

元素节点就是页面中的标签
文本节点包括内容、空格、回车（换行）
注释节点就是你写的注释
文档节点就是整个大文档（页面）

操作节点的属性
childNodes:获取的所有的子节点
children:获取所有的元素子节点【在IE6~8下不兼容】

firstChild: 获取第一个子节点
firstElementChild：获取第一个元素子节点【在IE6~8下不兼容】

lastChild:获取最后一个子节点
lastElementChild:获取最后一个元素子节点【在IE6~8下不兼容】

previousSibling:获取上一个兄弟节点
previousElementSibling:获取上一个兄弟元素节点【在IE6~8下不兼容】

nextSibling:获取下一个兄弟节点
nextElementSibling:获取下一个兄弟元素节点【在IE6~8下不兼容】

parentNode:获取父节点

## js节点的增删改
createElement:创建元素节点
createTextNode:创建文本节点
容器.appendChild(节点)：把节点插入到容器的末尾
容器.insertBefore(新节点, 老节点)：把节点插入到老节点的前面
容器.removeChild(节点)：移除容器中的节点
replaceChild 替换
```
let box = document.createElement('div'); // 动态创建一个元素节点
        let one = document.getElementById('one');
        box.style.width = '200px';
        box.style.height = '200px';
        box.id="box";
        box.className = 'box';

        let text = document.createTextNode('123455');// 动态创建一个文本节点
        box.appendChild(text); // 把文本节点插入到元素的末尾
        // document.body.appendChild(box) // 把box插入到元素的末尾
        document.body.insertBefore(box, one) // 把box插入到one的前面
        // document.body.removeChild(one) // 移除节点
        console.dir(text)
        console.log(box)
```

## js动态克隆节点
节点.cloneNode(true/false);克隆节点，如果传参是true就是深克隆，如果不传参或者传false就是浅克隆（只复制外层元素，不复制里边的内容）
```
let one = document.getElementsByClassName('box');
        let clone1 = one.cloneNode(); // 如果不传参，就是浅克隆
        let clone2 = one.cloneNode(true); // 深克隆
        let clone3 = one.cloneNode(false); // 传false，就是浅克隆
        clone1.innerHTML = '<span>222</span>'; // 修改clone1的内容
        clone2.children[0].innerText = '333'; // 修改clone2里的span元素的内容
        document.body.appendChild(clone1); // 把clone1插入到body的末尾
        document.body.appendChild(clone2)// 把clone2插入到body的末尾
```

## 增加行内属性
setAttribute('属性名',属性值)； 在元素结构中设置自定义属性 
getAttribute('属性名') 在元素结构中获取自定义属性
removeAttribute('属性名'); 在元素结构中移除属性
classList.add('属性名'); 增加属性名
classList.remove('属性名'); 删除属性名
```
<button>1</button>
<button>2</button>
<button>3</button>
<script>
        for (var i = 0; i < btns.length; i++) {
            // 把属性存储到元素的结构中，在元素的行内可以看到
            btns[i].setAttribute('data-index',i); // 给每一个button的结构中增加属性
            // btns[i].removeAttribute('data-index');// 给每一个button的结构中移除属性
            btns[i].onclick = function(){
                // 获取结构中的属性
                alert(this.getAttribute('data-index'))
            }
        }
        console.log(btns)
</script>
```

# 递归
递归：就是函数自己调用自己，直到满足某些条件就停止递归
```
// 实现1到5之间的偶数的和
    function sum(num){
        if(num>5){
            return 
        }
        if(num%2 === 0){
            return num + sum(num+1)
        }
        return sum(num+1)
    }
    console.log(sum(1)) // 6

	细节：
    // function sum(1){
    //     return sum(1+1) // 6
    // }

    // function sum(2){
    //         return 2 + sum(2+1) // 4
    // }

    // function sum(3){
    //     return sum(3+1) // 4
    // }

    // function sum(4){
    //         return 4 + sum(4+1) // 0
    // }

        // function sum(5){
    //     return sum(5+1) // 0
    // }

    // function sum(6){
    //         return 0
    // }
```

# 作用域：全局作用域，私有作用域，块级作用域

## 全局作用域

 + 全局作用域：
    当你打开一个页面，浏览器就会形成全局作用域为代码执行提供环境，在全局作用域在会生成一个全局的大对象叫window

 + 全局作用域一般不销毁，直到页面关闭，作用域才会销毁

 + 全局变量
    在全局作用域下声明的变量就是全局变量
    > 在全局作用域下给window创建属性的办法1.在全局作用域下直接创建 a=100; 2.var 3.function
    > 给window新增键值对是发生在变量提升的阶段


    1. 用var和function声明的变量会在全局作用域下声明一个变量，而且也会给window增加属性，属性名是变量名，属性值是变量名储存的值(let声明的变量不能给window增加键值对，const声明的常量也不能新增键值对)
     ```
     var s = 12;
     function fn(){}
     console.log(window.s)
     console.log(window.fn)
     let a = 12;
     console.log(window.a) // undefined
     ```

    2. var和function可以重复创建同一个变量名(let不可以在同一个作用域中重复声明)
     ```
     var a = 12;
     var a = 13;
     console.log(a) // 13

     let a = 12; // 报错  SyntaxError（语法错误）
     let a = 13;
     ```

    3. var和function有变量提升(let不进行变量提升，在代码运行以前，会对当前作用域下带let进行解析，判断是否有重名的变量；有的话，就直接报错)
     ```
     
     b = 12 // 等价于window.b = 12因为window.可以省略
     var b = 12(有变量提升)
        
     var a = b = c = 12; // 等价于var a = 12;b = 12; c = 12;

     var a,b,c = 12; // 创建变量a、b、c，但是只给c赋值

     var a = 12,b = 13, c = 14; // 创建三个变量，给每一个变量都进行赋值
     console.log(a, b, c)
     ```

## 私有作用域：

 + 全局作用域生成之后才会有私有作用域，私有作用域是属于全局作用域的

 + 函数执行会形成一个私有的栈内存（私有作用域）【为代码执行提供环境】

 + function fn(){
    函数定义：
        1、首先开辟一个堆内存生成一个16进制的空间地址
        2、把函数体里的代码以字符串的格式存储进去
        3、把16进制的地址赋值给函数名
        }

 + fn()
    函数执行：
        1、首先开辟一个私有作用域【为代码执行提供环境】
        2、形参赋值和arguments赋值
        3、变量提升
        4、代码从上往下执行
        5、作用域是否被销毁

 + return的作用
    1. 阻断函数代码运行
    2. 把值ruturn出去

 +  私有变量
    1. 在私有作用域里边定义的变量就是私有变量（let、var、function、const）
    2. 形参也是私有变量(形参和arguments存在映射关系)
    3. 在私有作用域里使用一个变量，如果自己私有作用域有，就是用自己的，如果没有呢，就是用上一级作用域的
    4. 函数外边不能拿到函数里边的变量
    5. 如何判断当前变量是一个私有变量
        + 当前作用域有没有被var
        + 有没有被function
        + 是否是形参
        + 有没有let或const

## 函数的作用域查找
> 函数的上一级作用域是谁，在函数定义的时候就已经确定了，函数在哪创建的，他的上一级作用域就是谁，跟在哪执行的没有关系

## 作用域链查找机制
> 在私有作用域中，函数执行，如果要使用一个变量，自己作用域要是有，就使用自己的，要是没有，就向上一级作用域查找，上一级还没有，在向上一级查找，直到找到全局作用域，如果还没有就报错--->这种一级一级向上查找的机制就是【作用域链查找机制】

## 暂时性死区
> 暂时性死区：在代码块内，使用let和const命令声明变量之前，该变量都是不可用的，语法上被称为暂时性死区。
> 暂时性死区的本质就是，只要一进入当前作用域，所要使用的变量就已经存在了，但是不可获取，只有等到声明变量的那一行代码出现，才可以获取和使用该变量。
```
console.log(typeof a) // a is not defined
let a = 12
//ES6让js变得更加严谨
```

## 变量提升
 + 变量提升就是浏览器解析代码的一个过程
 + 在当前作用域中，代码执行之前，浏览器会对当前作用域里的带var和function进行提前的声明和定义；带var的只声明（创建变量）不定义；带function既声明（创建变量）又定义（进行赋值）
 + 在变量提升时，首先对当前作用域下的函数进行变量提升，然后再对var变量提升
 + let不进行变量提升，在代码运行以前，会对当前作用域下带let进行解析，判断是否有重名的变量；有的话，就直接报错
 ```
    console.log(window.a); // undefined
    console.log(b); // 报错 引用错误 在当前代码之后的代码不在运行
    var a = 10;
    b = 12;

    console.log(b; // 报错 语法错误，他会使整个页面不运行
 ```

## 变量提升的特殊情况
1. 变量提升发生在等号左边
2. 不管if条件是否成立，都要进行变量提升
 > 在老版本浏览器里，if条件里的function既声明又定义，
 > 在新版本浏览器里，if条件里的函数只声明不定义
 >  条件一旦成立，第一件事就是给函数名赋值,然后在执行代码
    ```
        console.log(fn); // undefined
        // var和function给window增加属性的过程是变量提升的时候发生的
        if ('fn' in window) {
            // 如果条件成立，进来的后的第一件事就是给fn赋值(开辟堆内存)，然后在执行代码
            fn(); // 'erYa'
            function fn() {
                console.log('erYa');
            }
        }
        fn();
    ```
 >  in 属性，他是检测一个对象中有没有某个属性名，如果有就返回true，反之就返回false
    ```
    let obj = {
        name: 22,
        age: 33
    };
    console.log('age' in obj);  // true
    console.log('ss' in obj) // false
    ```
3. 函数里虽然return下面的代码不执行，但是要进行变量提升
4. 匿名函数不进行变量提升
5. return的代码不进行变量提升
6. 自执行函数不进行变量提升

## 堆栈内存
> 打开一个页面，浏览器会形成两个虚拟的内存：堆内存、栈内存
> 栈内存存储了啥：变量、基本数据类型值、地址(每形成一个作用域，就会消耗一块栈内存)
> 堆内存储存了啥：储存了引用数据类型的值(会首先把属性名是数字的按从小到大顺序放进堆内存中)
> 咱们的全局作用域、私有作用域都是栈内存，为代码执行提供必要的环境，理论上来说，存储的东西越少，运行的越快

### 堆栈内存的销毁
 + 堆内存的销毁
  + 谷歌浏览器(标记法)：谷歌浏览器每隔一段时间就会在当前作用域从头到尾检查一遍，看看有没有没有被占有的空间地址，如果有，就立即对其进行回收

  + IE和火狐(计数法)：浏览器采用计数的规则，如果空间地址被占用一次，那这个空间地址就默认+1，每空闲一次，空间就默认-1，如果浏览器发现有空间地址的计数为0的空间地址，就把其回收

 + 栈内存的销毁
  + 作用域就是栈内存：全局作用域、私有作用域
  + 栈内存回收，那么栈内存中所有储存的值都会随着回收
  + 栈内存的销毁：立即销毁、不销毁、不立即销毁
    1. 全局作用域的销毁：一般情况不销毁，除非把当前页面关闭，整个作用域就销毁了

    2. 私有作用域的销毁：立即销毁、不销毁、不立即销毁
     + 立即销毁
     + 不销毁
       - 函数要return一个引用数据类型值
       - 函数的return值要被外界接收
     + 不立即销毁

```
function fn(){
    var name = 'jinYu',
    age= 16;
    return {
        name: name,
        age: age
    }
}
var res = fn() 
//不销毁

function fn(){
    var a = 1;
    // 在该函数中，空间地址被DOM元素的事件占用；这个作用域是不销毁的；
    first.onclick = function(){
        console.log(a);
    }
}
fn();

var a = 100;
var obj = {
    a:1,
    fn:(function(){
        // 这个作用域也是不销毁的；这个自执行返回的小函数，被obj的fn属性占用；
        // 这个自执行函数的上一级作用域是全局作用域；
        var a = 0;
        return function(){
                    console.log(a);// 0
                }
            })()
        };
obj.fn();
//不销毁

function fn(){
    var a = 12;
    return function(){
        console.log(a)
    }
}
fn()() 
// 当外层大函数执行完成之后不能立即销毁，他要继续等待里面的小函数执行完成销毁之后，大函数再销毁       
``` 

## 闭包
> 闭包=>函数执行形成的私有作用域就是闭包，他可以保护里边的私有变量不受外界干扰,还可以保存变量
> 闭包：在函数执行体中返回一个小函数，这个小函数可以访问小函数外的变量，这种现象就是闭包

## this
> this:他是js中的关键字，有特殊的含义
> this:他就是函数的执行主体，谁执行的函数this就是谁
> 不能给this直接赋值，this 不能放到等号的左边

1. 在全局作用域下，this就是window
2. 函数执行时，看执行函数前有没有“.”,如果有点，那点前面是谁，this就是谁，如果没有点，那this就是window
3. 自执行函数里的this是window
4. 给元素事件行为绑定方法，方法里的this指向被绑定的元素本身
5. 回调函数里的this一般指向window(函数的参数是函数执行，执行的函数就是回调函数)
6. 构造函数的this是当前实例
7. 实例的公有方法和私有方法的this一般情况是当前实例
8. 箭头函数没有this
9. call,apply,bind 可以改变this指向；
10. 自执行函数的实参中的this，指向了自执行函数外层的作用域

```
function A(){
    console.log(this); 
}
function B(a){
    var obj = {a:a}
    obj.a();
}
B(A)
//回调函数的this指向可以改变，不一定是window
```

## 单例模式
> 单例模式：把描述同一个事物特征的信息进行分组归类，放到同一个命名空间下(减少全局变量的污染)
```
    //    var name = 'erYa';
    //    var age = 18;

    //    var name = 'jinYu';
    //    var age = 22;

    //    let person1 = {
    //        name: 'erYa',
    //        age:18
    //    };
    //    let person2 = {
    //        name: 'jinYu',
    //        age: 22
    //    }
    // person1变量名就是命名空间
```
### 高级单例模式
> 把单例模式封装到一个自执行函数里 (闭包)
```
let person1 = (function(){
        let age = 18;
        let name= 'erYa';
        return {
            bar:function(){
                var num = 100;
            };
            fn:function(){};
        }
    })()


        let person2 = (function(){
        let fn = function(){};
        let name= 'jinYu';
        let age = 18;
        return {
            name:name,
   
            fn:fn
        }
    })()

    let person3 = function(){
        let name= 'jinYu';
        let age = 26
        return {
            name:name,
            fn:fn
        }
    }
    console.log(person2) // 这是一个函数，不是person3的个人信息,因为它不是自执行函数，没有执行
```

## 工厂模式
> 工厂模式：函数的封装
> 把实现同一个功能的代码放在一个函数体中，当想实现类似的功能时，直接执行这个函数就可以，减少了代码的冗余：实现了高内聚，低耦合：就是行数的封装
> 如果用单例模式去写很多个person就会变的很麻烦，就有了工厂模式
> 特点：批量生产
> 把实现相同功能的代码封装到函数里，以后想运行这个方法，就直接执行这个函数就好了
> 高内聚：提高代码的复用率
> 低耦合：减少页面的重复的代码
```
function createPerson(name, age){
            var name = name;
            var age = age;
            var sex = 'girl'
            return {
                name,
                age,
                sex
            }
       }
       let person1 = createPerson('erYa', 18);
       let person2 = createPerson('jinYu', 18);
       console.log(person1, person2);
```

## 面向对象(重):基于对象
> 对象：万物皆对象
标记语言：HTML/CSS3
编程语言：JavaScript、PHP、C.....
面向过程：C
面向对象：JS、PHP...

## 构造函数(重)
> 刚才那些都是js的内置类，但是我们也可以自己去自定义一些类
> new 函数执行叫做构造函数运行模式，此时的Fn就是自定义的Fn类(构造函数)，函数执行之后的返回结果就是一个对象，叫做实例对象(f就是Fn的实例)
> 类就是函数数据类型的
> 实例是对象数据类型的
> 构造函数中的this指向当前实例
> 箭头函数不能被new执行，所以不能当构造函数
> 构造函数和普通函数的不同
> 类一定是个函数，但函数不一定是类
 1. 运行上的不同
    普通函数 ➡ 形成私有作用域 ➡ 形参赋值 ➡ 变量提升 ➡ 代码执行 ➡ 作用域是否销毁

    构造函数 ➡ 形成私有作用域 ➡ 形参赋值 ➡ 变量提升 ➡ 默认生成一个对象 ➡ 把this指向这对象 ➡ 代码执行 ➡ 默认把这个对象return出去 ➡ 作用域是否销毁

 2. 执行上的不同
    构造函数如果不传实参，可以不加小括号
 
 3. 构造函数如果手动return一个基本数据类型的值，不会改变返回值，如果手动return一个引用数据类型的值，就会改变返回值，此时return的东西已经不是此前类的实例了【所以不要轻易修改构造函数的返回值】

 > new操作符具体做了什么
   1. 在代码执行之前，函数中会首先创建一个空对象
   2. 让当前函数中的this指向这个空对象
   3. 当代码执行完成之后，会默认返回空对象
```

        //   构造函数（构造自定义类）
        function Fn(name, age) {
            /* 
            1、默认生成一个空对象 {}
            2、让函数里的this指向这个对象
            3、代码执行
            4、默认return 这个对象
            */
            this.name = name; // 给this增加键值对
            this.age = age // 给this增加键值对
            this.say = function(){}
            return {}
            //只有this才算属性
        }

        // new: 他是js里的关键字
        Fn() // 普通函数运行
        let f = new Fn()  // {}
        let f1 = new Fn('erYa', 18);
        let f2 = new Fn('jinYu', 18);
        let f3 = new Fn;
        let f4 = Fn;
        console.log(f)
        console.log(f1)
        console.log(f2)
        console.log(f1.age === f2.age)
        console.log(f1.say === f2.say)
        console.log(f3)
        console.log(f4)

        function Fn(){
            this.name= 100;
        }
        var f=new Fn;
                
        // 如果这个函数需要参数，那么这个需要有小括号，如果不需要参数，那么小括号可以省略；
```

**函数：**
1、普通函数：
    1、形参、实参、arguments、箭头函数、arguments.callee、return
    2、私有作用域、闭包、this、变量提升、私有变量、
    3、形成私有作用域、形参赋值、变量提升、代码执行、作用域是否销毁
    4、作用域链
2、构造函数
    1、形成私有作用、形参赋值、变量提升、默认生成一个空对象、让函数里的this指向当前对象、代码执行、默认把this return出去、作用域是否销毁
    2、构造函数执行时如果不传实参，可以不加小括号
    3、如果手动return一个基本值，那构造函数的返回值不会被改变，如果renturn引用值，那函数返回值就会被改变(现在return已经不是当前类的实例了)
    4、构造函数里的this指向当前实例
3、普通对象
    由0到多组键值对组成、属性名的类型是数字或字符串

函数的主角色还是函数
函数既有protopyte又有__proto__，函数的堆内存既储存了函数的私有属性，又储存了函数体中的代码字符串，是在同一个空间地址下的

## instanceof
> instanceof:他是检测当前实例是否是属于某个类的实例，如果实例是属于这个类，那就返回true，反之就是false
> instanceof只要检测的类在实例的原型链上，那么就返回true
> 只要改变了当前实例的原型链，那结果就不准确了
> 【局限性】：instanceof不能够检测字面量方式创建的基本数据类型，只能检测引用数据类型的值

**创建变量**
> 字面量方式创建变量
  + 通过字面量方式创建的基本数据类型值不是一个标准的实例，不能使用instrnceof进行检测，引用数据类型方式创建的就是一个标准的实例，可以使用instrnceof检测

```
var num = 1;
console.log(num instanceof Number); //false
var obj = {};
console.log(obj instanceof Object); //true
var ary = [];
console.log(ary instanceof Array); //true
```
> 实例创建
```
var num = new Number(1);
console.log(typeof num); //'object'
console.log(num instanceof Number);//true
console.log(num); //Number {1}
console.log(num+1) //2
console.log(num == 1 ) //true

//如果实例创建的数组的参数是数字并且只有一个参数，那就代表数组的length；如果大于等于两个，那么就是数组的每一项；
var  arr = new Array(100,200);
console.log(arr); //[100,200]
console.log(typeof Array); //function
var arr = new Array("a");
console.log(arr); //['a']

//Function是所有函数数据类型的基类
var f = new Function；
console.log(f); //(function anonymous() {})
var p1 = new f;
console.log(p1); //{}
var ary = [];
//ary是Array的实例，Array是Function的实例；
console.log(Array  instanceof Function);//true
```

```
    let ary = [];
    let obj = {name:1};
    console.log(ary instanceof Array) //true
    console.log(obj instanceof Object) //true
    console.log(ary instanceof Object) //true
    console.log(ary instanceof RegExp) //false
    console.log(/^$/ instanceof RegExp) //true RegExp是正则的意思

     /* 
        1、自变量创建实例的方式
        let num = 1;
        let str= 'w';
        2、构造函数创建实例的方式
        let ss = new Number(1);
        */
       let ss = new Number(1); // 利用构造函数的方式创建一个Number的实例
       console.log(ss)
       console.log((1).toFixed(2)) // '1.00'  把数字转换为字符串，保留指定位小数
       console.log(ss.toFixed(2)) // '1.00'
       let w = new String(3)  // 创建一个字符串的实例
       console.log(w)
       console.log(w.substr) // f
       console.log(w instanceof String) // true
```

## 原型模式(重)
> 构造函数解决了实例的私有属性的问题
 1. 每一个函数(普通函数、构造函数)都天生自带一个prototype属性，属性值是一个对象，他里面储存的是实例的公有属性(原型)
 2. 每一个原型都天生自带一个constructor属性，其属性值指向当前类
 3. 每一个对象都天生自带一个__proto__属性，其属性值指向当前所属类的原型
 4. 构造函数解决了实例的私有属性问题，原型解决了实例的公有属性问题;如果将实例的私有属性放在公有属性上，减少了堆内存的开辟

 1. Function是每一个函数的基类
 2. Object是每一个元素的基类
 3. Object的原型的__proto__指向自己，但是没有意义，那就是null
 4. 每一个函数都是Function的实例，(包括他自己，他的__proto__执行自己的原型)
 5. object是类，类是函数，按他的__proto__指向Function的原型
 6. 所有的原型(都是对象)都指向Object的原型
 7. Function的原型是个匿名函数()
例子见2019.11.22老师课件

**函数的三种角色：普通函数、构造函数、普通对象**
+ 函数数据类型：普通函数、构造函数（类）
+ 对象数据类型：普通对象、数组、Math、Date的实例、arguments类数组、正则对象、实例对象、原型、元素集合(类数组)、函数

## hasOwnProperty
> hasOwnProperty:检测一个属性是否是自己的私有属性
> in:检测一个属性是否属于某个对象
> 实例.hasOwnPeoperty(被检测的值)
```
let ary = [1, 2, 3];
        console.log(ary.hasOwnProperty(0)) // true 0是ary实例的私有属性
        console.log(ary.hasOwnProperty('push')) // fasle push是ary实例的公有属性
```

## 原型链
在对象里查询一个属性，先看自己的私有属性有没有，如果有就使用自己私有的，如果没有，就通过__proto__找到自己所属类的原型，看看原型上有没有，如果有就使用，如果没有就通过原型的__proto__找到Object的原型上，如果Object的原型上还没有，那就是undefined，这种一级一级向上查找就会形成原型链

**原型：**
1、Function是所有函数的基类（包括自己）
2、Object是所有对象的基类
3、Object的原型的__proto__执行的是自己，js认为自己指向自己没有意义，就规定为null
4、所有的函数都是Function的实例，那Object类的__proto__指向Function的原型
5、Function也是函数，所以他的__proto__指向自己的原型

**原型扩展**
1. 给Fn的原型新增键值对，这就是原型扩展
2. 用新的空间地址覆盖fn原有的空间地址，会导致constructor的丢失
```
Fn.prototype.getX=function(){} //增加键值对
Fn.prototype={
            constructor:Fn,
            getY:function(){
            }
        }
//重新覆盖地址 此时constructor会丢失，但是可以手动添加一个
```
> 内置原型的扩展方法 (添加键值对的方法)
 Array.prototype.aa=function(){
            console.log("你很帅");
        }
> 内置类的原型的空间地址不允许修改

**可枚举属性和不可枚举属性**
> 可枚举属性：1.对象的私有属性 2.新增的公有属性
> 不可枚举属性：对象或原型中天生自带的属性属于不可枚举属性
```
// for in 可以列举出所有的可枚举属性
    for(var key in f){
        console.log(key);  
    }
```

**Function和Object**
1. 所有的函数数据类型(普通的函数、内置类、自定义类)都是Function的一个实例
2. Function和Object都是Function的一个实例；Object的__proto__指向Function的原型
3. 所有的函数都有prototype和__proto__属性；
4. 所有类的原型(对象)中的__proto__都指向Object的原型；
5. window 是全局作用域中一个大的对象；window是Object的一个实例；

**constructor**
1. 不能把类的原型重定向
2. 不能在私有属性上加constructor

**给实例的类封装公共方法需要注意的几点**
1. 你自己封装的方法不能与人家内置的方法同名
2. 给你自己的方法加前缀

**自定义类的this**
1. 实例的私有属性或者公有属性里的this一般指向当前实例
2. 构造函数里的this是当前实例

console.log(ary.myUnique().sort().reverse().slice(1,3))
**如果你想用链式调用，前提是你的方法的返回值必须是当前类的实例**

**内置类的原型不能被重定向**
```    
Array.prototype = {};
console.log(ary.push)

Array.prototype.mySlice = function(n,m){
    return this.slice(n,m)
}
```

**优先级**
1. 成员访问：寻找对象里的属性名所对应的属性值就是成员访问(19)
    Fn.aa
2. new(带参数列表):就是构造函数执行有括号(19)
3. new(无参数列表):就是构造函数执行没有括号(18)
优先级一样，从左到右运算

## call apply bind 改变this指向
> 每一个函数都是Function的实例，所以每一个函数都可以调取Function原型上的方法
> call、apply、bind他们三个都可以改变函数里的this指向
>  "use strict"  // 使用严格模式

+ call方法
  > fn通过__proto__先找到Function原型中的call方法，让call方法执行，call执行时，改变了call的this的this指向，fn中的this指向了call的第一个参数，并且让call中的this执行

  1. fn通过__proto__属性找到当前所属类的原型(Function的原型)上的call方法
  2. 让call方法执行，并且给call传实参
  3. 在call方法执行的同时，也让fn执行，并且把fn的this指向了第一个参数
  4. 在严格模式下，如果call不传参或者传undefined，那fn的this就是undefined，如果传null，那fn的this都是null
  5. 在非严格模式下，如果call不传参或者传undefined或者传null，那fn的this都是window
  6. call的第一个参数是fn的this指向，从第二个开始，就都是fn的正常参数了
  7. fn1.call.call(fn2); //2 不管前边有多少call，他执行的是最后一个call方法
  8. Function.prototype.call.call(fn1); // 1
  // 如果出现两个及以上call，那最后运行的就是传进去的函数

+ apply
    > 他和call方法一样，只不过第二个参数必须是数组或者类数组(传入数组，但是fn实际接收到的仍然是一个一个接收)
    ```
    function fn(n,m){
            console.log(this, n, m)
        }
    fn.apply(1, [20,30])
    ```

+ bind (预处理this)
   > 这个方法也是改变this指向的，在bind函数中将fn进行了包装和处理，提前改变实例函数的this指向，并不会让实例函数执行，他的返回值是改变this之后的新函数
   > bind在IE8以下不兼容
   ```
    let box = document.getElementById('box');
    let fn = function(){
        console.log(this)
    };
    let obj = {}
    box.onclick  = fn.bind(obj)

    fn = fn.bind(obj)
    fn()
    // let ww = fn.bind(obj)
    console.log(ww === fn) // false
    ```

**案例call重构**见js老师课件第二周第二天

## 求数组的最大值
```
let ary = [2,3,4,1,2,4,2,1,9]
//1.Math.max,ES6的展开收缩运算符
console.log(Math.max(...ary))
//2.sort
console.log(ary.sort((a,b)=>b-a)[0])
//3.apply (1.改变this指向 2.解决传参的方式)
console.log(Math.max.apply(null,ary))
//4.比较
for(var i=0;i<ary.length-1;i++){
   if(ary[i]>ary[i+1]){// 找到前面一项比后一项大的情况；把最大值放到数组的最后面；
    // var  temp = ary[i];
    // ary[i]=ary[i+1];
    // ary[i+1]=temp;
    // 交换位置
    var a = ary[i]+ary[i+1];
    var b = ary[i]-ary[i+1];
    ary[i]=(a-b)/2;
    ary[i+1]=(a+b)/2;
    }
}
```

## 原型继承
让类B的原型指向类A的实例，那么以后类B的实例既可以调取类A实例的私有属性，也可以调取类A实例的的公有属性，那这种继承方式就是原型继承
> 这种方式不可以使用到内置类，因为内置类原型不能修改
```
function A(){
    this.getX = function(){
        console.log('恭喜发财')
    }
};
A.protopyte.getY = function(){
    console.log('妮儿，你长得可俊哩')
};
function B(){}
B.prototype = new A;
let f = new B;
f.getX();
f.getY();
```

## 中间类继承 (IE10以下不兼容)
arguments虽然不是Array的实例，但是我们可以手动把arguments的__proto__指向Array的原型，那这样arguments就可以使用Array原型上的方法了，这就是中间类继承
> 中间类继承只能继承公有属性
```
function fn(){
    arguments.__proto__=Array.prototypr;
}
console.log(arguments.push(23))
console.log(arguments)
```

## call继承
> call继承只能继承类中的私有属性
```
function A(){
    this.x = 10
}
A.protopyte.getX = function(){
    console.log('万事如意')
}
function B(){
    // this->当前实例
    /* 
    类B当做构造函数执行时，此时的this是当前实例，
    */
    this.a=20
    A.call(this)// 把函数A当做普通函数执行，并且把函数A的this指向了类B的实例
}
 let f = new B;
// 类B的实例继承了类A的私有属性，但是不能使用类A的公有属性
// 类B的所有实例都可以使用类A的私有属性
// console.log(f)
// f.getX()
```

## 寄生组合继承
> 使用call继承了私有属性，object.create继承了公有属性，这种继承方式就是寄生组合继承
> object.create(context)://创建一个空对象，让对象的__proto__指向你传的第一个参数
```
 var obj = {age:1,hh:"欢迎你"}
// Object.create   Object.keys
var o = Object.create(obj);// 返回一个新的对象 o 的__pro
console.log(o);// {__proto__:{age:1,hh:"欢迎你",__proto__:Object.prototype}}

function A(){
}
A.prototype.getX = function(){
    console.log(100);
}
function B(){
    A.call(this)// 继承私有属性
}
B.prototype = Object.create(A.prototype);// 继承公有属性；
// 为了防止修改B的原型时，修改了A的原型，所以使用Object.create的方法；
B.prototype.getY = function(){
}
var b = new B;
```

**案例：3、call的阿里面试题、4、类数组转数组、5、求一组数的平均数、9、sort的案例**

## ES6
1. let和const
 + let和const没有变量提升，var有变量提升
 + let和const不能重复声明，var可以(代码执行之前会进行过滤，如果有重复声明，就报错)
 + let可以解决暂时性死区
 + let可以形成块级作用域(大括号结合)
 + let声明的变量只在当前作用域有效
 + var在全局作用域下声明变量会给window增加键值对，let不会
 + const定义的常理必须赋值
```
function fn(){
    //即使函数没有执行，在代码执行之前会进行过滤，如果有重复声明，就报错
    let a = 100;
    let a = 1;
}


```

2. 箭头函数
 + 箭头函数没有this
 + 没有arguments
 + 箭头函数不能被new
 + 箭头函数不能作为generator
 + 如果在箭头函数里使用this，那他就会往上一级作用域查找this
 + 如果只有一个形参，可以去掉小括号
 + 如果只有return一行代码，可以省略return和大括号
 + 如果return的是一个对象，你要是省略的话，就给对象加小括号
 + 给函数的形参赋默认值(普通函数和箭头函数都可以)
```
let fn = () => {
    console.log(this)
}
fn()

let obj = {
    ame:3,
    fn:function(){
    // this->obj
    return ()=>{
    console.log(this)
    }
    }
}
```

3. ...运算符
 + 收缩运算符
 + 展开运算符
 + 扩展运算符
```
function fn(...g){
        console.log(g)
    }
fn(...[12,34,46,67,78,132,32,34])

let ary = [12,23,45,66];
// let n = ary[0]
// let m  =[]
// 前提是等号的左边和右边结构的一样
let [m,...a] = ary;
console.log(m,a) // 12 , [23, 45, 66]

// 我想拿到数组的第一项和最后一项
// let [x,,,s] = ary;
console.log(x,s)
let ary = [12,234,45,[23,435]];
console.log(ary[3][1]) // 435
let [m,,,[,x]] = ary
console.log(m,x) // 12, 435


普通对象的解构赋值
let obj = {
    name:2,
    age:3
}
let obj1 = {...obj}
console.log(obj1) // 克隆obj

//在左边的对象里定义变量名，如果这个变量名在右边的对象里有对应的属性名，那就把对应的属性值赋值给左边的变量名
//如果右边没有这个属性名就是undefined
//还可以给左边的变量赋默认值
let {name,age,we = 9} = obj;
console.log(name, age,we);

let ary = [1,2,3];
let  [m, , , r = 6] = ary
console.log(m,r)
    
let obj = {
    name:3,
    age:4
    }

let obj = {
    name:'erYa',
    age:18,
    friends:['xioaHua', 'gouDan']
}
let {friends:[,s]} = obj
console.log(s) // 'gouDan'
```

4. class自定义类
```
class Fn {
    // 这里边放的是实例的私有属性
    constructor (n,m){
        this.s = n // 给实例增加私有属性
    }
    // 直接在外边写就是给实例添加公有属性(如果赋的值不是一个方法，那就是给实例增加私有属性)
    getX(){
        console.log(111)
    }
    e = function (params) {
        console.log(444)
    }
    r = 4 // 用等号的形式就是给实例增加私有属性
    w = {g:333}
    static m = 10 // 把Fn当做对象，增加键值对
}
```
5. 模板字符串(``)
```
let ss = 25;
let str = '<li>'+ss+'</li>';
    '<li><span>'+ss+'</span><span>'+ss+'</span></li>' //旧
let str = `<li><span>${ss}</span><span>${ss}</span></li>` //新
```

## JSON
+ JSON数据格式：他不是数据类型，它是一种数据格式
+ 页面都是动态渲染的；是前端通过请求后台的数据库，后面把最新的数据返回，前面接受到后端返给的数据，然后进行字符串拼接，渲染到页面上；
+ 后端返回给前端数据格式一般都是JSON格式；
+ JSON数据格式
    - ：json格式的对象
    - ：json格式的字符串
+ JSON.parse:把json格式的字符串转换为json格式的对象
+ JSON.stringify:把json格式的对象转换为json格式的字符串
```
这个是JSON格式的对象
    var  obj ={"name":"hello","str":"world"};
这个是JSON格式的字符串；
    var str = '{"name":"hello","str":"world"}';
JSON.stringify : 将JSON格式的对象转成JSON格式的字符串
    console.log(JSON.stringify(obj));
JSON.parse: 将JSON格式的字符串转成JSON格式的对象
    console.log(JSON.parse(str))
```
**深克隆 ：两个对象是独立的，互不影响;**
```
    var newObj = JSON.parse(JSON.stringify(obj));
    obj.a.c=2;
    console.log(newObj);
```
**案例新商城排序(重) 见老师课件正式课第二周第四天**

## dom的回流和重绘
1. DOM 映射： 页面中的元素和JS中元素对象有一一映射的关系，当操作或移动JS的元素对象时，页面的标签元素也会跟着发生改变；这就是DOM映射的机制；
2. dom的回流:当页面的dom产生变化(增加，删除，改变位置，改变大小)都会引发dom的回流，所谓回流，就是把dom重新排列进行渲染，他会非常消耗性能的
3. 重绘：当某一个dom元素的样式发生改变(比如元素的样式，背景 字体颜色 透明度等)，不会引起dom的回流，但是会重新绘制
```
let box = document.getElementById('box');
        console.time()
        for (var i = 0; i < 10; i++) {
            var cur = document.createElement('li');
            cur.innerHTML = 111;
            box.appendChild(cur);
        }
        console.timeEnd()

        console.time()
        let frg = document.createDocumentFragment(); // 创建一个文档碎片；
        // 创建一个空容器，用来存储dom元素
        console.log(frg)
        for (var i = 0; i < 10; i++) {
           var cur = document.createElement('li');
           cur.innerHTML = 111;
           frg.appendChild(cur);
        }
        console.log(frg)
        box.appendChild(frg);
        console.timeEnd()
```

## 数据绑定：将后台返回给前端的数据进行展示
> 元素的原型链：a -> HTMLDivElement -> HTMLElement -> Element -> Node -> EventTarget -> Object

```
 <ul id="list"></ul>

var  ary = ["正在直播：习近平出席庆祝澳门回归祖国20周年大会","庆祝澳门回归祖国20周年文艺晚会在澳门举行 习近平出席观看","一国两制为啥在澳门成功了？何厚铧道出了这一根本支柱"];

1. document.createElement
let list = document.getElementById('list');
for(let i = 0;i < ary.length;i++){
    //每循环一次，都会引发一次回流
    let curLi = document.createElement('li');
    curLi.innerHTML = ary[i];
    list.appendChild(curLi);
}

2. document.createDocumentFragment 文档碎片
//相当于js储存dom的一个容器，引发一次回流

let list = document.getElementById('list');
let frg = document.createDocumentFragment();
for(let i = 0;i<ary.length;i++){
    let curLi = document.createElement('li');
    curLi.innerHTML = ary[i];
    frg.appendChild(curLi);
}
list.appendChild(frg);
frg=null;

3. 字符串拼接 
//innerHTML：能识别标签

let list = document.getElementById('list');
var str = '';
for(let i=0;i<ary.length;i++){
    str += '<li>'+ary[i]+'<button a='123'>删除</button><li>'
}
list.innerHTML = str;

4. 模板字符串
let list = document.getElementById('list');
let str = ``;
for(let i=0;i<ary.length;i++){
    str += `<li time='abc'>${ary[i]}<button>删除</button></li>`
}
    list.innerHTML = str;
    
// 字符串也会引发DOM的回流；只不过只引发一次；
// 在框架项目之前，数据都采用模板字符串的方式进行绑定
```


# 正则
> 正则是js的内置类RegExp
> 正则就是处理字符串的规则，它的特长在于处理复杂的字符串
> 1、正则定义了一个字符串的模型。
> 2、正则的第一个作用是“验证某字符串是否和这个模型相匹配”（test：匹配一个字符串是否满足这个规则，如果满足于返回true，反之返回false）
> 3、正则的第二个作用是“把匹配到的内容找出来”。（exec：捕获）
> 其实正则只是定义了一个字符串的模型，至于如何去验证字符串和查找字符串，是正则类上的方法完成的。

## 正则的创建方式
1. 自变量的创建方式
```
let reg = /^$/
```
2. 构造函数创建方式
 > 传递的参数是一个字符串
 > 利用字符串可以拼接的特点，能够实现正则传递变量(两个斜杠包起来的都是元字符，如果正则中要包含某个变量的值，则不能使用自变量方式创建)
```
let reg = new RegExp('')
       
let m = 'moon';
let reg1 = /^$/
let reg = new RegExp('^'+m+'/d$')
console.log(reg)
```

## 正则由两部分组成：元字符和修饰符
+ 修饰符：就是把正则额外的修饰一下
    - i(ignoreCase): 忽略单词大小写匹配
    - m：多行匹配
    - g(global)：全局匹配
+ 元字符：量词元字符、普通元字符、特殊元字符
    - 量词元字符：代表出现的次数
        + *:代表0到多次
        + +:出现一到多次
        + ?:出现0到1次
        + {n}:出现n次
        + {n,}:至少出现n次
        + {n,m}:出现n到m次
    - 特殊元字符：单个或者多字符组合在一起具有特殊意义
        + \:转义字符，可以把普通元字符字符转换为特殊的元字符，也可以把特殊元字符转换为普通元字符
        + .:除了换行符以外的任意字符
        + ^:以什么什么开头
        + $:以什么什么结尾
        + \n:换行符
        + \d:0-9之间的一个数字
        + \D:非0-9数字的任意字符
        + \w:数字、字母、下划线
        + \W:非数字、字母、下划线
        + \s:空白字符(包含换页符，空格，制表符等)
        + \t:制表符(一个TAB键：四个空格)
        + \b:单词边界
        + \B:非单词边界
        + x|y:取x、y中的任意一个
        + [xyz] 取x、y、z中的任意一个 
        + [a-z] 在a到z范围内取一个
        + [^a-z] 在a到z范围外取一个
        + ():分组，改变了正则处理的优先级,分组捕获
        + (?:):只匹配不捕获
        + (?=):正向预查
        + (?!):负向预查
        + []:中括号出现的字符一般都代表他本身
    - 普通元字符：代表本身含义
        + let reg = /name/ 此正则匹配的就是"name"

## 元字符详细解析
  + x|y在正则中的作用
    ```
        let reg = /^18|29$/
        console.log(reg.test('18')) // true
        console.log(reg.test('29')) // true
        console.log(reg.test('189')) // true
        console.log(reg.test('129')) // true
        console.log(reg.test('28')) // false
        //直接x|y会存在很乱的优先级问题，一般我们写的时候都伴随着()进行分组

        let reg = /^(18|29)$/
        console.log(reg.test('18')) // true
        console.log(reg.test('29')) // true
        console.log(reg.test('189')) // false
        console.log(reg.test('129')) // false
        console.log(reg.test('28')) // false
        //加()只能是18或29
    ```

  + []在正则中的作用
    ```
        1、中括号里放的一般都是普通字符
        let reg = /^[@+]$/
        console.log(reg.test('+')) // true
        console.log(reg.test('@')) // true

        let reg = /^[\\d]$/
        console.log(reg.test('d')) // true
        console.log(reg.test('\\')) // true
        //\d比较特殊在[]还是0-9的意思 

        2、中括号不允许出现多位数
        let reg = /^[12-57]$/  //  1  2-5 7
        console.log(reg.test('30')) // false
        console.log(reg.test('1')) // true
        console.log(reg.test('4')) // true
        console.log(reg.test('7')) // true
        console.log(reg.test('6')) // false
    ```

  + 转义字符(\可以把在正则中有特殊意义的字符转义为普通字符，也可以把普通字符转换以有意义的字符)
    ```
    let reg = /^23\.45$/
    console.log(reg.test('23e45')) // false
    console.log(reg.test('23.45')) // true
    ```
 
  + ()在正则中的作用
    + 改变优先级
    + 分组捕获
    + 分组引用
```
正则的捕获：
let reg = /^[a-z]([a-z])\1$/
    console.log(reg.test('see')) //true

```

  + ?在正则中的作用
    + 问号左边是非量词元字符:本身代表量词元字符，出现0到1次
    + 问号左边是量词元字符:取消捕获时候的贪婪性
    + (?:) 只匹配不捕获
    + (?=) 正向预查
    + (?!) 反向预查

## 常用正则表达式
 + 手机号匹配
    ```
    let reg = /^1[3-9]\d{9}$/
    /* 
    1、十一位数字
    2、第一位是1，第二位是3到9的数字
    */
    console.log(reg.test('15231105887'))
    ```

 + 1、匹配有效数字：1、1.5、+2、0、-1
        1、开头有可能是+-号，也有可能没有    ?
        2、如果是个位数[0-9]   两位数 ([1-9]\d+)
        3、小数  (\.\d+)? 可以不出现，也可以出现1次
    
    ```
      let reg = /^[+-]?(\d|([1-9]\d+))(\.\d+)?$/
      console.log(reg.test('2')) // true
      console.log(reg.test('2.5')) // true
      console.log(reg.test('-2')) // true
      console.log(reg.test('+2')) // true
      console.log(reg.test('2.')) // false
      console.log(reg.test('2..')) // false
      console.log(reg.test('3.1415926')) // true
    ```

 + 2、匹配密码
        1、6到16位组成
        2、由数字、字母、下划线组成
        let reg = /^\w{6,16}$/
        
    ```
       function fn(str){
           if(str.length<6 || str.length>16 ){
            alert('密码不符合规范');
            return
           }
           let ary = ['2','_','....'] // 由数字、字母、下划线组成
           for (var i = 0; i < str.length; i++) {
                if(!ary.includes(str[i])){
                    alert('密码不符合规范');
                    return
                }
           }
       }
    ```

 + 3、邮箱
        let reg = /^[a-zA-Z0-9-_]+@[a-z0-9]+(\.[a-z]+)+$/
        12344@qq.com

    ```
        let reg = /^[a-zA-Z0-9-_]+@[a-z0-9]+(\.[a-z]+)+$/;
        console.log(reg.test('12344@qq.com.cn')) // true
        console.log(reg.test('12344@qq.com')) // true
        console.log(reg.test('12344@qq..com')) // false
        console.log(reg.test('@qq.com')) // false
        console.log(reg.test('-@qq.com')) // false
    ```

 + 4、匹配中文名字  [\u4E00-\u9FA5]
            let reg = /^[\u4E00-\u9FA5]{3,6}(·[\u4E00-\u9FA5]{2,6}){0,2}$/
    
    ```
        let reg = /^[\u4E00-\u9FA5]{2,6}(·[\u4E00-\u9FA5]{2,6}){0,2}$/;
        console.log(reg.test('爱新觉罗·溥仪'))
        console.log(reg.test('阿诺德·施瓦辛格'))
    ```

 + 5、身份证：
        1、18位
        2、前6位是省市
        3、中间8位是生日
        4、倒数四位
            1、前两位是公安局代码
            2、第三位是性别，奇数是男，偶数是女
            3、最后一位是数字，有可能是X
    ```
        let reg = /^\d{17}(\d|X)$/
        let reg1 = /^(\d{6})(\d{4})(\d{2})(\d{2})\d{2}(\d)(?:\d|X)$/;
        ?:  只匹配不捕获,  不加括号也不捕获
        let reg2 = /^(\d{6})([1-2]\d{3})((0[1-9])|(1[0-2]))((0[1-9])|([1-2][0-9])|(3[0-1]))(\d{2})(\d)(\d|X)$/;
    ```

## 正则的捕获
> exec：他是正则实例的一个公有属性，他是用来捕获符合规则的字符串的
 1. 返回值：是一个数组，如果捕获不到就是null
 2. 如果是数组
    1、第一项是最大的捕获内容
    2、以后数组的后几项就是分组捕获的内容
    3、index是第一次捕获位置的索引
    4、input是原字符串
 3. 如果你只匹配不捕获，就在小括号里加?:
 4. exec只能捕获到第一次出现的符合正则规则的内容(这是正则捕获的懒惰型，默认只捕获第一个)

> match:他是字符串的一个方法，在String类的原型上，这个方法传递一个正则，返回的是一个数组
 + 如果正则不加g，跟exec返回值一样
 + 如果加上g会把每一次捕获到的内容放到一个数组里返回
 + 缺点：多次匹配的情况下(加上g)，如果要进行分组捕获，那他就拿不到分组捕获的内容了

> replace
```
let str = 'zhufeng33zhufeng33';
let reg = /[a-z]+/g
str = str.replace(reg,function(content){
    console.log(content)
    console.log(arguments)
    1.正则匹配几次，回调函数就执行几次
    2.当执行的时候，他会把捕获的内容当作回调函数的实参传给回调函数
    3.回调函数的返回值(就是return后面的东西)就替换当前捕获到的内容
    return 'zhufengpeixun'
})
console.log(str)

let str = 'good day';
let reg = /\b([a-z])/[a-z]+\b/g
str = str.replace(reg,(word,firstWord) =>{
    console.log(word,firstWord)
    1.先把首字母转大写
    2.截取单词第一项往后的单词
    3.把转大写的首字母和截取到的字母拼接到一起
    4.用拼接后的单词替换捕获到的内容
    firstWord = firstWord.toUpperCase();
    word = word.slice(1);
    reture firstWord + word
})
console.log(str)
```

> 正则的懒惰性
 + 如果正则不加g,那每一次去捕获，捕获到的都是第一次符合规则的内容lastIndex的值不会变，都是0
 + 如果正则加上g，那每捕获一次，正则的lastIndex就会记录当前捕获到的内容的最后一项索引，下次再捕获的时候从记录的索引的基础上+1，继续捕获

> 正则的贪婪性
 + 正则在匹配的时候能多匹配一个就多匹配一个，这就是正则的贪婪性
 + 在量词元字符的右边加?,那就是取消正则的贪婪性(按照正则匹配的最短结果来获取)
```
 let str = 'zhufeng2019zhufeng2020';
 let reg1 = /\d+/g
 let reg = /\d+?/g
 console.log(str.match(reg)) // ["2", "0", "1", "9", "2", "0", "2", "0"]
 console.log(str.match(reg1)) // ["2019", "2020"]
```

**案例myexec 正则的捕获 replace捕获 queryUrlParams 字符串时间格式化**

## js盒子模型
 1. client系列
    + 它不受内容溢出的影响
    + 获取的是数字，而且没有单位
    + 他的值必须是整数，四舍五入
    + 是可视区域的宽度或高度
  - clientWidth: 当前元素可视区域的宽度  宽度+左右padding
  - clientHeight:当前元素可视区域的高度  高度+上下padding
  - clientLeft:获取当前元素左边框的宽度
  - clientTop:获取当前元素上边框的宽度
```
// 获取当前浏览器可视窗口的宽度和高度
// document.documentElement获取当前的html
let w = documentElement.clientWidth || document.body.clientWidth
let h = documentElement.clientHeight || document.body.clientHeight
```

 2. offset系列
    + offsetWidth:当前元素的总宽度  clientWidth + 左右border
    + offsetHeight:当前元素的总高度  clientHeight + 上下border
    > offset的偏移量
     + offsetParent:父级参照物
     + offsetLeft：左偏移量 :从当前元素的左外边框到父级参照物的左内边框
     + offsetTop：上偏移量 ： 从当前元素的上外边框到父级参照物的上内边框
     + body的父级参照物是null
     +  一般情况下所有的父级参照物都是body，如果给元素加上position属性(relative，absolute、fixed)，会让他的所有子孙元素的父级参照物都指向当前这个元素
    **案例offset偏移量**

 3. scroll系列
    + scrollHeight:如果当前元素的文本不溢出，那就等于clientHeight，如果当前元素溢出了，那就是当前的高度+上padding
    + scrollWidth:如果当前元素的文本不溢出，那就等于clientWidth，如果当前元素溢出了，那就是当前的宽度+左padding
**这11个属性是可读属性，只能读不能写**

   + scrollLeft:当前元素横向滚动条卷去的长度
   + scrollTop:当前元素纵向滚动条卷去的高度
   + 它俩既可读，又可写


## getCss
> 获取元素的css样式
 1. 元素.style.width 这是获取的行内样式
 2. getComputedStyle
    + 他是window上的一个属性
    + 他既能获取样式表里的样式，也能获取行内的样式
    + getComputedStyle(元素).属性名
 3. currentStyle
    + 这个属性只在IE下存在
    + 元素.currentStyle.属性名
    + 他既能获取样式表里的样式，也能获取行内的样式

