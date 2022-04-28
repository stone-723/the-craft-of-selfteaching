# 函数
在js里 可能会定义非常多相同代码或功能相似的代码
这些代码可能需要大量重复使用
虽然for循环语句也可以实现一些简单的重复操作 但有局限性 
此时我们就需要使用JS中的函数了

## 函数的概念
函数：封装了一段可被重复调用执行的代码块。通过此代码块可以实现大量代码的重复使用。

## 函数怎么使用
函数在使用时 分为两步 1.声明函数 2.调用函数
函数是做某件事情 所以函数名一般为动词
函数不调用 自己是不会执行的
调用函数时一定要加小括号

**声明函数
function 函数名（）{
     //函数体
}
function：声明函数的关键字 此单词也是函数的意思
调用函数
函数名（）;

**函数的封装就是把一个或多个功能通过函数的方式封装起来 对外只提供一个简单的函数接口**
      **封装一个求x-y之间数总和的函数**
      
        function getSum(a1, a2) {
            var sum = 0;
            for (var i = a1; i <= a2; i++) {
                sum += i;
            }
            console.log(sum);
        }
        getSum(0, 100);
        
##  函数的参数
函数可以重复相同的代码
我们可以利用函数的参数实现函数重复不同的代码
形参：形式上的参数 函数定义的时候 传递的参数 当时并不知道是什么 形参是用来接收实参的 
实参：实际的参数   函数调用的时候 传递的参数 实参是传递给形参的
参数的作用：在函数内部某些值不能固定 我们可以通过参数在调用函数时传递不同的值进去

**如果实参的个数多于形参的个数 会取到形参的个数 多的直接被抛弃（但不会报错）
  如果实参的个数小于形参的个数 多余的形参定义为undefined 最终结果为NaN（也不会报错）
  建议 尽量将实参和形参个数相匹配

## 函数的返回值（return）
通过return语句可以实现函数降值返回给调用者
语法结构
function 函数名（）{
    return 需要返回的结果;
}
函数名（）;

**我们函数只是实现某种功能 最终的结果需要返回给函数的调用者
  只要函数遇到return 就能将后面的结果返回给函数的调用者
  例子
  
        function getSum(a1, a2) {
            var sum = 0;
            for (var i = a1; i <= a2; i++) {
                sum += i;
            }
            return sum;
        }
        console.log(getSum(0, 100));
        
使用return将结果返回给调用者 而不是在函数内部使用输出语句

**函数返回值注意事项
1.return 终止函数
return语句之后的代码不被执行
2.return一次只能返回一个值 你写多个值 只执行最后一个
3.我们想要返回多个结果 可以返回一个数组 
4.函数没有return 返回 undefined

### break continue return的区别
break：结束当前的循环体
continue：跳出本次循环 继续执行下次循环
return：不仅可以退出循环 还能返回return语句中的值 同时还可以结束当前的函数体内的代码


# arguments 的使用
当我们不确定有多少个参数传递的时候 使用arguments来获取 在javaScript中 arguments实际上
是当前函数的一个内置对象 所有的函数都内置了一个arguments对象  arguments对象中储存了传递的所有实参.

arguments展示形式是一个伪数组 因此可以进行遍历 
伪数组的特点：
1.具有length属性
2.按索引方式储存数据
3.不具有数组的push pop等方法

**可以使用数组的方式遍历arguments
i=0 i<arguments.lengts i++ consolo.log(arguments[i])
只有函数才有arguments对象 而且是每个函数都内置好了这个arguments

# 函数可以调用另一个函数
每个函数都是独立代码块 因此函数会互相调用
使用函数调用函数的例子

        function backDay() {
            var year = prompt('请输入年份');
            if (isLeapYear(year)) {
                alert('当前年份是闰年 2月份有29天');
            } else {
                alert('当前年份是平年 2月份有28天');
            }
        }
        backDay();

        function isLeapYear(year) {
            var flag = false;
            if (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) {
                flag = true
            }
            return flag;
        }
        
# 函数的2种声明方式
1.利用函数关键字自定义函数（命名函数 )
function xx(){
 }

2.函数表达式(匿名函数）
var 变量名 = function(){};
var fun = funcition(){
   console.log（'我是函数表达式'）；
 }
fun();
注意**fun是变量名 不是函数名
      函数表达式声明方式和声明变量差不多 变量里存的值 函数表达式里存的函数
      函数表达式也可以传递参数 如下
      
      var fun = function（aru）{
              console.log（aru）；
      }
      fun（'我是被传递的实参'）；
      
