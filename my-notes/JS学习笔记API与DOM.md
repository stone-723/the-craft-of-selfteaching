# Web APIs 和 JS 基础关联性
1. JS的组成
ECMSScript  即JS语法 也是JS的基础
以下两个也统称为 Web APIs
DOM 页面文档对象模型
BOM 浏览器对象模型

# API（应用程序编程接口）
是一些预先定义的函数 目的是提供应用程序与开发人员基于某软件或硬件得以访问一组例程的能力 而又无需访问源码 或理解内部工作机制的细节. 即 给程序员提供的一种工具 以便更轻松实现要完成的功能.

# WebAPI
是浏览器提供的一套操作浏览器功能和页面元素的API(BOM和DOM）

# DOM
文档对象模型 是W3C组织推荐的处理可拓展标记语言*HTML*的标准编程接口

DOM树
文档：一个页面就是一个文档DOM中使用document表示
元素：页面中的所有标签都是元素 DOM中使用element表示
节点：网页中的所有内容都是节点（标签 属性 文本 注释等）DOM中用node表示
**DOM把以上内容都看做是对象**

## DOM在实际开发中用于操作元素 获取页面中的元素使用以下几种方式

### 根据ID获取元素
使用getElementByld（）方法可以获取带有ID的元素对象
语法
var element = document.getElementById（‘id’）;
参数：element是一个Element对象 如果当前文档中拥有特定ID的元素不存在则返回null
id是**大小写敏感的字符串** 代表了所要查找的元素的唯一ID.（参数值需要加字符串符号‘’）
返回的是一个元素对象

### 根据标签名获取元素
使用getElementsByTagName（）方法可以返回带有指定标签名的对象的集合
语法
var element = document.getElementByTagName（‘标签名’）;
返回的是获取过来元素对象的集合 以伪数组的形式存储
想要依次打印里面的元素对象 我们可以采取遍历的方式
得到的元素对象是动态的
即便页面中只有一个li 返回的还是伪数组形式
页面中没有选择的元素 返回的是空的伪数组
还可以获取某个父元素内部所有指定标签名的子元素
element.getElementsByTagName（‘标签名’）
<ol id='ol'>
    <ul>1</ul>
    </ol>
var ol = document.getElementById（‘ol’）；
console.log（ol.getElementsByTagName（‘li’））；
              ↑给父元素指定个id         ↑子元素标签名
注意 父元素必须是单个对象（必须指明是哪一个元素对象) 获取的时候不包括父元素自己

### 通过HTML5新增方法获取元素
1.document.getElementsByClassName('类名'）;//根据类名返回元素对象集合
2.document.querySelector（‘选择器’）；//根据指定选择器返回第一个元素对象
**切记querySelector里面的选择器需要加符号 类加. id加#    只返回第一个**
3.document.querySelectorAll（‘选择器’）；根据指定选择器返回所有元素对象集合 （伪数组形式)

### 特殊元素获取(body html)
1.获取body元素
var bodyEle = document.body；
console.log（bodyEle）；
返回body元素对象
2.获取html元素
var htmlEle = document.document.documentElement
返回html元素对象

# 事件基础
事件概述
JavaScript使我们又能力创建动态页面 而事件是可以被JavaScript侦测到的行为
网页中的每个元素都可以产生某些触发JS的事件 例如我们可以在用户点击某按钮时产生一个事件 然后去执行某些操作

事件由三部分组成 分别是
1.事件源          事件被触发的对象
2.事件类型        如何触发 什么事件 比如鼠标点击（onclick）还是鼠标经过 还是键盘按下
3.事件处理程序    通过一个函数赋值的方式完成
也称它们为事件三要素

## 执行事件的步骤
1.获取事件源
2.注册事件（绑定事件)
3.添加事件处理程序（采取函数赋值形式)

## 常见鼠标事件
onclick           鼠标点击左键触发
onmouseover       鼠标经过触发
onmouseout        鼠标离开触发
onfocus           获得鼠标焦点触发
onblur            失去鼠标焦点触发
onmousemove       鼠标移动触发
onmouseup         鼠标弹起触发
onmousedown       鼠标按下触发

# 操作元素
JS的DOM操作可以改变网页内容 结构和样式 我们可以利用DOM操作元素来改变元素里面的内容 属性等 注意 以下都是属性

## 改变元素内容
element.innerText
↑元素名
从起始位置到终止位置的内容 但它去除HTML标签 同时空格和换行也会去掉
element.innerHTML
从起始位置到终止位置的内容 包括HTML标签 同时保留空格和换行.

元素也可以不用添加事件 直接改变内容

## innerText和innerHTML的区别
innerText 不识别HTML标签 去除换行和空格
innerHTML 识别HTML标签 不去除空格和换行（用的多）
这两个属性都是可读写的 可以获取元素里面的内容

## 修改元素属性 src  href id alt title
1.获取元素
2注册事件 处理程序
获取了元素后只需要
元素名.事件 = function（）{
    img.属性名 = '新属性'；
    }
    即可
    
## 根据不同时间 显示不同图片和问候语练习题

       //1.获取元素
        var img = document.querySelector('img');
        var div = document.querySelector('div');
        //2.得到当前的小时数
        var date = new Date();
        var h = date.getHours();
        //3.判定小时数改变图片文字
        if (h < 12) {
            img.src = 'images/1.gif';
            div.innerHTML = '早上好 给你一拳'
        } else if (h < 18) {
            img.src = 'images/2.gif';
            div.innerHTML = '下午好 给你一拳'
        } else {
            img.src = 'images/3.gif';
            div.innerHTML = '晚上好 给你一拳'
        }
        
## 表单元素的属性操作
利用DOM可以操作如下表单元素的属性
type/value/checked/selected/disabled
表单里面的值 文字内容是通过 value来修改的
如果想要某个表单被禁用 不能再点击 用disabled
元素名.disabled = true;
还可以用
this.disabled = true；
this指向的是事件函数的调用者
点一次就变灰色 不能点
false就能再启用

## 京东登录界面密码框练习题
**     //获取元素
        var eye = document.getElementById('eye');
        var pswd = document.getElementById('pswd');
        //注册事件 处理元素 flag小算法 利用flag的值来控制流程
        var flag = 0;
        eye.onclick = function () {
            //点击一次后 flag一定要进行变化
            if (flag == 0) {
                pswd.type = 'text';
                eye.src = 'images/open.png';
                flag = 1;
            } else {
                pswd.type = 'password';
                eye.src = 'images/close.png';
                flag = 0;
            }
        }


## 样式属性操作
我们可以通过js修改元素大小 颜色 位置等样式
1.element.style       行内样式操作 
2.element.className   类名样式操作
**注意
1.JS里面的样式采取驼峰命名法 比如fontSize backgroundColor
2.JS修改style样式操作 产生的是行内样式 JS权重比较高

## 利用for循环 循环精灵图
思路
1.精灵图图片排列有规律
2.利用for循环 修改精灵图片的北京位置 background-position
3.让循环的i索引号x44 就是每个图片的y坐标
js写法如下
        // 1.获取元素 所有的li
        var lis = document.querySelectorAll('li');
        for (var i = 0; i < lis.length; i++) {
            //让索引号乘上44就是每个li的背景y坐标
            var index = i * 44;
            lis[i].style.backgroundPosition = '0-' + index + 'px';
        }
### 表单新事件
onfocus 获得焦点
onblur  失去焦点

## 
使用element.style来修改元素样式 如果样式少功能简单就用这个 如果复杂 使用
element.className比较合适
先在css里声明好一个类 将样式写进去
然后在js里使它一经鼠标点击 就自动添加这个新类 来产生变化
var test = document.querySelector（‘div’）；
test.onclick = function（）{
         this.className = ‘之前写好的类’；//这一步就讲当前元素的类名改为了之前写好的
}
可以通过修改元素className更该元素的样式

**注意 
class是保留字 所以使用className来操作类名属性
className会直接更改元素类名 会覆盖原先的类名

## 操作元素总结
操作元素是DOM核心内容
                     innerText
   操作元素内容→    
                     innerHTML

        
   操作常见元素属性→ src、href、title、alt等


   操作表单元素属性→ type、value、disabled等
    
                      
                      element.style
                     
   操作元素样式属性→ 

                      className