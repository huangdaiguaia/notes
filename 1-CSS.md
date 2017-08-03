###CSS

###块 内联 可变

**1.块**[div p ul li]

- display:block;
	+ 块级元素独占一行	
	+ 块元素内可放内联元素和块元素
	+ 宽度自动填满其父元素的宽度 

**2.内联**[a span strong em img input label]

- display:inline;
	- 行内元素排列在同一行中,直到这行排不下才换行 
	- 内联元素内可放文本和内联元素
	- 宽高 
		- width height 无效
	    - padding margin竖直方向无效

- display:inline-block;
	+ 元素呈现为内联对象
	+ 周围元素保持在同一行
	+ 但可以设置宽度和高度地块元素

**3.可变**(可根据上下文语境):[button]

**4.属性的可继承性**  所有元素可继承：visibility和cursor

不可继承的： |块状元素可继承  |内联元素可继承  |列表        |表格   
-------------|----------------|----------------|------------|--------------    
display      | text-indent    |text			   |list-style  |border-collapse   
margin	     | text-align     |font
border					  	  |color
padding					  	  |line-height
background				  	  |white-space
height					  	  |direction
width    				  	  |word-spacing
left						  |letter-spacing
right
top 
bottom  				  	  
overflow
position
z-index
float
table-layout
vertical-align
page-break-after 
page-bread-before
unicode-bidi。

**5.权重** 

类型                     |权重
-------------------------|------
内联                     |权重1000
ID 选择器 权重           |100
类 伪类 属性选择器 权重  |10 
类型选择器 权重			 |1

- 除!important ，内联权重最大！
- css样式选择器的优先级相同时，后面定义的样式生效

***

###定位

* 定位元素 默认后者层级高于前者; z-index:[number]设置定位层级 
* 让一个元素在他父亲元素的正中间  

***
	css:
	top:50%;
	left:50%;
	margin-top:-整个盒子自身高度的一半;[注意不要忘了边框和内边距]
	margin-left:-整个盒子自身宽度的一半;

**position:relative;  相对定位**

* 如果没有定位偏移量，对元素本身没有任何影响；
* 定位元素位置控制[沿着这个盒子原来的位置移动]

**position:absolute;  绝对定位**

* 使元素完全脱离文档流；
* 使内嵌支持宽高；
* 不设置宽度的时候宽度由内容撑开[绝对定位内部元素不继承父级宽度，而是靠内容自动撑开宽度]
* 
* 如果有定位父级相对于发生偏移，没有定位父级相对于整个文档发生偏移；
* 定位父级--相对/绝对都有效

**position:fixed； 固定定位**

* 与绝对定位的特性基本一致，差别是始终相对整个文档进行定位；
* 问题：IE6不支持固定定位；

***
###浮动

**float** 脱离文档流

* 使块元素在一行显示
* 使内嵌支持宽高
* 不设置宽度的时候宽度由内容撑开
* 
* 提升层级半层

**inline-block**

* 使块元素在一行显示
* 使内嵌支持宽高
* 不设置宽度的时候宽度由内容撑开
* 
* 换行被解析了
* 在IE6,7下不支持块标签

***
###消除浮动

<!-- - 内联和块性质一样
	+ inline-block
	+ 宽高
	+ 定位
	+ 浮动 -->

* 加高
	- 问题：扩展性不好

* 父级浮动[需要定义宽度?]
	- 问题：页面中所有元素都加浮动，margin左右自动失效

* 给父级加 display:inline-block;
	- 问题：margin左右自动失效

+ 给父级 绝对/固定定位
	* position:absolute;绝对定位元素子级的浮动可以不用写清浮动方法；
	* position:fixed;固定定位元素子级的浮动可以不用写清浮动方法；IE6不兼容

* 空标签清浮动
	- 问题：IE6 最小高度 19px；（解决后IE6下还有2px偏差）

***
	<div class="clear"></div>
	.clear{
		height:0;
		font-size:0;
		clear:both;
	}

* br清浮动
	- 问题：不符合工作中：结构、样式、行为，三者分离的要求。
	- 属于内嵌样式,不符合w3c标准[结构样式行为三者分离]

***
	<br clear="all">
	<br clear="all" />

* **after伪类**[**现在主流方法**]
	+ IE6，7下不兼容
		- :after{
			content"元素内部末尾添加的内容";
		   } 
	+ clear:left/right/both/none 
		- 元素的某个方向不能有浮动元素  
		- clear属性只对块元素起作用
	+ IE6，7 zoom 缩放
		* 触发IE下haslayout,使元素根据自身内容计算宽高。
			+ 可以触发layout的属性
				* display:inline-block;
				* height width:(任何值除了auto)
				* float:(left或right)
				* zoom:(除normal外任何值)
		* FF不支持；

***
	.clear{
		zoom:1;
	}
	.clear:after{
		content:'';
		display: block;
		clear: both;
	}

* 给浮动元素父级加overflow:hidden/auto
	- overflow[有可以包住浮动元素的特点:即把元素提升层级]
	- 问题：需要配合宽度或者zoom:1
	- 问题：
		+ 在IE6 7下父级的overflow:hidden 没有包住**子级浮动元素**
		**子级的相对定位**的功能
			+ ie6 下父级的overflow:hidden 是包不住子级的相对定位的
			+ 解决办法:给父级也加上定位(相对一般)


* 给父级 定义 display:table;

***
###IE6 7

- 在IE6 7 下浮动元素的父级有宽度就不用清浮动;

- 在 IE6 下定位元素的父级宽高都为奇数那么在 IE6 下定位元素的 right 和 bottom 都有1像素的偏差。

- **inline-block**的IE6 7兼容性问题：  
	+ 原因:使用display:inline-block在IE下会触发layout
	+ 触发了layout，而它本就是行布局，所以触发后，块元素依然还是行布局，而不会使块元素呈递为内联对象
	+ 注:IE6 zoom缩放		
		* 触发IE下haslayout,使元素根据自身内容计算宽高。
			+ 可以触发layout的属性
				* display:inline-block;
				* height width:(任何值除了auto)
				* float:(left或right)
				* zoom:(除normal外任何值)
	* 解决办法:

***
	div {display:inline-block;}
	div {display:inline;}   
	//或者
	div {display:inline; zoom:1;}

- **IE6双边距BUG**
	+ IE6下块标签浮动并且有横向margin时:横向的margin值会被放大为两倍：
	+ 解决办法: display:inline;

- **IE6 li部分兼容性问题**：
	+ 在IE6，7下li本身没浮动,但是li内容有浮动的时候，li下边就会产生几px的间隙
		+ 解决办法:
		+ 给li加浮动
		+ 给li加vertical-align:top; //middle bottom
		
    + 左右两列布局，右边右浮动时:IE6 IE7下折行；
    	* 解决办法:
    	* 左边元素浮动
    	* 在IE6 7 下元素浮动，要并在同一行的元素都要加浮动
  
- **在IE6下高度小于19px的元素**,高度会被当做19px来处理
	+ 解决办法:
	+ 1.font-size:0;//但只能处理到最小2px的高度
	+ 2.overflow:hidden;

- **IE6 7 的input框文字偏上**
	+ 设置高度与行高相同
		* 字体大小设置为偶数或line-height为偶数，不然IE6还是会出现错位
		* line-height:32px/9;；
	+ 输入框的文字居中，可用内边距来设定
  

###OTHER

- **vertical-align**
	+ 居上对齐 top
	+ 居中对齐 middle
	+ 同排元素都要加
	+ 可以解决元素下方间隙问题
	+ [对浮动元素无效 若不想让浮动元素顶部对齐 只能通过设置margin]

***
**图片**

- 图片下方间隙问题
- display:block; (改变标签本身特性)
- overflow:hidden; (必须知道图片高度)
- vertical-align (暂时最完美的方案)
- img{vertical-align:bottom; display:block}
- 设置容器font-size:0(个人认为这种方法最好！！！)

- a标签包图片会有边框 所以
	`img{
		border:none;
	}`

***	
**input**

- **input需要清掉的默认样式**

***
	input{
		margin:0;
		padding:0;
		outline:none;
		boder:none;
		background:none;
	}

- **单选框和复选框对其问题** 让后面的登陆按钮和上面的input对齐
	+ 可以直接使用margin属性来暴力定位
	+ 使用top属性来定位，但要同时给position:relative;；

***
- **按顺序选元素**

***
	li:last-child{
	    border-right: none;
	}
	first-child
	nth-child(2)

- **不透明度**
	- 标准   
		+ opacity: 0~1;
		+ opacity: 0.8;
	- IE     
		+ filter: alpha(opacity=0~100);
		+ filter: alpha(opacity=80);

- **white-space:nowrap;**段落中的文本不进行换行

- **文字长的部分变成点点点**:

***

	{
	  	text-overflow:ellipsis;
		overflow: hidden;
		white-space: nowrap;
	}

- **经验**
	+ 在给span设置宽度的时候 一定不要忘记display:block;
	+ 设置宽高 [left top] 时不要忘记加px
	+ 一定要注意判断语句if里面是 ==

- **a顺序**: 驴lv 哈ha
	+ a:link是未访问的链接；
	+ a:visited是已访问的链接；
	+ a:hover是鼠标悬停在链接上；
	+ a:active是被选择的链接

- **标签嵌套规范**:
	+ p里不能包含块标签
	+ a中不能再嵌套a

***
- **body|head < html < 文档**
- document 是最顶层的一个虚拟的父节点 包括 ! HTML window??

- 宿主对象
    + 宿主:生活的环境
    + 在js中:宿主即浏览器提供的对象
        * DOM BOM
        * document
        * window

- 内置对象
    + Global[概念性的 只存在书上]
    + Math [不需要new实例化 可以直接用]
        * Math.ceil();

- 本地对象      
    + Array [需要实例化 只能用new出来的实例]
        * var arr=new Array();
        * arr.push();


* DOM: Document Object Model[文档对象模型]
* BOM: Browser Object Model [浏览器对象模型]**window**
* ECMAScriptEuropean Computer Manufacturer's Association[欧洲计算机制造商协会]**global**

***
- **主流浏览器内核私有属性css前缀**
	+ mozilla内核 (firefox,flock等)     -moz
	+ webkit内核(safari,chrome等)       -webkit
	+ opera内核(opera浏览器)            -o
	+ trident内核(ie浏览器)             -ms

- **HTML注释**
	+ <!--注释的内容-->
- **CSS注释**
	+ /* 注释内容 */
- **JS注释**
	+ 单行注释以 // 开头。
	+ 多行注释以 /* 开始，以 */ 结尾。

- **border**
	+ 一个值:四条边
	+ 两个值:上下,左右
	+ 三个值:上,左右,下
	+ 四个值:上,右,下,左

- **&nbsp**:Non-Breaking Space

***





