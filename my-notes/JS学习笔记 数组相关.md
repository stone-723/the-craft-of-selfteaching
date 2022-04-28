# 数组
数组是指一组数据的集合，其中的每个数据被称作元素，在数组中可以存放任意类型的元素。
数组是一种将一组数据储存在单个变量名下的方式.

## 什么是数组
数组（Array）可以把一组相关的数据一起存放 并提供方便的访问（获取）方式
数组里可以存放任意类型的数据 例如
var arr=['小白'，12，true，29.3]；
## 创建数组的方式
JS中创建数组有2种方式
**利用new创建数组
var 数组名 = new Array（）；
**利用数组字面量创建空的数组
var 数组名 = []；
使用数组字面量方式创建带初始值的数组
var 数组名 = ['a','b','c','d','e'];

## 访问（获取)数组元素 
**索引（下标）**:用来访问数组元素的序号（从0开始）
数组可以通过索引来访问、设置、修改对应的数组元素,我们可以通过
数组名[索引]的形式来获取数组中的元素

## 遍历数组
遍历：把数组中二点每个元素从头到尾都访问一次

我们可以通过索引将数组里的元素一项项取出来
但如果需要将数组里所有的元素取出来的时候 就需要用到我们的循环了
var arr = ['w','f','g'];
for(var i = 0;i < 3; i++){
        console.log(arr[i]);
        }
**注意 因为数组索引号从0开始 所以i必须=0开始 i<数组的总个数 （直接写i< arr.length)
输出的时候 arr[i] i计数器当成索引号来用

## 数组长度
使用   数组名.length  来访问数组元素的数量
数组的长度是元素个数 不要和索引号混淆
arr.length动态监测数组元素的个数

## 计算数组的和以及平均值
        var sum = 0;
        var average = 0;
        var arr = [2, 6, 1, 7, 4];
        for (var i = 0; i < arr.length; i++) {
            sum = sum + arr[i];//需要加的是数组元素arr[i] 而不是计数器i
        }
        average = sum / arr.length;
        console.log(sum, average);
        
## 求数组中最大值

        var arr = [2, 6, 1, 77, 52, 25, 7];
        var max = arr[0];
        for (var i = 1; i < arr.length; i++) {
            if (arr[i] > max) {
                max = arr[i];
            }
        }
        console.log(max);

## 数组转换为字符串
       
       var arr = ['red', 'green', 'bule', 'pink'];
        var str = '';
        var sep = '|';
        for (var i = 0; i < arr.length; i++) {
            str += arr[i] + sep;
        }
        console.log(str);
        
## 数组新增元素
可以通过修改length长度以及索引号增加数组元素
1.修改长度来实现数组扩容的目的
length属性是可读写的
2.修改索引号
追加数组元素
如果追加的索引号是原本已经有的 将会替换原来的
**不要直接给数组名赋值 否则里面的数组元素全部消失

## 数组存放1-10个值
使用循环来追加数组
声明一个空数组
循环中的计数器i可以作为数组元素存入
        var arr = [];
        for (var i = 0; i < 10; i++) {
            arr[i] = i + 1;
        }
        console.log(arr);

## 筛选数组方法

        var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
        var newArr = [];
        // newArr.length 就是0
        for (var i = 0; i < arr.length; i++) {
            if (arr[i] > 10) {
                // 新数组应该从0开始 依次递增 对上索引号
                newArr[newArr.length] = arr[i];                
            }
        }
        console.log(newArr);
        
## 删除数组指定元素（数组去重）
        
        var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
        var newArray = [];
        for (var i = 0; i < arr.length; i++) {
            if (arr[i] !== 0) {
                newArray[newArray.length] = arr[i];
            }
        }
        console.log(newArray);
        
## 翻转数组
**1.先声明一个新数组newArr
  2.把旧数组索引号二点第四个取过来（arr.length-1）给新数组索引号的第0个个元素（newarr.length）
  3.采取递减的方式 i--
        var arr = ['red', 'green', 'bule', 'pink', 'purple'];
        var newArray = [];
        for (var i = arr.length - 1; i >= 0; i--) {
            newArray[newArray.length] = arr[i]
        }
        console.log(newArray);

## 冒泡排序
是一种算法 把一系列的数据按照一定的顺序进行排列显示
 **演示
       var arr = [5, 2, 4, 1, 3];
        for (var i = 0; i <= arr.length - 1; i++) {//外层循环管趟数
            for (var u = 0; u <= arr.length - i - 1; u++) {//里层循环管 每一趟的交换次数
                //内部交换2个变量的值 一定是前一个和后一个相比较
                if (arr[u] > arr[u + 1]) {
                    var temp = arr[u];
                    arr[u] = arr[u + 1];
                    arr[u + 1] = temp;
                }
            }
        }
        console.log(arr);
        
        外层循环的躺数就是数组长度减一
        里层循环的交换次数就是数组长度减去次数
        但我们次数是0开始 所以是arr.length-i-1
        最后交换2个变量就可以了

## 检测是否为数组
1. instanceof 来检测 例如 console.log(arr instanceof Array）；//true
2.Array.isArray（参数） h5新增的办法 例如 console.log（Array.isArray（arr）；//true

## 添加删除数组元素的方法
方法名                      说明                                                        返回值
push（参数1...）   末尾添加一个或多个元素 注意修改原数组                             并返回新的长度

push是可以给数组追加新的元素 参数直接写数组元素 push完毕后 返回的结果是新数组的长度 原数组也会发生变化

pop（）            删除数组最后一个元素 把数组长度减一 无参数 修改原数组             返回它删除的元素的值

pop删掉最后一个元素 一次删除一个 无参数 返回它删掉的元素值

unshift（参数1...) 向数组的开头添加一个或多个元素 注意修改原数组                     并返回新的长度

unshift是可以给数组追加新的元素 参数直接写数组元素 unshift完毕后 返回的结果是新数组的长度 原数组也会发生变化

shift()            删除数组的第一个元素 数组长度减一无参数 修改原数组                并返回第一个元素的值

shift删掉第一个元素 一次删除一个 无参数 返回它删掉的元素值

## 筛选数组
遍历数组 设置条件 将不符合条件的使用push塞进新数组

## 数组排序

reveres（） 颠倒数组中元素的顺序 无参数    该方法会改变原来的数组 返回新数组
arr.reverse()

sort（）    对数组的元素进行排序           该方法会改变原来的数组 返回新数组
arr.sort()可以实现冒泡排序 但只能个位数 2位数以上就不行了 但在里面加一个函数就可以完美使用了
var arr = [1，4，77，6，89，2]；
arr.sort（function（a，b）{
       return a - b；//升序排列 b-a就是降序
       }）；
       console.log（arr）；
       
## 获取数组元素索引
indexOf()  数组中查找给定元素的第一个索引   如果存在返回索引号 不存在返回-1
lastIndexOf（） 在数组中的最后一个的索引    如果存在返回索引号 不存在返回-1

## 数组去重 （只留一个）
  封装一个去重函数 unique 
            function unique(arr) {
            varnewArr = [];
            for (var i = 0; i < arr.length; i++) {
                if (newArr.indexOf(arr[i]) === -1) {
                    newArr.push(arr[i]);
                }
            }
            return newArr;
        }
        var demo = unique([1, 34, 765, 2, 3, 4, 1, 4, 6, 7, 3, 2, 1, , 3, 5, 5, 6, 7]);

核心是利用查找索引方法 在新数组中如果找得到 说明已经有了  则不加入新数组 如果找不到 即返回的是-1 就加入新数组 这样新数组就没有重复元素了.

## 数组转换成字符串

toString（）      数组转换成字符串 逗号分隔每一项  返回一个字符串

join('分隔符')    方法用于吧数组中的所有元素转化为一个字符串 返回一个字符串
join可以自由决定使用的分隔符号  默认是逗号 
console.log(arr1.jioin('-'));

# 其他几个方法
concat（） 链接2个或多个数组 不影响原数组 返回一个新数组
slice（）  数组截取slice（begin，end）  返回被截取项目的新数组
splice（） 数组删除splice（第几个开始，要删除个数) 返回被删除项目的新数组 这会影响原数组




