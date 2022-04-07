# 精灵图
 为了有效减少服务器接收和发送请求的次数 提高页面加载速度
 出现了CSS精灵技术 也称（CSS Sprites CSS雪碧）
 
 核心原理 ：将网页中的一些小背景图像整合到一张大图中
 这样服务器只需要一次请求就可以了.
 
 使用方式
 给小盒子添加背景图片 然后使用background-position移动背景图片 让需要的图标和盒子对齐
 （需要精确坐标X Y 网页中坐标往上/往左是负值）‘
 position可以连写 例
 
 background：url（images/shiro1.png） -182px 0;
 
# 字体图标
使用场景：主要用于显示网页中通用 常用的一些小图标
iconfont
字体图标展示的是图标 本质属于字体
轻量 灵活 兼容
（不能替代精灵图的作用 但是在一些小图标很方便 很好用）
使用步骤：从网上下载 下载完成把fonts文件夹移动到根目录 然后使用引入语法
引入语法：在style标签里引用就好 
字体声明：
@font-face {
  font-family: 'icomoon';
  src:  url('fonts/icomoon.eot?jyl09u');
  src:  url('fonts/icomoon.eot?jyl09u#iefix') format('embedded-opentype'),
    url('fonts/icomoon.ttf?jyl09u') format('truetype'),
    url('fonts/icomoon.woff?jyl09u') format('woff'),
    url('fonts/icomoon.svg?jyl09u#icomoon') format('svg');
  font-weight: normal;
  font-style: normal;
  font-display: block;
}

点开刚才下载好的文件里面的html文件 复制小方框 把它放进标签里
给刚才的标签声明字体
例如
span{
font-family:'icomonn';
}

就可以显示了
注：因为是文字 所以颜色大小都可以用font属性进行修改

字体图标的追加
把压缩包里面的selection.json重新上传 选中自己想要的新的图标 重新下载压缩包 替换原来的文件即可

# CSS三角
网页中常见的三角形 使用CSS可以直接画出来 不需要使用图片或字体图标
设置一个宽高为0 的盒子 将其他的边隐藏 只留一个边 那个边就是三角 大小通过调试边框像素值
例如下
div{
width：0；
height：0；
line-height：0；
font-size：0；
border：50px solid transparent（透明）；
border-left-color：red；生成一个红色的左边为底边的三角形
}

做一个带小三角形的气泡框只需要在大盒子放小盒子 用定位就可以了


# CSS用户界面样式
所谓界面样式 即更改一些用户操作样式 提高用户体验

## 更改用户鼠标样式
cursor
li{cursor：pointer；}
设置或检索在对象上移动的鼠标指针采用何种系统预定义的光标形状.
属性值
default        小白 默认
pointer        小手
move           移动
text           文本
not-allowed    禁止
其他样式可去查询

## 表单轮廓
outline
给表单添加 outline：0；
或         outline：none；
样式后 
可以去掉默认的蓝色边框

## 防止表单域拖拽
防止拖拽文本域 resize
textarea{resize：none；}


# vertical-align 属性应用
用于设置一个元素的垂直对齐方式 但只针对于行内元素或行内块元素有效.
语法：
vertical-align：
baseline          默认 元素放置在父元素的基线上
top               把元素的顶端与行中最高元素的顶端对齐
middle            把此元素放置在父元素的中部
bottom            把元素的顶端与行中最低的元素的顶端对齐.

# 溢出文字省略号显示
单行文本溢出显示省略号
必须满足3个条件
1.先强制一行内显示文本
white-space：nowrap；（强制一行显示）、（默认 normal 是自动换行）
2.超出部分隐藏
overflow：hidden；
3.文字用省略号代替超出的部分
text-overflow：ellipsis；

多行文本溢出显示省略号
有兼容性问题 适合于webKit浏览器或移动端
做法
overflow：hidden；
text-overflow：ellipsis；
display：-webkit-box；
-webkit-line-clamp：行数；
-webkit-box-orient：vertical；

# 常见布局技巧

## margin负值运用
让每个盒子margin往左移动-1px 可以正好压住相邻盒子的边框 解决边框重叠变粗的问题
鼠标经过某盒子时 提高当前盒子的层级即可 如果没有定位就给加一个相对定位（保留位置）
如果有定位 直接加z-index.


## 文字围绕浮动元素
直接做一个大盒子 往里头放图片给图片加浮动 文字会自动围绕图片

## CSS三角强化
如何做一个直角三角形
可以按以下步骤
border-top：100px solid transparent；将上边框宽度调大 挤压右边框 颜色设为透明
border-right：50px solid red；
border-bottom：0px；将下和左的边框均设置为0
border-left：0px；

可简写为以下代码
width：0；
height：0；
border-color：transparent red transparent transparent；
border-style：solid；
border-width：22px 8px 0 0；  上大 右小 左下0

## CSS初始化
不同浏览器对标签的默认值不同
为了消除不同浏览器对HTML文本呈现的差异 照顾浏览器的兼容
我们需要对CSS进行初始化
CSS初始化是指重设浏览器的样式 也称为 CSSreset
每个网页都必须进行CSS初始化

以下为京东网站的CSS初始化

**/把所有标签的内外边距清零/
* {
    margin: 0;
    padding: 0
}

/* em 和 i 斜体文字不倾斜 */
em,
i {
    font-style: normal
}

/* 去掉li的小圆点 */
li {
    list-style: none
}

img {
    /* border 0 照顾低版本浏览器 如果图片外包含了链接会有边框的问题 */
    border: 0;
    /* 取消图片底侧有空白缝隙的问题 */
    vertical-align: middle
}

button {
    /* 当我们鼠标经过button按钮的时候 变成小手 */
    cursor: pointer
}

/* 所有链接颜色为#666 去掉下划线 */
a {
    color: #666;
    text-decoration: none
}

/* 鼠标经过链接时变红 */
a:hover {
    color: #c81623
}

/* 设置字体 比较多 照顾兼容性 */
button,
/* 把中文字体的名称用相应的Unicode编码来代替 这样就可以有效的解决浏览器解释CSS代码时出现乱码的问题 */
/* 例如 黑体\9ED1\4F53 宋体\5B8B\4F53 微软雅黑\5FAE\8F6F\96C5\9ED1  */
input {
    font-family: Microsoft YaHei, Heiti SC, tahoma, arial, Hiragino Sans GB, "\5B8B\4F53", sans-serif
}

body {
    /* 抗锯齿性 让文字显示更加清晰 放大锯齿不明显 */
    -webkit-font-smoothing: antialiased;
    background-color: #fff;
    font: 12px/1.5 Microsoft YaHei, Heiti SC, tahoma, arial, Hiragino Sans GB, "\5B8B\4F53", sans-serif;
    color: #666
}

.hide,
.none {
    display: none
}

/* 清除浮动 */
.clearfix:after {
    visibility: hidden;
    clear: both;
    display: block;
    content: ".";
    height: 0
}

.clearfix {
    *zoom: 1
}

只需要知道 每个网页都需要进行CSS初始化 