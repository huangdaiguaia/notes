###DOM BOM

- **1.添加节点**

***
    if ( oUl.children[0] ) {
        oUl.insertBefore( oLi, oUl.children[0] );
    } else {
        oUl.appendChild( oLi );
    }

    if(aLi.length==0)
    {
        oUl.appendChild(oLi);
    }
    else
    {
        oUl.insertBefore(oLi, aLi[0]);
    }

- **2.父级**
    + this.parentNode     结构父级
    + this.offsetParent   定位父级

    + offsetWidth    不包括margin的宽
    + offsetLeft     距离定位父级的左边距离

- **3.子节点**
    + 推荐 childern
    + 不推荐 oUl.childNodes[0] 
        * 注意:空的文本节点[即换行] oUl.childNodes[i].nodeType==1  
        * 1:代表是元素节点
        * 3:代表是文本节点

- **4.oFirst兼容性**
    + var oFirst=oUl.firstElementChild||oUl.firstChild;  //ff||

- **oTab.tBodies[0].rows[2].cells[1]**

###距离

可视区尺寸
document.documentElement.clientWidth
document.documentElement.clientHeight
滚动距离
document.body.scrollTop
document.documentElement.scrollTop

对象.scrollHeight/scrollWidth 除开边框以外盒子里面放的东西的宽


###定时器

- 天：Math.floor(t/86400)
- 时：Math.floor(t%86400/3600)
- 分：Math.floor(t%86400%3600/60)
- 秒：t%60

***
- January、February、March、April、May、June、 
- July、August、September、October、November、December

- 数字形式：new Date( 2013,4,1,9,48,12 );
- 字符串形式：new Date('June 10,2013 12:12:12');

***
    Math.floor(t/86400)+'天'
    +Math.floor(t%86400/3600)+'时'
    +Math.floor(t%86400%3600/60)+'分'
    +t%60+'秒';

    Math.floor(t/86400)+'天'
    +Math.floor(t/3600)+'时'
    +Math.floor(t/60)+'分'
    +t%60+'秒';



###事件

- **event对象的兼容性问题**
    + ie/chrome：event是一个内置的全局对象
    + 标准下（包括ff）：事件对象是通过事件函数的第一个参数传入
        * var ev = ev || event;
        * 事件对象[和当前这个对象发生的这个事件有关的详细的信息]
        * 鼠标位置、键盘按键 ev.keyCode
    
- **事件绑定**:向一个对象上加两个函数
    + IE
        * 对象.attachEvent(事件名, 函数)
        * oBtn.attachEvent('onclick', aaa);[detachEvent]
        * [this->window]
            - 解决方法：
            - document.attachEvent(‘onclick’, function(){fn1.call(document)});

    + 其他
        + 对象.addEventListener(事件名, 函数, 是否捕获)
        + oBtn.addEventListener('click', aaa, false);[removeEventListener]

- **事件调用**
    + 直接调用 fn1();
    + 事件调用 document.onclick = fn1;
    + 定时器也可以调用
        * setInterval( 函数, 毫秒 )    重复执行（发动机
        * setTimeout( 函数, 毫秒 )      执行一次（炸弹
        * 定时器如果是由用户控制的,一定要先关后开[原则]

- **事件分类**
    - 普通事件：onclick、onmousedown
    - DOM事件：[DOM浏览器所特有的 即ff所特有的] DOMMouseScroll
        - DOM事件只能通过绑定来添加
        - DOM事件阻止默认行为 : oEvent.preventDefault();

- **事件冒泡**
    + **冒泡 捕获**
        + 冒泡[一般把事件绑定在父亲身上]:
            * 告诉div1，如果有一个出去的事件触发了你，你就去执行fn1这个函数
        + 捕获:
            * 告诉div1，如果有一个进去的事件触发了你，你就去执行fn1这个函数

    + **阻止事件冒泡**
        * oEvent.cancelBubble=true;

    + **不是很懂**

***
    W3C在mouseover和mouseout事件中添加了relatedTarget属性 ：
    •在mouseover事件中，它表示鼠标来自哪个元素
    •在mouseout事件中，它指向鼠标去往的那个元素

    IE在mouseover和mouseout事件中添加了两个属性
    •fromElement，在mouseover事件中表示鼠标来自哪个元素
    •toElement，在mouseout事件中指向鼠标去往的那个元素

    document.getElementById('box1')  //是父亲

    document.getElementById('box1').onmouseover = function (e) {
         if (!e) e = window.event;
         var reltg = e.relatedTarget ? e.relatedTarget : e.fromElement;
         while (reltg && reltg != this) reltg = reltg.parentNode;
         if (reltg != this) {
              // 这里可以编写 onmouseenter 事件的处理代码
              alert('111');
         }
    }

    document.getElementById('box1').onmouseover = function (e) {
         if (!e) e = window.event;s
         var reltg = e.relatedTarget ? e.relatedTarget : e.toElement;
         while (reltg && reltg != this) reltg = reltg.parentNode;
         if (reltg != this) {
              // 这里可以编写 onmouseenter 事件的处理代码
              alert('111');
         }
    }

###OTHER

- **鼠标滚轮的上下方向兼容性解决**  
`bDown=oEvent.wheelDelta?oEvent.wheelDelta<0:oEvent.detail>0;`

- **基本两个要一起用 的clientX和scrollLeft**   
`oDiv.style.left=oEvent.clientX+scrollLeft+'px';`

- 拖拽

***
	onmousedown  储存距离
	onmoousemove 根据距离 计算div最新的距离
	onmouseup    释放事件
