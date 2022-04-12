# HTML5的新特性

## 新标签 

**语义化标签**
< header > 头部标签
< nav >导航标签
< article >内容标签
< section >定义文档某个区域
< aside >侧边栏标签
< footer >尾部标签 

**视频标签**
< video>视频标签  尽量使用mp4格式
语法
< video src=“文件地址” controls=“controls”>< /video>
常见属性
属性            值                       描述
autoplay      autoplay                 视频就绪自动播放 （谷歌浏览器需要添加muted来解决自动播放的问题）            
controls      controls                 向用户显示播放控件
width         px像素                   设置播放器宽度
height        px像素                   设置播放器高度
loop          loop                     播放完是否继续播放该视频（循环播放）
preload       auto（预先加载视频）    规定是否预加载视频 如果有了autoplay即可忽略该属性
              none（不应加载视频）    
src           url                      视频url地址
poster        lmgurl                   加载等待的画面图片
muted         muted                    静音播放

**音频标签**
< audio>音频标签 使用mp3格式较多
语法
< audio src=“文件地址”controls=“controls”>< /audio>
常见属性
属性           值           描述
autoplay     autoplay      如果出现该属性 则音频在就绪后马上播放
controls     controls      如果出现该属性 则向用户显示控件 比如播放按钮
loop         loop          如果出现该属性 则每当音频结束时重新开始播放
src          url           要播放的音频url.

## 新input表单
属性值                 说明
type="email"         限制用户输入必须为Email类型
type="url"           限制用户输入必须为URL类型
type="date"          限制用户输入必须为日期类型
type="time"          限制用户输入必须为时间类型
type="month"         限制用户输入必须为月类型
type="week"          限制用户输入必须为周类型
type="number"        限制用户输入必须为数字类型
type="tel"           手机号码
type="search"        搜索框
type="color"         生成一个颜色选择表单

**新增的表单属性**
属性                  值                             说明
required             required          表单拥有该属性表示其内容不能为空 必填
placeholder          提示文本          表单的提示信息 存在默认值将不显示
autofocus            autofocus         自动聚焦属性 页面加载完成自动聚焦到指定表单
autocomplete         off/on            当用户在字段开始键入时 浏览器基于之前键入过的值 应该显示出在字段中填写的选项 默认已经打开 
                                       比如autocomplete=“on” 关闭autocomplete=“off” 需要放在表单内 同时加上name属性 同时成功提交
multiple             multiple          可以多选文件提交
# CSS3的新特性

## 新增选择器

**属性选择器**
属性选择器可以根据元素特定属性的来选择元素 可以不用借助类或id选择器
选择符                    简介
E[att]                选择具有att属性的E元素
E[att="val"]          选择具有att属性且属性值等于val的E元素（可以选择【属性=值】的某些元素 重要）
例子
input[type=text]{
                  color：pink；
                  }
                  
                 上面这个就是只选择type=text 文本框的input  将它选取出来 把颜色改为粉色.
                                              
E[att^"val"]          匹配具有att属性且值以val开头的E元素（可以选择属性相同 且属性值相同开头的那些元素）
例子
div[class^icon]   
                 选择了首先是div 然后具有class属性 且属性值是以icon为开头的这些元素
                                                 
E[att$"val"]          匹配具有att属性且值以val结尾的E元素（可以选择属性相同 且属性值相同结尾的那些元素
E[att* "val"]         匹配具有att属性且值中含有val的E元素（只要值包含写的 就可以选取出来）


注意 类选择器 属性选择器 伪类选择器 权重为0010.

**结构伪类选择器**
结构伪类选择器主要根据文档结构来选择器元素.常用于根据父级选择器里面的子元素
选择符                   简介
E:first-child         匹配父元素中的第一个子元素E
例子
ul li:first-child{
              }
E:last-child          匹配父元素中的最后一个E元素
例子
ul li:last-child{
               }
E:nth-child（n)       匹配父元素中的第n个子元素E  (选择某个父元素的一个或多个特定的子元素）
n可以是数字 关键字和公式
如果n是数字 就是选择第n个子元素 从数字1开始
n也可以是关键字 even 偶数 odd奇数
n也可以是公式 常见公式如下（如果n是公式 则从0开始计算 但是第0个元素或者超出了元素的个数会被忽略）
常见公式
2n           偶数
2n+1         奇数
5n           5 10 15....
n+5          从第5个开始（包括第5个）到最后
-n+5         前五个（包括第5个）
数字可灵活运用 

E:first-of-type       指定类型E的第一个
E:last-of-type        指定类型E的最后一个
E:nth-of-type（n）         指定类型E的第n个
基本和上面的用法一样  
nth-of-type会把指定的元素的盒子排列序号 nth-of-type对父元素里面指定子元素进行排序选择 先去匹配E然后再根据E去找第N个孩子
但nth-child会把所有的盒子都排列序号    nth-child对父元素里所有孩子排序选择（序号固定）先找到第n个元素 然后再去看它和E是否匹配
所以在一个父元素里有多个子元素时候 使用nth-of-type会更加合适

**伪元素选择器**
伪元素选择器可以帮助我们利用CSS创建新标签元素而不需要HTML标签 从而简化HTML结构
选择符
::before            在元素内部的前面插入内容
::after             在元素内部的后面插入内容
**注意
1.before和after创建一个元素 属于行内元素
2.新创建的这个元素在文档树中找不到 所以称为伪元素
3.语法：element::before{}
4.before和after必须有content属性
5.before在父元素内容的前面创建元素 after在父元素的内容后面插入元素（一前一后）
6.伪元素选择器和标签选择器一样 权重为1

# 使用伪元素清除浮动
3.父级添加after伪元素
：after方式是额外标签的升级版  也是给父元素添加
语法：
.clearfix::after{      设置一个伪元素
  content:'';          伪元素必写属性
  display:block;       插入的元素必须是块级
  height:0;            不要看见这个元素
  clear:both;          核心代码清除浮动
  visibility:hidden;   不要看见这个元素
  }
.clearfix{ *zoom:1;}   IE6.7专有
优点 没有增加标签 结构简单
缺点 照顾低版本浏览器

4.父级添加双伪元素
也是给父元素添加
.clearfix::before,.clearfix::after{  设置双伪元素
    content:"";                      伪元素必写属性
    display:table;                   转换为块级元素并且一行显示
    }
.clearfix:after{                     清除浮动
    clear:both;
    }
.clearfix{
     *zoom:1;
     }
优点 代码更简洁
缺点 照顾低版本浏览器

# CSS3盒子模型box-sizing

CSS3中可以通过box-sizing来指定盒模型
有2个值即可指定为
content-box
border-box
计算盒子大小的方式发生了改变
1.box-sizing：content-box 盒子大小为width+padding+border 以前默认的
2.box-sizing：border-box 盒子大小为width
即 如果将属性改为border-box
那padding和border就不会撑大盒子 前提是padding和border不超过width宽度
可在CSS开头使用通配符选择器将这个属性赋给所有盒子

# CSS3滤镜filter
例   filter：blur（） blur 模糊处理 括号数值越大图片越模糊

# CSS3calc函数
calc（）此CSS函数让你在声明CSS属性值时执行一些计算
例如
width：calc（100% - 30px）（让子盒子永远比父盒子小30像素）

# CSS3过渡
谁做过渡给谁加
过渡（transition）可以在不使用JS和flash动画的情况下
让元素从一种样式变换为另一种样式时为元素添加效果
过渡动画可让页面更好看 更动感 和：hover一起搭配使用比较常见

transition：需要过渡的属性  花费时间  运动曲线  何时开始；
1.属性          想要变化的CSS属性 宽度高度 背景颜色 内外边距都可以如果想要所有的属性都变化过渡 写一个all就行
2.花费时间      单位是秒 （必须写单位） 例如0.5s
3.运动曲线      默认是ease（可以省略）linear 匀速  ease 渐慢  ease-in 加速  ease-out 减速  ease-in-out 先加速后减速
4.何时开始      单位是秒 （必须写单位） 可以设置延迟触发事件 默认是0s（可以省略） 
如果想要写多个属性 使用逗号进行分割 想要多个属性都变化 直接写all

# 狭义的HTML5 CSS3
HTML5相关结构标签本身
CSS3相关样式


# 广义的HTML5 
是指HTML5本身+CSS3+JavaScript
现在基本都指这个