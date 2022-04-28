# 对象
对象是一个具体的事物
例如一个数据库 一张网页 一个与远程服务器的连接 都可以看作是对象
JavaScript中的对象分为3种 自定义对象 内置对象 浏览器对象
自定义对象和内置对象都属于ECMAScript 浏览器对象属于JS独有的

**在JavaScript中 对象是一组无序的相关属性的方法的集合 所有的事物都是对象 例如字符串 数值 数组 函数等
对象是由属性和方法组成的
属性：事物的特征 在对象中用属性来表示（常用名词)
方法：事物的行为 在对象中用方法来表示（常用动词)

## 为什么需要对象
保存一个值时 可以使用变量 保存多个值（一组值)时 可以使用数组
如果需要保存一个完整的信息 使用对象会更加好
JS中的对象表达结构更清晰 强大

## 创建对象的三种方式
在JavaScript中 现阶段我们可以采用3种方法创建对象（object）
### 1.利用字面量创建对象
对象字面量:就是花括号{}里面包含了表达这个具体事物（对象）的属性和方法
var obj={
    uname:'西木野真姬',
    age:18,
    sex:'女',
    sayHi:function(){
           console.log（'hi'）;
           }
 }
（1）里面的属性或方法我们采取键值对的形式 键 属性名：值 属性值
（2）多个属性或方法中间用逗号隔开 最后一个不需要
（3）方法冒号后面跟的是一个匿名函数

### 2.利用new Object创建对象
var obj=new Object(); 创建了一个空的对象
obj.uname=西木野真姬；
obj.age=18；
obj.sayHi=fuction（）{
console.log（'hi~'）；
}
通过上面这种方式追加属性

我们是利用等号赋值的方法 添加对象的属性和方法
每个属性和方法之间用分号结束
调用是
console.log（obj.uname）;
console.log（obj['sex']）;
obj.sayHi();

### 3.利用构造函数创建对象
**为什么需要构造函数？**
 是因为前面两种创建对象的方式一次只能创建一个对象
 有时候我们一次创建的对象 里面很多的属性和方法是大量相同的
 因此我们可以利用函数的方法 重复这些相同的代码 这样的函数就叫 构造函数
 因为此函数里面封装的不是代码 而是对象 所以叫 构造函数
 构造函数就是把对象里的一些相同的属性和方法抽象出来装到函数里
**构造函数的语法格式**
function 构造函数名(){
        this.属性=值；
        this.方法=function（）{}
}
调用
new 构造函数名();

例
function Star（uname,age,sex）{
        this.name = uname;
        this.age = age;
        this.sex = sex;
        this.sing = function（sang）{
        console.log(sang);
        }
}
var xmyzj = new Star('西木野真姬','18','女');
console.log(xmyzj.name);
xmyzj.sing('爱上你万岁');
var nxn = new Star('南小鸟','18','女')；（这样就可以创建多个对象了）
console.log(nxn.name);
nxn.sing('蓝莓小火车');

**注意
构造函数的名字首字母要大写
构造函数不需要 return就可以返回结果
调用函数返回的是一个对象
我们调用构造函数 必须使用 new
我们只要new Star（） 调用函数就创建一个对象 xmyzj{}

### 使用对象
（1）调用对象的属性 我们采取     对象名.属性名
（2）调用对象的属性的第二种方法  对象名['属性名']
（3）调用对象的方法 sayHi        对象名.方法名（）  调用函数必须加小括号

# 变量 属性 函数 方法的区别
## 变量和属性的区别
1.他们都是用来储存数据的
2.变量单独声明并赋值 使用时直接使用变量名 单独存在
3.属性 在对象里面 不需要声明 使用时必须用对象.属性 才可以使用 寄生存在
## 函数和方法的区别
1.都是实现某种功能 做某件事 单独存在
2.方法 在对象里面 调用的时候 必须 对象.方法才行 附庸存在

## 构造函数和对象
构造函数 如Stars()抽象了对象的公共部分 封装到函数里 他泛指某一大类 class
创建对象 如new Stars() 特指某一个 通过new关键字创建对象的过程我们也称为对象实例化

# new关键字执行过程
1.new 构造函数可以在内存中创建一个空的对象
2.this就会指向刚才创建的空对象
3.执行构造函数里面的代码 给空对象添加属性与方法
4.返回这个对象

# 遍历对象
for...in语句 用于对数组或对象的属性进行循环操作（最合适用在对象上）
语法结构
for（变量 in 对象）{

}
例子
for（var k in obj）{
      console.log（k）;//输出变量 得到属性名
      console.log（obj[k]);//得到的是属性值
}

**注 
使用for in里面的变量 一般喜欢写k或者key

**小结
1.对象可以让代码结构更清晰
2.对象复杂数据类型object
3.本质：对象就是一组无序的相关属性和方法的集合
4.构造函数泛指某一大类 比如苹果 不管是青苹果还是红苹果 都统称为苹果
5.对象实例特指某一个事物 比如这个苹果 我们的班主任 等
6.for in语句用于对对象的属性进行循环操作

# 内置对象
指JS语言自带的一些对象 这些对象供开发者使用 并提供了一些常用的或是最基本而必要的功能（属性和方法）

## Math对象
在mdn查属性方法的使用
Math是一个内置对象 具有数学常数和函数的属性和方法 不是一个函数对象
Math不是一个构造器 Math的所有属性方法都是静态的 直接用
和数学相关的运算（求绝对值 取整 最大值 ）
Math.PI                   圆周率
Math.floor()              向下取整往最小取
Math.ceil()               向上取整往最大取
Math.round()              四舍五入 就近取整 其他数字四舍五入 .5特殊 往大了取 -3.5结果是-3
Math.abs                  绝对值
Math.max()/Math.min()     求最大/最小值

### Math对象随机数方法 
Math.random()返回一个随机的小数0-1之间的 取不到1 能取到0
这个方法里面不跟参数

得到两个数之间的随机整数 并且包含这两个 在MDN可以找到公式
**function getRandom（min,max）{
     return Math.floor（Math.random（）*（max-min+1））+min；
     }
       console.log（getRandom（1，10））；

# 猜数字练习题
         function getRandom(min, max) {
            return Math.floor(Math.random() * (max - min + 1)) + min;
        }
        var random = getRandom(1, 10);
        var i = 0;
        while (i < 10) {
            var num = prompt('请输入1-10之间的数字 猜猜看');
            if (num > random) {
                alert('大了');
                i++;
            } else if (num < random) {
                alert('小了');
                i++;
            } else {
                alert('猜对了');
                break;
            }
        }
        
## 日期对象（时间戳）
Date（）日期对象 是一个构造函数 必须使用new来调用创建我们的日期对象
var arr = new Array（）；创建一个数组对象
var obj = new Object（）；创建一个对象实例
var date = new Date（）；使用Date 如果没有参数 就返回当前系统的当前时间
Date的参数常用写法
数字型 2019，10，01 或者是字符串型 '2019-10-1 8：8：8'
getFullYear（）获取当年
getMonth（）获取当月（0-11）   返回的月份小一个月 月份需要+1
getDate（）获取当天日期
getDay（）获取星期几（星期0到星期6） 周一返回1 周六返回6 周日返回0
getHours（）获取当前小时
getMinutes（）获取当前分钟
getSeconds（）获取当前秒钟

## 获取日期的总毫秒形式
Date对象是基于1970年1月1日（世界标准时间）起的毫秒数
我们经常用总的毫秒数来计算时间 因为更加精确
1.通过 valueOf（）   2.通过getTime（）
简单写法  最常用的
var date = +new Date（）
console.log(date);
3.H5新增获取总的毫秒数方法
console.log（Date.now());

## 倒计时案例
核心算法 将输入的时间减去新增的时间就是倒计时时间
用时间戳来做
将时间戳转化为天 时 分 秒
转换公式如下
d =parseInt（总秒数/60/60/24）；//算天数
h =parseInt（总秒数/60/60%24）；//计算小时
m =parseInt（总秒数/60%60）；//计算分数
s =parseInt（总秒数%60）；计算当前秒数


                倒计时封装

function countDown(time) {
            var nowTime = +new Date();//括号为空 返回当前时间戳
            var inputTime = +new Date(time);//返回用户输入的时间戳
            var times = (inputTime - nowTime) / 1000;//time为剩余时间的秒数
            var d = parseInt(times / 60 / 60 / 24);//算天数
            d = d < 10 ? '0' + d : d;
            var h = parseInt(times / 60 / 60 % 24);//计算小时
            h = h < 10 ? '0' + h : h;
            var m = parseInt(times / 60 % 60);//计算分数
            m = m < 10 ? '0' + m : m;
            var s = parseInt(times % 60);//计算秒数
            s = s < 10 ? '0' + s : s;
            return d + '天' + h + '时' + m + '分' + s + '秒';
        }
        console.log(countDown('2022-4-28 14:00:00'));

## 字符串对象

 var str = 'andy'
 console.log（str.length）；//对象才有属性和方法 复杂数据类型才有 为什么简单数据类型会有length属性呢？因为有基本包装类型
 
### 基本包装类型

把简单数据类型 包装成为了复杂数据类型
为了方便操作基本数据类型 JavaScript还提供了三个特殊的引用类型 String Number和boolean

# 字符串的不可变

指的是里面的值不可变 看上去可以改变内容 实际上是地址变了 内存中新开辟了一个内存空间。
因为字符串不可变所以不要大量的拼接字符串


## 根据字符返回位置

字符串的所有方法都不会修改字符串本身 操作完成会返回一个新的字符串
但我们使用indexOf（‘要查找的字符‘， 开始的位置）可以返回指定内容在元字符串中的位置 如果找不到就返回-1 开始的位置是index索引号
lastIndexOf（）从后往前找 只找第一个匹配的

## 查找某个字符所有出现的位置及次数练习题

思路：先查找第一个出现的位置 此时只要indexOf返回的结果不是-1就继续往后找
因为indexOf只能找到第一个 所以后面的查找 一定是当前索引+1 从而继续查找 代码流程如下

        var str = 'abcoefoxyozzopp';
        var index = str.indexOf('o');//查找第一个o的索引号 赋值给index
        var num = 0;//设置一个变量来累计o出现的次数
        while (index !== -1) {//此时index是o的索引号 不等于-1 开始循环
            console.log(index);//打印此时的索引号
            num++;//找到一次就加一次 这样最后就是总的出现次数了
            index = str.indexOf('o', index + 1);//索引号+1 继续循环找下一个o
        }
        console.log('o出现的次数:' + num);

## 根据位置返回字符（重点）

方法名.                              说明                                          使用
charAt（index）。                返回指定位置的字符                     str.charAt（0）
chaCodeAt（index）            获取指定位置处字符的ASCII码               str.charCodeAt(0)
str[index]                       获取指定位置处字符                     Html5支持 和charCodeAt（）等效

## 统计出现次数最多的字符串练习题

思路：判断一个字符串’abcoefoxyozzopp’中出现次数最多的字符 并同机器次数
利用charAt（）遍历这个字符串
把每个字符都储存给对象 如果对象没有该属性 就为1 如果存在了就+1
遍历对象 得到最大值和该字符

代码流程如下

        var str = 'abcoefoxyozzopp';
        var o = {};
        for (var i = 0; i < str.length; i++) {
            var chars = str.charAt(i);//chars是字符串中的每一个字符 
            if (o[chars]) {// o[chars]得到的是属性值
                o[chars]++;
            } else {
                o[chars] = 1
            }
        }
        console.log(o);
        //遍历对象
        var max = 0;
        var ch = '';
        for (var k in o) {//k得到的是属性名 o[k]得到的是属性值
            if (o[k] > max) {
                max = o[k];
                ch = k
            }
        }
        console.log('出现最多的字符是' + ch);//k是局域 出了就没效果 所有在外面声明一个ch 全局 让他来代替k输出
        console.log('出现最多的字符出现的次数是' + max);

## 字符串操作方法（重点）
方法名                                        说明
concat（str1，str2，str3...）          concat（）方法用于链接两个或多个字符串 拼接字符串 等效于+ +更常用
substr（start，length）                从start位置开始（索引号） length取的个数 重点记住这个
slice（start，end）                    从start位置开始 截取到end位置 end取不到 他俩都是索引号
substring（start，end）                从start位置开始 截取到end位置 end取不到 基本和slice相同 但不接受负值
replace（'被替换的字符','替换为的字符')替换字符    它只会替换第一个字符 需要使用正则表达式才可以全换  
split（'分隔符'）                      字符转换为数组 要有分隔符号才行 不然会看成一个数组  和join相反
toUpperCase（）                         转换大写
toLowerCase（）                         转换小写

