###大标题
- **1.小标题**


###JavaScript

  + ECMAScript
  + DOM: Document Object Model[文档对象模型]
  + BOM: Browser Object Model [浏览器对象模型]
  <!--  -->
  + DOM: Document Object Model[文档对象模型]
  + BOM: Browser Object Model [浏览器对象模型]**window**
  + ECMAScriptEuropean Computer Manufacturer's Association[欧洲计算机制造商协会]**global**
  + W3C: World Wide Web Consortium [万维网联盟]
  + API: Application Programming Interface[应用程序编程接口]
  + CSS: Cascading Style Sheets [层叠样式表]
  + XHTML: Extenxible HypenText Markup Language [可扩展超文本标记语言]

###属性

- **1.操作元素标准属性**
    * oTxt.value='123';    [点“.”后面的值无法修改]
    * oTxt['value']='abc'; [中括号[]里面的值可以修改 可以不符合变量命名规则]

- **2.操作元素非标准属性**
    - 设置:setAttribute 
        * oTxt.setAttribute('value', 'rtertw');
    - 获取:getAttribute 
        * oTxt.getAttribute('id');

- **3.元素对象的js属性**
    + obj.tagName     
        * 标签名:h1
    + obj.innerHTML   
        * 标签里面的内容:linux is <i>very</i> much!
    + obj.textContent 
        * 标签里面的文本 不要里面的HTML代码:linux is very much!
    + obj.outerHTML   
        * 标签的html代码:

***
      * <h1 info='linux is very much!' id='hid' - class='hcls'>linux is <i>very</i> much!</h1>
    
***
###一.样式

  + **1.js中加样式**:
    * obj.style.cssText = ' width:200px; height:200px; ';
    * obj.style.display = 'block';
    * obj.className = "active"; 
    * setAttribute
        + obj.setAttribute("class", "active");
        + obj.setAttribute("href","css2.css");
        + div.style.setProperty('width','250px');
    * font-size => fontSize[不允许出现-] 
  
  + **2.JQuery加样式**  
  - 设置 CSS 属性
    - $("p").css("background-color","yellow");
  - 设置多个 CSS 属性
    - $("p").css({"background-color":"yellow","font-size":"200%"});
  - backgroundPosition background-position 都可以
  - left可以加引号,嫌麻烦可以不加;
    + 后面是变量时:变量名后可以加上+'px';
    + 后面是常量时:可以是'常量px';
    + 推荐:
      * left:titleBoxLeft
      * left:-100
    + 最后可以加逗号,一定不能用分号.
  
###OTHER.

- **1.不能作为判断条件**:
    - 背景 颜色[color red #f00] 相对路径

- **2. .actve一直变**

***
    思路一：全部清空，当前添加(很好操作,但浏览器很累)
    for( var i=0; i<aLi.length; i++ ){
      aLi[i].className = '';
    }
    this.className = 'active';

    思路二：清空上个，当前添加
    oldLi.className = '';
    oldLi = this;
    this.className = 'active';

- **3.获取dom元素对象的方法:**
    * document.getElementById()
    * document.getElementsByTagName()
    * document.getElementsByClassName()
    * document.getElementsByName()

###二.数据类型

**1.JS中的数据类型**：

  + 数字(NaN)、
  + 字符串、
  + 布尔、
  + 未定义[undefined]

  + 函数、
  + 对象(obj[元素]、[]、{}、null)、

**JS中基本数据类型** [八字节内存] :Number String Boolean Undefined \\ Null
**JS中复杂数据类型**:Object

**typeof返回数据类型**:Number String Boolean Undefined \\Object Function
**instanceof确定是啥对象**: Object Array RegExp
**valueOf**  注意这个是大写的O

**2.注:undefined**

  + 变量被声明但没有被赋值[赋值即初始化] var timer
  + 对象没有赋值的属性                   oBody.timer
  + 调用函数时 没有提供的参数
  + 函数没有返回值时 默认返回undefined

***
    用undefined不会报错 而用一个未声明的变量会报错
    var timer = null;                               // null
    alert(timer);                                     // null
    clearInterval( timer );                       // null

    var timer;                                        //undefined
    alert(timer);                                    //undefined
    clearInterval( timer );                      //undefined

    alert(oBody.timer);                           //undefined
    clearInterval( oBody.timer );             //undefined

    只有这个不可以 最起码要声明
    alert(timer);                                      //报错
    clearInterval(timer );                         //报错


    alert(window.a);    //用一个不存在的属性：undefined
    alert(a);           //用一个不存在的变量：出错

**3.转换成布尔类型**

**真**：[7]
  非0的数字、非空字符串[空格也算非空]、true、函数、能找到的对象、[]、{}

**假**：[7]
  0、NaN、空字符串''、false、不能找到的元素、null、未定义

**4.转换成数字类型**

  0:null
  NaN:undefined

  NaN：not a number 不是个 数字 的 数字类型[NaN与任何值都不相等]

**5.显式类型转换**[强制类型转换]：

  Number()
  parseInt()
  parseFloat()

**6.隐式类型转换**：

  +              | 200 + '3'   变成字符串 1.toString()[连接字符串]  2.Number()[数字相加]
  ---------------|----------------------------------
  - * / %        |'200' - 3    变成数字
  ++ --          |变成数字
   <             |数字的比较 、字符串的比较
  !              |把右边的数据类型转成布尔值
  ==             |

**7.toFixed()** 返回字符串;

**8.HTML 中拿到的内容**类型都是字符串

###OTHER.

**4.重用代码**：[传参,函数内做判断]

  + 尽量保证 HTML 代码结构一致，可以通过父级选取子元素
  + 把核心主程序实现，用函数包起来
  + 把每组里不同的值找出来，通过传参实现

**5.return[函数中]**：返回值

  + 函数名+括号：fn1() ==>  return 后面的值；
  + 所有函数默认返回值：未定义；
  + return 后面任何代码都不执行了；!!!


**6.arguments[函数中]**

    当函数的参数个数无法确定的时候：用 arguments
    function fn1(){
      arguments => [ 1,2,3 ]  实参的集合,不是数组,没有数组的那些方法
      alert( arguments );
      alert( arguments.length );
      alert( arguments[arguments.length-1] );
    }

###字符串:

**不影响原始字符串**

- **字符串模式匹配方法**
    + .match()
        * 在字符串上调用这个方法,本质上与调用RegExp的exec()方法相同
        * 一个参数
            - 正则表达式
            - 一个RegExp对象
        * 方法可在字符串内检索指定的值
        * 找到一个或多个正则表达式的匹配
        * 该方法类似 indexOf() 和 lastIndexOf()
        * 但是它返回指定的值，而不是字符串的位置。

    + .search()返回要查找的字符串第一次出现的位置，没有返回-1

    + .replace( , ) 替换

    + .split()
 
- concat
- slice
- substring
- substr

***
    var str = '妙味课堂-WWW.miaov.com';

    str.charAt(1);                      // '味'

    str.charCodeAt(1);                  // 21619
    String.fromCharCode(22937, 21619);  // '妙味'

    str.indexOf('m', 4);      // 9
    str.lastIndexOf('o');     // 16

    '1000' < '2'              // true
    '1000' > 2                // true

**substring slice 从哪开始 到哪里结束[不包括结束位置]**
**substr 从哪开始 [几P]**

    str.substring(0, 4);      // '妙味课堂'
    str.slice(-3);            // 'com'

    str.toUpperCase();        // '妙味课堂-WWW.MIAOV.COM'
    str.toLowerCase();        // '妙味课堂-www.miaov.com'

    str.split('.', 2);        // [ '妙味课堂-WWW', 'miaov' ]

    var arr = [ 'www', 'miaov', 'com' ];
    arr.join('aaa');          // 'www.miaov.com'

###数组

**1.定义**

    var arr = new Array(3);           //定义了一个长度为3的数组
    var arr = new Array('3');          //定义了一个长度为1 ---[3]----的数组

**2.清空数组**

    arr.length = 0;       //数组的length是可写的 但是字符串是不能的
    arr = [];             //效率更高一点

**3.方法**

- 改变原数组 返回原数组 也可能会返回改变的值
- 不改变原数组 返回新数组 可可能返回别的

**4.不改变原数组**

- **4.0迭代方法**: 
  + filter() 
    * 利用指定的函数 来返回数组中想要的项 
    * 不改变原数组

- **4.1转换方法**:
  + toString()
    * 把数组转为字符串
    * 不改变原数组

  + valueOf
    * 返回数组
    * 不改变原数组

  + toLocaleString()

  + join()
    * 把数组中所有元素放入一个字符串
    * 不改变原数组

- **4.2操作方法**
  + concat()
    * 创建一个数组的副本
    * 连接两个或多个数组
    * 不改变原数组

  + slice()
    * 不改变原数组

  + splice() 
    * 起始位置 要删除的项数 要添加的项
    * 删除 插入 替换
    * 返回被删除的元素
    * **4.2中的叛徒 改变原数组**

**5.改变原数组**

  + **5.1怎么进怎么出**

作用   |数组末尾[屁屁]|    数组开头 |返回
-------|--------------|-------------|--------------               
添加   |push          |    unshift  |返回新数组的长度
删除   |pop           |    shift    |都返回删除的值

    栈方法   LIFO [Last In First Out]   push    pop
    队列方法 FIFO [First In First Out]  push   shift

- **5.2重排序方法**:
  + sort() 
    * 接受一个比较函数作为参数;
    * 默认以字符串来排序;
  + reverse() 颠倒数组中元素的顺序

**eg:排队走[顺着 倒着]**

    var arr = [ 'TM', '钟毅', '张森', '杜鹏', 'Leo' ];
    arr.unshift(arr.pop());
    arr.unshift(arr.pop());

    arr.push(arr.shift())
    alert( arr );
**splice 从哪开始 [几P] 干啥**

    splice   删除[2]、添加[3]、替换[4个参数]  只返回被删除的哥们
    var arr = [ 'TM', '钟毅', '张森', '杜鹏', 'Leo' ];

    arr.splice( 0 , 2 );
    arr.splice( 0, 2, '莫涛 or 钟毅' );
    alert( arr.splice( 1, 0, '钟毅媳妇儿~', '钟毅媳妇们~' ) );
    alert( arr );

**eg:数组去重**

    var arr = [ 1,2,2,4,2 ];
    for ( var i=0; i<arr.length; i++ ) {
      for ( var j=i+1; j<arr.length; j++ ) {
        if ( arr[i] == arr[j] ) {
          arr.splice( j, 1 );
          j--;
        }
      }
    }
    alert( arr );
***

###JSON0[JavaScript Object Notation][记号 标记法]

**1.提倡的写法 更安全**

    var json2 = { name : 'miaov' };
    var json2 = { 'name' : 'miaov' };

**2.用中括号的时候 都要加引号**

    alert( json2.name );
    alert( json2['name'] );

**3.遍历**

    var json4 = { 'name' : 'miaov', 'age' : 3, 'fun' : '前端开发'  };

    // attr 属性名 'name' 'age' 'fun' ,所以attr不用引号
    for ( var attr in json4  ) {

      alert( attr );
      //相当于alert('name'); alert('age');alert('fun');

      alert( json4[attr] );
      //相当于alert( json4['name']); alert( json4['age']);alert( json4['fun']);
    }

**区别**

  + for in 数组和json都可以用
  + for循环只能数组用[json没有length]

###Math对象

  + Math.floor(3.4);   //向下取整
  + Math.ceil(3.4);    //向上取整
  + Math.round(3.4);   //四舍五入

**随机数**Math.random();产生0~1之间的随机数

    // x ~ y
    var x = 0;
    var y = 10;
    alert( Math.round( Math.random()*(y-x) + x ) );

    // 0~x
    alert( Math.round( Math.random()*x) );

    // 1~x
    alert( Math.ceil( Math.random()*x) );


###OTHER

- **onchange** 是失去焦点且内容改变才会执行函数
- **onblur**   只要失去焦点 就会执行函数

- **json**:命名空间

- **alert(arr)**;
  + 会在后台调用toString()方法

- **简写**:

***
    var arr=new Array();
    var arr=[];

    var fun=new Function('alert("a")');
    var fun=function ()
    {
        alert('a');
    };

    var re=new RegExp('a', 'i')         //注意引号 即参数要为字符串
    var re=/a/i;

- **防止重复点击**
  + 为了防止这个函数没执行完 又点击 再执行一遍

***
    var on =true;

    if(!on){return;}

    on=false;
    
    //????
    onOff = true; //在函数执行完之后设置这个

- **高亮 复原** oldBgColor=this.style.background;

- **层级问题**

***
    var iMinZindex=2;
    obj.style.zIndex=iMinZindex++;

- **自己理解 循环i**
  	* 这个循环是添加点击事件 aLi[i].onclick
  	* 只有for循环执行完了才可以点击  
  	* 所以可以点击的时候 才开始执行后面 
  	* i已经变成3了

***
    for(var i=0;i<aLi.length;i++){ 
      aLi[i].onclick=function(){
          alert(i);                        //3
          this.style.background = 'yellow';
      }
    }
    for(var i=0;i<aLi.length;i++){
      fnWrite(aLi[i]);                      //这里的i每一个都可以成功
    }



