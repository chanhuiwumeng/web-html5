#  JavaScript的基本语法 :imp:

## 1. JavaScript的基本使用方式

### 1.1 **JavaScript的Hello-World**

```html
<!DOCTYPE html>
<html lang="zh-cmn-Hans">
  <head>
    <meta charset="utf-8" />
    <title>javascript</title>
    <script>
      document.write('Hello World')
    </script>
  </head>
  <body></body>
</html>

```

![image-20201020170248389](_media/image-20201020170248389.png)

### 1.2 JavaScript的三种使用方式

+ head 标签内部使用JavaScript脚本
+ 在Body底部使用JavaScript甲苯
+ 使用外部的JavaScript脚本

```html
<!DOCTYPE html>
<html lang="zh-cmn-Hans">
  <head>
    <meta charset="utf-8" />
    <title>javascript</title>
    <!-- 在Head标签内部使用script标签 表示js脚本，再在script标签中间书写js代码 -->
    <script>
      document.write('Hello World')
    </script>
    <!-- 当我们将多个页面的js代码可以提取出来，在多个页面中引入使用，提高代码的复用性。页面更加的简洁 -->
    <script src="../js/index.js"></script>
  </head>
  <body>
    <!-- js脚本执行通常需要等待我们页面的Html,Css元素加载完成才可以去执行，所以我们将script脚本放在body底部 -->
    <script>
      document.write('Hello Body Bottom')
    </script>
  </body>
</html>

```

**index.js**

```javascript
document.write("Hello 外部的js文件");
```

## 2. JavaScript的基本语法

> **JavaScript \*语法\*是一套规则，它定义了 JavaScript 的语言结构。**

### 2.1 注释

> 就像 HTML 和 CSS，JavaScript 代码中也可以添加注释，浏览器会忽略它们，注释只是为你的同事（还有你，如果半年后再看自己写的代码你会说，这是什么垃圾玩意。）提供关于代码如何工作的指引。注释非常有用，而且应该经常使用，尤其在大型应用中

+ 单行注释
+ 多行注释

```html'
<script>
     // document.write('Hello Body Bottom');

     /*
      document.write('Hello Body Bottom');
      document.write('Hello Body Bottom');
     */
    </script>
```

### 2.2 关键字

> javaScript中被赋予特殊含义的单词。
>
> 在编辑器中带有颜色提示的单词。

**JavaScript保留关键字**

|          |           |            |           |              |
| -------- | --------- | ---------- | --------- | ------------ |
| abstract | arguments | boolean    | break     | byte         |
| case     | catch     | char       | class*    | const        |
| continue | debugger  | default    | delete    | do           |
| double   | else      | enum*      | eval      | export*      |
| extends* | false     | final      | finally   | float        |
| for      | function  | goto       | if        | implements   |
| import*  | in        | instanceof | int       | interface    |
| let      | long      | native     | new       | null         |
| package  | private   | protected  | public    | return       |
| short    | static    | super*     | switch    | synchronized |
| this     | throw     | throws     | transient | true         |
| try      | typeof    | var        | void      | volatile     |
| while    | with      | yield      |           |              |

### 2.3 标识符

> 代码中我们自己用来命名的名称就是标识符:
>
> + JavaScript语法严格区分大小写。
> + 可以使用:结尾 ，可以不适用分号结尾，建议加上，养成良好的编码习惯和规范。
>
> + 标识符由字母，数字，下划线,$组成
> + 标识符不能以数字开头
> + 建议标识符也不要使用$开头，有些标识符可以使用\_开头。
> + 关键字不能作为标识符使用
>
> + 标识符在命名的时候严格遵守驼峰命名法
>   + 方法名,变量名,参数名 使用小驼峰命名
>   + 构造函数等使用大驼峰命名法

```javascript
 	var num = 100;//声明变量
     function homeAddress(){}//声明函数
     function Student(){}//声明构造函数
```

### 2.4 变量

> - 变量是计算机内存中存储数据的标识符，根据变量名称可以获取到内存中存储的数据
> - 为什么要使用变量
>   - 使用变量可以方便的获取或者修改内存中的数据

#### 2.4.1 变量声明的几种方式

****

> **JavaScript是一门若数据类型的语言，所有变量的声明使用var,let,const,计算机根据值的数据类型去决定变量的数据类型。**
>
> 变量的声明有几种格式:
>
> ​	var 变量名  = 值 ;(ES6之前的声明格式)
>
> ​	let 变量名 = 值;(ES6中变量的声明方式)
>
> ​	const 变量名  = 值;(ES6中常量的声明方式)

**先声明再赋值:**

```javascript
var  num ;
	num = 200;
```

**声明的时候赋值:**

```javascript
var num = 300;
```

**声明多个变量后在赋值:**

```javascript
var num,age,address;
    num = 100;
    age = 99;
    addresss = "西安市";
```

**声明多个变量同时赋值:**

```javascript
var num = 100,age = 88, price = 99.99;
```

**变量必须先初始化再使用不然就是报错: undefined**

```javascript
var num ;
console.log(num);//undefined  未定义   就是变量存在但是没有值
```

#### 2.4.2 JavaScript 变量内存

![img](_media/173328266.png)

### 2.5 数据类型

#### 2.5.1 数据类型的基础

![image-20201021171253393](_media/image-20201021171253393.png)
> 数据类型的分类:
>
> **基本数据类型**:
>
> + undefined   未定义   变量声明了但是没有值.
>
> + boolean   true/false
>
> + Number   数字类型
>   + 正无穷大
>   + 负无穷大
>   + NaN  不是数字类型
> + isNaN  is not a number 
>   
> + String   字符串的值 只要被定义了就是不可变的
>   + 与某些编程语言（例如C）不同，JavaScript字符串是不可变的。这意味着一旦创建了字符串，就无法对其进行修改。(MDN官网)
>
> + bigint 
>   + 使用`BigInt`s，即使超出`Number`s的安全整数限制，您也可以安全地存储和操作大整数。
>
> + Symbol(Es6新添加的)
>
> 结构类型:Object   function  数组 .....
>
> 使用typeof 可以获取数据的数据类型

```html
<script>
      var num = 100 //数字类型
      var price = 99.99 //数字类型 中的浮点类型
      var result = true //boolea类型
      var name = 'joke' //字符串类型 字符串创建出来以后值就是不可以变化的
      var address = null //表示变量没有指向任何的对象
      var age = undefined //未定义  没有值
      var totalPrice = 2n
      var num1 = 0b101 // 二进制的值  十进制的值是5
      var num2 = 011 //八进制 十进制的值是9
      var num3 = 0x1f //十六进制  十进制的值是 15+16 = 31

      console.log(num)
      console.log(price)
      console.log(result)
      console.log(name)
      console.log(address)
      console.log(age)
      console.log(totalPrice)
      console.log(isNaN('Hello'))
      console.log(num1)
      console.log(num2)
      console.log(num3)
    </script>
```

![image-20201021172859010](_media/image-20201021172859010.png)

#### 2.5.2 数据类型的转换

1. 转化为字符串类型
   + toString()
   + String()
   + 拼接字符串

```html
	<script>
      var num = 123
      console.log(num)
      console.log(num.toString()) //使用方法转为字符串
      console.log(num + '') //拼接空的字符串转为字符串
      console.log(String(null)) //对于不能使用toString()的数值
    </script>
```

2. 转换为数值类型
   + Number()  数字的字符串类型  包含不是数字的值就是NAN
   + Number.parseInt()  转换为整数类型
   + Number.parseFloat() 转换为浮点类型
   + \+ \-   进行拼接和运算后的结果是数字值

```html
 <script>
      var str = '123'
      var price = '99.99'
      console.log(Number('123')) //数值类型的字符串转为数值类型
      console.log(Number('123abc')) //NaN 字符串中又是数字值的时候就是NaN
      console.log(Number.parseInt(str)) //转为整数类型
      console.log(Number.parseFloat(price)) //转为浮点类型
      console.log('123' + 0) //数值的运算可以自动转换 拼接后的是数字类型的值
      console.log('123' - 0) //进行运算后的值是原本的数字值
    </script>
```

3. 转换为boolean类型

> 0  ''(空字符串) null undefined NaN 会转换成false  其它都会转换成 true

```html
if (0) {
        console.log('1')
      } else {
        console.log('0')
      }
```

### 2.6 运算符

#### 2.6.1 算数运算符

| 运算符 | 描述              |
| :----- | :---------------- |
| +      | 加法 字符串的拼接 |
| -      | 减法              |
| *      | 乘法              |
| /      | 除法              |
| %      | 系数              |
| ++     | 递加              |
| --     | 递减              |

#### 2.6.2 赋值运算符

| 运算符 | 例子   | 等同于    |
| :----- | :----- | :-------- |
| =      | x = y  | x = y     |
| +=     | x += y | x = x + y |
| -=     | x -= y | x = x - y |
| *=     | x *= y | x = x * y |
| /=     | x /= y | x = x / y |
| %=     | x %= y | x = x % y |

#### 2.6.3 关系运算符

| 运算符 | 描述           |
| :----- | :------------- |
| ==     | 等于           |
| ===    | 等值等型       |
| !=     | 不相等         |
| !==    | 不等值或不等型 |
| >      | 大于           |
| <      | 小于           |
| >=     | 大于或等于     |
| <=     | 小于或等于     |
| ?      | 三元运算符     |

#### 2.6.4 逻辑运算符

| 运算符 | 描述   |
| :----- | :----- |
| &&     | 逻辑与 |
| \|\|   | 逻辑或 |
| !      | 逻辑非 |

#### 2.6.5 类型运算符

| 运算符     | 描述                                  |
| :--------- | :------------------------------------ |
| typeof     | 返回变量的类型。                      |
| instanceof | 返回 true，如果对象是对象类型的实例。 |

#### 2.6.6 位运算符

| 运算符 | 描述         | 例子    | 等同于       | 结果 | 十进制 |
| :----- | :----------- | :------ | :----------- | :--- | :----- |
| &      | 与           | 5 & 1   | 0101 & 0001  | 0001 | 1      |
| \|     | 或           | 5 \| 1  | 0101 \| 0001 | 0101 | 5      |
| ~      | 非           | ~ 5     | ~0101        | 1010 | 10     |
| ^      | 异或         | 5 ^ 1   | 0101 ^ 0001  | 0100 | 4      |
| <<     | 零填充左位移 | 5 << 1  | 0101 << 1    | 1010 | 10     |
| >>     | 有符号右位移 | 5 >> 1  | 0101 >> 1    | 0010 | 2      |
| >>>    | 零填充右位移 | 5 >>> 1 | 0101 >>> 1   | 0010 | 2      |

### 2.7 流程控制语句

> 表达式: 一个表达式可以产生一个值，有可能是运算、函数调用、有可能是字面量。表达式可以放在任何需要值的地方。

#### 2.7.1 顺序语句

> 程序的默认执行流程就是从上到下。从左到右的执行。

#### 2.7.2 分支语句

![image-20201022162006266](_media/image-20201022162006266.png)

> 分支语句分为以下几种:
>
> + if(布尔表达式/布尔值){ 执行的代码}
> + if() else{}
> + if () else if(){}
> + switch 语句
>
> **注意:**
>
> + undefined,null,0,-0,NaN,"" //空字符串  转为 flase 其他的值是true

```javascript
if (/* 条件表达式 */) {
  // 执行语句
}

if (/* 条件表达式 */){
  // 成立执行语句
} else {
  // 否则执行语句
}

if (/* 条件1 */){
  // 成立执行语句
} else if (/* 条件2 */){
  // 成立执行语句
} else if (/* 条件3 */){
  // 成立执行语句
} else {
  // 最后默认执行语句
}
```

```javascript
switch (expression) {
  case 常量1:
    语句;
    break;
  case 常量2:
    语句;
    break;
  case 常量3:
    语句;
    break;
  …
  case 常量n:
    语句;
    break;
  default:
    语句;
    break;
}
```

> 思考题: 
>
> var num = !!"123"; //结果是？
>
> var num = !!123; //结果是？

#### 2.7.3 循环语句

![image-20201022162321134](_media/image-20201022162321134.png)

> 循环语句分为以下:
>
> + while()
> + do{} while{}
> + for (){} 
> + for 循环嵌套

**while循环:**

> while 循环为true 时出现死循环，避免出现死循环

```javascript
// 当循环条件为true时，执行循环体，
// 当循环条件为false时，结束循环。
while (循环条件) {
  //循环体
}
```

**do while 循环:**

> do..while循环和while循环非常像，二者经常可以相互替代，但是do..while的特点是不管条件成不成立，都会执行一次。

```javascript
do {
  // 循环体;
} while (循环条件);
```



**For循环:**

> while和do...while一般用来解决无法确认次数的循环。for循环一般在循环次数确定的时候比较方便

```javascript
// for循环的表达式之间用的是;号分隔的，千万不要写成,
for (初始化表达式1; 判断表达式2; 自增表达式3) {
  // 循环体4
}
```

**Break:**

> break 语句跳出循环后，会继续执行该循环之后的代码

**Continue:**

> **continue 语句**中断循环中的迭代，如果出现了指定的条件，然后继续循环中的下一个迭代。

**Chrome断点调试工具:**

![image-20201022163807947](_media/image-20201022163807947.png)

###2.8 数组(Array)

> 所谓数组，就是将多个元素（通常是同一类型）按一定顺序排列放到一个集合中，那么这个集合我们就称之为数组.
>
> **注意:****
>
> 1. <font style='color:red;'>**在其他的严格型的语言中数组只能保存同一种数据类型的语言，在javascript中可以保存多种数据类型的值.**</font>
> 2. <font style="color:red;">**在其他严格型的语言中数组的只要被声明了，数组的长度就是不可以变化的，但是在JavaScript中数组的长度是可以变化的，获取数组的元素是通过数组的下标来获取，获取不到就是undefined** </font>

#### 2.8.1 数组的声明

> 数组的声明方式:
>
> 1. var [] arr = new Array()[1,2,3,4,5];
> 2. var [] arr = [2,3,4,5,6]
> 3. 数组的元素和获取是通过数据下标来进行，数组的下标是从0开始

```javascript
<script>
      //var array = new Array(2, 34, 54, 65, 76, 4, 99, 12)
      var array = [2, 34, 54, 65, 76, 4, 99, 12]
	//数组的遍历
      for (let index = 0; index < array.length; index++) {
        console.log(array[index])
      }
</script>
```

#### 2.8.2 **数组的最值:**

```javascript

```

#### 2.8.3 **数组的排序:**

> 数组常见的排序方式:
>
> + 冒泡排序
> + 选择排序
> + 插入排序
> + 快速排序
> + 归并排序
> + 希尔排序

```javascript

```

## 3. 函数(Function)

> 函数是 JavaScript 中的基本组件之一。 一个函数是 JavaScript 过程 — 一组执行任务或计算值的语句。要使用一个函数，你必须将其定义在你希望调用它的作用域内。
>
> 函数也是程序的基本单元，是完成特定代码的语句块。
>
> 在javaScript中我们可以将重复使用的代码封装起来，起个名字在其他的地方进行调用，就是函数
>
> <font style="color:red">JavaScript中函数的定义:</font>
>
> function 函数的名称(参数列表){
>
> ​	方法语句;
>
> }
>
> **函数只有被调用才能使用，可以重复调用和使用:**

### 3.1 函数的声明和使用

> 函数的声明以后并不能直接执行，函数只有被调用才能执行。
>
> 一个函数它通常只能干一件事情，但是也会有一些复杂的函数，函数的名称我们通常使用动词。

#### 3.1.1 直接声明

```javascript
/*函数的声明*/
function show(){
    console.log("Hello JavaScript");
}
/*函数的调用*/
show();
show();
```

#### 3.1.2 函数表达式声明函数

```javascript
/*函数式声明函数*/
var show = function(){//后边其实是一个匿名的函数
     console.log("Hello JavaScript");
}
console.log(show);
/*函数式声明的函数的调用*/
show();
show();
```

#### 3.1.3 全局变量和局部变量

> 全局变量:  在函数外声明的变量，网页上的所有脚本和函数都能访问它
>
> 局部变量：在函数内部声明的变量（必须使用var），只能在函数内部访问它
>
> + 可以在不同的函数中使用名称相同的局部变量
>
> 变量的生命周期:
>
> + 全局变量在网页关闭以后被从内存中清除
> + 局部变量在方法执行完成以后从内存中被清除

### 3.2 函数的返回值

> 比如我们需要一个计算数字和的函数，执行完成以后我们要拿到数字的和的值。
>
> **返回值函数的声明:**
>
> function show(){
>
> ​		return  返回值;
>
> }
>
> 如果函数使用 return语句，但是return后面没有任何值，那么函数的返回值也是：undefined

```javascript
function sum(){
    return 10 + 20;
}
sum();//有返回值的函数调用不会出现结果
var result = sum();//必须先接收返回值
console.log(result);
```

> 在函数执行的时候,如果程序不行再继续向后边执行我们可以使用return false 终止程序运行。

```javascript
 <script>
      function show() {
        if (10 > 9) {
          return false
        }
        //下面的语句并不会执行
        console.log('JavaScript')
      }
      show()
</script>
```

### 3.3 函数的传参

> ```javascript
> //param 是形式参数 仅仅是在函数中进行占位
> function [name]([param[, param[, ... param]]]) {
>    statements
> }
> ```

#### 3.3.1 普通参数

```javascript
//javaScript是弱数据类型的语言 所以在声明参数的时候不需要数据类型，系统会根据函数调用时传入的参数的数据类型判断形式参数的数据类型
function sum(a,b){
    console.log(a+b);
}
sum(10,20);
sum(99.99,90);
```

#### 3.3.2 可变参数

> 有的时候在程序的执行中我们并不确定，参数的个数，就可以使用可变参数。可变参数的本质就是数组.
>
> function show (...param){}
>
> <font style="color:red;">function show(name,age,.....param){} 多个参数和可变参数使用的时候可变参数必须在最后边，前边的参数取完值剩下的交给可变参数。可变参数在前边会报错</font>

```javascript
 <script>
      function show(...param) {
        console.log(param)
      }
      show(1, 2, 3, 4, 5, 5)
      function sum(name, age, ...param) {
        console.log(name + ':' + age + ':' + param)
      }
      sum('joke', 23, 45, 67, 89)
    </script>
```

#### 3.3.3 arguments的使用

> JavaScript中，arguments对象是比较特别的一个对象，实际上是当前函数的一个内置属性。也就是说所有函数都内置了一个arguments对象，arguments对象中存储了传递的所有的实参。arguments是一个伪数组，因此及可以进行遍历

```javascript
 function sum(name, age, ...param) {
        console.log(arguments);
      }
      sum('joke', 23, 45, 67, 89)
```

![image-20201022174659249](_media/image-20201022174659249.png)

#### 3.3.4 匿名函数

> 没有名字的函数,通常是将一个匿名函数交给一个变量去引用。也就是函数的函数表达式声明形式。

```javascript
var show = function(){}
```

#### 3.3.5 函数的自调用  :small_airplane:

> 匿名函数不能通过直接调用来执行，因此可以通过匿名函数的自调用的方式来执行
>
> 自我调用的函数只能使用一次。

```javascript
(function(){
    console.log("Helllo 自我调用的函数");
})()
//为了区别明显在前面加分号
 ;(function (a, b) {
        console.log('自我的调用函数的第一种使用方式:' + (a + b))
      })(100, 200)

 ;(function (a, b) {
        console.log('自我的调用函数的第二种使用方式:' + (a + b))
      }(100, 200))
//还有一种书写方式
  +function (a, b) {
        console.log('自我的调用函数的第一种使用方式:' + (a + b))
      }(100, 200)
```

> `+`号使得js解释器认为它现在在处理的是一个表达式, 而非函数定义. 如果不写这个`+`号, 解释器会按照函数定义去处理, 并认为后面的`()`是语法错误.
>
> 其实除了`+`号, `-`, `!`, `~`以及其他一元操作符都可以产生相同的效果.
>
> 与要在用`()`把函数包起来的常用写法相比, 这种写法的好处(也许)就是只要在前面加个`+`就行了, 更省事儿. 当然, 最后的`();`是一定不能少的.

#### 3.5.6 函数作为参数和返回值

> 函数也是一种数据类型。所以函数也可以作为参数来使用后面回见到很多的(回调函数)
>
> 函数也可以作为返回值来使用

```javascript
<script>
    //函数作为参数使用
      function num(a, b) {
        return a + b
      }
      function show(a) {
        console.log(a)
      }
      show(num(100, 200))
  </script>

//函数作为返回值使用
function show(a){
    var num = 100;
    return function(){
        return a+num;
    }
}
show(200)()//返回值的函数执行;
```

### 3.4 箭头函数(重点) :kissing_smiling_eyes:

> 在ES6的语法中，新规定了一种函数叫做箭头函数 ，现在使用的普遍较多,是对函数式编程的引进。
>
> 语法格式:  var show = (参数列表)=>{
>
> ​	执行语句;
>
> }

```javascript
 <script>
      var show = () => {
        console.log('Hello World')
      }
      var sum = () => console.log('没有返回值可以省略 大括号')
      // 没有返回值的带参数的箭头函数
      var num = (a, b) => console.log(a + b)
      // 有返回值  有参数的 箭头函数
      var caculate = (a, b) => {
        return a + b
      }
</script>
```

### 3.5 块级作用域 :exclamation:

> 任何一对花括号（｛和｝）中的语句集都属于一个块，在这之中定义的所有变量在代码块外都是不可见的，我们称之为块级作用域。
> **在es5之前没有块级作用域的的概念,只有函数作用域**，现阶段可以认为JavaScript没有块级作用域

#### 3.5.1 基本的块级作用域

```javascript
<script>
      //全局变量
      var num = 100
      function show() {
        console.log(num)
        //局部变量
        var age = 99
        console.log(age)
      }
      console.log(num) //q00
      console.log(age) //报错没有被定义
    </script>
```

**在代码块中使用var 没有作用域:**

```javascript
//全局变量
      var num = 100
      {
        console.log(num)
        var sum = 100
      }
      console.log(sum) //100 输出成功了  那就是有问题
```

#### 3.5.2 作用域链

> 只有函数可以制造作用域结构， 那么只要是代码，就至少有一个作用域, 即全局作用域。凡是代码中有函数，那么这个函数就构成另一个作用域。如果函数中还有函数，那么在这个作用域中就又可以诞生一个作用域。
>
> 将这样的所有的作用域列出来，可以有一个结构: 函数内指向函数外的链式结构。就称作作用域链。

### 3.6 嵌套函数和 闭包(closure) :exclamation:

### 3.7 this 关键字 :exclamation:

## 4. JavaScript常用的对象和方法

+ Object
+ Date
+ Array
+ Math
+ Number
+ reqexp (正则表达式)
+ Global (全局对象)
+ String
+ Function 

## 5. JavaScript的面向对象

### 5.1 构造函数自定义对象

### 5.2 对象的原型

### 5.3 原型链

### 5.4 JavaScript对象的继承

## 6. BOM

## 7. DOM









