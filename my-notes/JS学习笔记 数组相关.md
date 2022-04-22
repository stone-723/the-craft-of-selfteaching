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

