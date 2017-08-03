
###AJAX

- **127.0.0.1**  localhost

- **ajax** : 
    + Asynchronous JavaScript and XML 
    + 异步JavaScript和XML[用javascript异步形式去操作xml]

- **txt文件utf-8编码**
    + 服务器端[即www文件夹]txt文件编码 改成和网页一样的utf-8编码 
    + [文件->另存为->utf-8]

- **eval就是计算字符串里的值**

***
    status
    n.    地位; 身份; 情形，状态;

    state
    n.    国家; 州; 状况，情况; 资格;
    vt.   规定; 陈述，声明;
    adj.  国家的; 国务的，公务的; 正式的;
    
    //ie6以下 ActiveXObject是有很多动能的插件  Microsoft.XMLHTTP要用的插件名字
    try {
        xhr = new XMLHttpRequest();
    } catch (e) {          //e 为错误信息
        xhr = new ActiveXObject('Microsoft.XMLHTTP');
    }

    var request=new XMLHttpRequest();
    request.open("GET","get.php",true);
    request.send();
    request.onreadystatechange=function(){
        if(request.readyState===4&&request.status===200){
            request.responseText;//做一些事情
        }
    };
    

- **表单：数据的提交**
    + action : 数据提交的地址，默认是当前页面
    + method : 数据提交的方式，默认是get方式
        + get
            * 把数据名称和数据值用=连接
            * 如果有多个的话，那么他会把多个数据组合用&进行连接
            * 然后把数据放到url?后面传到指定页面
            * url长度限制的原因，我们不要通过get方式传递过多的数据
        + post
            * 数据是通过请求头传递过去
            * 理论上无限制
    + enctype : 
        * 提交的数据格式，默认application/x-www-form-urlencoded

***
    <form action="1.post.php" method="post">
    <input type="text" name="username" />
    <input type="text" name="age" />
    <input type="submit" value="提交" />

- **AJAX：数据的提交**[open(方法, url, 是否异步)]
    + get:从服务器获取数据
        * 在url网址中可以看到数据 
        * 适合用来获取 所以数据会被缓存
        * 缓存[被缓存]  
            - 解决缓存问题
            - 在url？后面连接一个随机数，时间戳
        * 数据格式:编码encodeURI
        * 数据放在open()里面作为参数传递

***
    xhr.open('get','2.get.php?username='+encodeURI('刘伟')+'&age=30&'+newDate().getTime(),true);
    xhr.send();

- **AJAX：数据的提交**
    + post:向服务器提交数据
        * 在 http content中可以看到数据 
        * 适合用来提交 所以数据不会被缓存
        * post没有缓存问题 
        * 数据格式[申明发送的数据类型]:无需编码
        * 数据放在send()里面作为参数传递

***
    xhr.open('post','2.post.php',true);
    xhr.setRequestHeader('content-type', 'application/x-www-form-urlencoded');
    xhr.send('username=刘伟&age=30');

- **表单和ajax**
    + 功能类似 而不是关联 上下级一起完成一些事
        * 表单:从前端向后端[服务器]提交数据
        * ajax:从后端获取数据 显示在前端

- **后端**:
    + 可以自己就储存数据
    + 可以从form表单获取数据
    + 可以通过open() send()中获取数据

- **接口**:
    + localhost/miaov/2014-ajax/guestbook/index.php?&a=verifyUserName
    + localhost/miaov/2014-ajax/guestbook/index.php?m=index&a=verifyUserName&- username=leo

- J**SON字符串->JSON对象**
    + **json**:{"name":value,...}  [name 必须用双引号] 
        * stringify : 可以把一个对象转成对应字符串
        * parse : 可以把字符串转成对应对象
    + **eval**
    + 字符串解析成js代码并运行[避免使用 不安全 耗性能]
    + JSON字符窜->JSON对象  var obj=eval('('+str+')');

***
- **JSONP** : JSON with Padding
    - script标签[script标签调用函数]
    - 用script标签加载资源是没有跨域问题的

- 提前定义好的一个全局函数(数据) 不然在这里执行不了 涉及作用域的问题
- 按需加载远程资源[DOM创建script标签]

***
    var oScript = document.createElement('script');
    oScript.src = '2.txt';
    document.body.appendChild(oScript);

    var oScript = document.createElement('script');
    oScript.src = 'http://api.douban.com/book/subjects?q='+oQ.value+'&alt=xd&callback=fn1';
    document.body.appendChild(oScript);

    http://api.douban.com/book/subjects?q=javascript&alt=xd&callback=fn1

    'https://www.baidu.com/su?wd='+this.value+'&cb=maiov';//window.baidu.sug

    window.baidu.sug({q:"g",p:false,s:["谷歌翻译","gps跟踪前女友","google翻译","github","gta5","google","git","工商银行","赶集网","高德地图"]});

- **Ajax请求响应的HTTP状态码request.status**
    + 1xx：信息类，表示收到web浏览器请求，正在进一步的处理中
    + 2xx：成功，表示用户请求被正确接收，理解和处理。如200 OK
    + 3xx：重定向，表示请求没有成功，客户必须采取进一步的操作
    + 4xx：客户端错误，表示客户端提交的请求有错误，例如，404 not - found，意味着请求中所引用的文档不存在
    + 5xx：服务器错误，表示服务器不能完成对请求的处理，如500
        * 200: OK 正常返回信心
        * 404: Not Found 找不到与url相匹配的资源

- **AJAX和FLASH**
    + Ajax
        * 优势：
            - 可搜索性 
            - 开放性 
            - 费用 
            - 易用性 
            - 易于开发。
        * 劣势：
            - 它可能破坏浏览器的后退功能
            - 使用动态页面更新使得用户难于将某个特定的状态保存到收藏夹中
            - 不过这些都有相关方法解决。

    + Flash
        * 优势：
            - 1.多媒体处理 
            - 2.兼容性 
            - 3.矢量图形 
            - 4.客户端资源调度

        * 劣势：
            - 1.二进制格式 
            - 2.格式私有 
            - 3.flash 文件经常会很大，用户第一次使用的时候需要忍耐较长的等待时间
            - 4.性能问题

###正则表达式[字符串有没有一部分符合要求]

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

***
- **正则RegExp:regular expression**

- **RegExp的方法**:
    + .exec()
    + .test() 返回true或false
 

- **选项**:
    + 全局匹配：g——global
    + 忽略大小写匹配:i-----ignore

- **转义字符**

字符    |   含义   |    eg    |   对比字符  |    eg
--------|----------|----------|-------------|------ --  
.       | 代表所有 |
\d      |  digital |   [0-9]  |       \D    |   [^0-9]                      
\w      |   world  | [0-9a-z] |       \W    |   [^0-9a-z_]                
\s |space 空白字符 | 空格 制表符\t..| \S    |     

- **字符类[]**方括号含义
    + 或者
    + 范围[0-9] [a-z]
    + 除了..之外[^a]

- **量词**

***
    {n,m}
    +  {1,}
    *  {0,}   //不建议使用 会出现问题
    ?  {0,1}

- **其他**
    + 行首 ^
    + 行尾 $
    + 单词边界 \b

###js运动课程

    //30 一般不能太大 不然会一顿一顿的
    clearInterval(timer);
        timer=setInterval(function (){
            var iSpeed=5;

            if(oDiv.offsetLeft>=300)    //是否到达终点
            {
                clearInterval(timer);   //到达终点
            }
            else
            {
                oDiv.style.left=oDiv.offsetLeft+iSpeed+'px';    //到达之前
            }
        }, 30);

- **缓冲运动**[逐渐变慢 最后停止]
    + 计算机接受不了小数 遇见小数 他会挠挠头 直接扔掉
    + 实际上 在计算机内部 小数也是用整数来处理的

***
    var iSpeed=(iTarget-oDiv.offsetLeft)/8;
    iSpeed=iSpeed>0?Math.ceil(iSpeed):Math.floor(iSpeed);

- **匀速运动**

***
    clearInterval(timer);
        timer=setInterval(function (){
            var iSpeed=oDiv.offsetLeft<iTarget?7:-7;

            if(Math.abs(oDiv.offsetLeft-iTarget)<7) //-----------------
            {
                clearInterval(timer);

                oDiv.style.left=iTarget+'px';        //-------------------
            }
            else
            {
                oDiv.style.left=oDiv.offsetLeft+iSpeed+'px';    //到达之前
            }
        }, 30);

- **弹性运动的问题**：如height不能为负[运动过界]

***
###面向对象:

- **多态**:父类和子类有相同的操作 但是这些操作又不是那么一样

- **构造函数**:
    + 构造对象的函数
    + 一般new出来一个对象 
    + 首字母大写

- **工厂方式**
    + 原料
    + 加工
    + 出厂

    + 问题:
        * 在调用这个方式创建对象的时候 没有new [你会发现加了new之后会简单很多]
        * 在工厂方式中的方法是一样的 但创建出来的对象每一个都会和自己绑一个方法
            - 浪费内存

***
        下面两个匿名函数a!=b
        var a=function ()
        {
            alert('a');
        };

        var b=function ()
        {
            alert('a');
        };

        实际上在js上 应该这样写 而这样是new了两次 所以是两个 所以 a!=b
        var a=new Function('alert("a")');
        var b=new Function('alert("a")');
        
        - alert(arr);
          + 会在后台调用toString()方法

        var num=[1,2,3,4,5,6,7,8,9];
        result=num.slice();  //拷贝数组num 不改变原来数组 返回心得拷贝的数组
        alert(result); //1,2,3,4,5,6,7,8,9
        alert(result==num);//false
        result2=num.concat(); //拷贝数组num 不改变原来数组 返回心得拷贝的数组
        alert(result2); //1,2,3,4,5,6,7,8,9
        alert(result2==num);//false

        num2=num;
        alert(num2); //1,2,3,4,5,6,7,8,9
        alert(num2==num); //true


        简写:
        var arr=new Array();
        var arr=[];

        var fun=new Function('alert("a")');
        var fun=function ()
        {
            alert('a');
        };

        var re=new RegExp('a', 'i')         //注意引号 即参数要为字符串
        var re=/a/i;

- **prototype[原型]方式** :
    + 给一个对象的原型添加方法 [扩展系统函数的功能]
    + 解决浪费内存

    - 在其他语言中 类确实和构造函数截然不同

    类[构造函数 那个老师个人认为 ]  |  对象[实例]
    --------------------------------|--------------
    不具备实际的功能只是用来构造对象|  有实际的功能 
    模子                            |  蛋糕
    Array                           |  arr

***
    var arr=new Array();
    arr.push();

    //???不是很懂
    给一类东西加方法[css中的class]
    普通方法
    给一个对象加方法[css中的行间样式]
    arr1.sum=function ()
    Array.prototype.sum=function ()    

- **混合法**
    + 用构造函数添加属性[没有new的工厂]
    + 用原型方式 添加方法

***
- **面向过程的程序->面向对象的程序**
    + 原则
        * 先写出普通的写法，然后改成面向对象写法

    + 普通方法
        * 前提:所有东西都在onload里面

    + 改写普通方法:
        * 函数不能有嵌套 可以有全局变量
        * [把onload中不是赋值的语句放到单独的函数中]

    普通  |面向对象
    ------|--------
    自由[其实是属于window]  |属于一个对象
    变量  |属性
    函数  |方法

    - 改成面向对象

    onload  [初始化整个程序]       | 构造函数[初始化一个对象]
    -------------------------------|------------------------
    全局变量                       |      属性
    函数                           |      方法

- **this**
    - 函数的直接调用者
        + [当前方法属于谁,指向谁]
    - new关键字[指向new出来的对象]
        + 函数前面有new的时候,指向函数默认new出来的对象
    - 事件中[触发事件的对象][IE attachEvent 时 :全局对象Window]

- **关于转换过程this的问题**
    + 要尽量让面向对象中的this指向对象
    + this啥时候会问出问题?
        * 定时器[所有被定时器调用的函数 this指向window]
        * 事件
            - 通过闭包传递this
            - 再套一层  _this
            - 传参
 
    + 问题eg:
        * this.aInput[i].onclick =this.tab; 
        * this.tab 因为不仅仅是一个普通的函数 而是当前对象的方法
        * tab这个函数嫁给了这个按钮
        * 这个式子 使this[在下面的tab方法中]属于按钮 而不再属于new出来的对象

    + 解决办法:把一个匿名函数嫁给按钮

***
    this.aInput[i].onclick =function(){
        _this.tab(this);   //这里的this 是指被点击的按钮
    }

- **各种对象**
    + 宿主对象
        * 宿主:生活的环境
        * 在js中:宿主即浏览器提供的对象
            - DOM BOM
            - document
            - window

    + 内置对象
        * Global[概念性的 只存在书上]
        * Math [不需要new实例化 可以直接用]
            - Math.ceil();

    + 本地对象      
        * Array [需要实例化 只能用new出来的实例]
            - var arr=new Array();
            - arr.push();

###PHP

- php变量不需要定义 可以直接使用
- 字符串可以不加引号 当然加也没问题
- 变量前面一定要有 $
- 字符串连接 用  .         [+]
- 表示 的 用 ->            [.]
- $_GET      系统提供的一个数组 存放用户通过get方式提交是数据
- echo $_GET['user'];   user 对应于前台的name

- MVC

M       |V       |C
--------|--------|---------
Model   |View    |Controlers
模型    |视图    |控制器
数据    |前端标签(HTML CSS JS)|逻辑

###cookie

- 只有ff的cookie在本地也是可以正常运行的 [就不需要服务器了]

###firebug

- 分组

***
    console.group('第一组');
    console.log(1);
    console.groupEnd();

    console.group('第二组');
    console.log(2);
    console.groupEnd();

