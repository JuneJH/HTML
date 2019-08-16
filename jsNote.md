# JavaScript

[toc]

## 浏览器

Mosaic
liveScript -> javaScript

### shell    内核

### js的逼格

解释性语言：跨平台 稍微慢
单线程：js引擎是单线程
标准：ECMA，也称ECMAScript
ecmaScript
DOM
BOM

### js执行队列

轮转时间片：类似吃饭

### 主流浏览器

IE        ->    trident
Chrome    ->    webkit/blink
firefox   ->    Gecko
Opera     ->    presto
Safari    ->    webkit
**结构行为样式相分离**

## JS基本语法

### 数据类型

1. 不可改变的原始值（只有覆盖掉，改变值时重新开辟空间）  Number String Boolean undefined null
2. 引用值  array object function ....date RegExp

(原始值)stack 先进后出 引用值存放的是heap的地址             heap

### js错误

1. 低级错误（语法解析错误）js报错不会影响下一个代码块

### js运算符

+ 可以链接字符串  任何数据类型和字符串相加，都是字符串相加

== NaN不等于任何东西，自己都不等于

### 逻辑运算符

 &&  ||  !
 undefined null NaN "" 0 false ====> 转换成布尔值都是false 其余都是turn;

 && 短路语句

 || 兼容性判断

### 条件语句

```javascript
   if(条件){

   }
```

### 循环

#### for

```javaScript
for(var i = 0; i < 10; i ++){

}
```

1. var i = 0;
2. if(i < 10){执行体}
3. i ++;
4. ->第2步
5. -> 第三步
6. -> 4

never-ending loop

#### while

#### do while

```javaScript
do{

}while
```

### 条件

```javaScript
switch(条件){
   case 1:
       console.log('a');
       break;
   case 2:
       console.log('b');
       break;
}
```

## 数组

取值[index]

length:  数组的长度

## 对象 object

```javaScript
var obj = {
   key : value,
}
```

## 编程形式

1. 面向过程 第一步，第二步 按照过程
2. 面向对象 找对象来干，依靠什么来去做

## typeof()

1. 返回的值：number string boolean object undefined function
    - object : {},[],null(代替空对象出现)

### 显式转换

1. Number() 转换为数字 Number(undefined)---> NaN Number(true)---> 1  Number(null)---> 0;
2. parseInt() 转换为整形数据，true这类值转成NaN，“123abc” ——————》123
   - 参数(需要转换的数,该数的进制（radix：2~36）)
3. parseFloat(),只有一个参数
4. String()
5. Boolean()
6. toString(（目标基底）radix):   undefinded和null 不能用。将十进制的数据算做目标进制

### 隐式转换

1. isNaN() ---> Number() <---> NaN
2.  ++/-- +/- (一元正负)
   - ++ / -- : ---> Number() ---> ++
   -  + a/-a : ---> Number() 
3.  +  :当加号两侧有一个是字符串就会调用String();
4.  -*/% : ---/Number()
5.  && || ! ---> Boolean()
6.  < > <= >= ---> Number()  但是两个字符串相比是ASC码。只要有数字就会发生转换
7.   == != 

#### 绝对等于

=== ， ！==

### 递归

1. 找规律，数学公式
2. 找出口

### 预编译

#### JS运行三部曲

1. 语法解析
2. 预编译
3. 解释执行

##### window的域
1. 暗示全局变量
   - 暗示全局变量没有提升，只有当运行发现了未声明就赋值时，才将其放进GO
2. window就是全局

##### 预编译的过程

- 预编译发生在函数执行前一刻
1. 创建AO   Activation Object（执行期上下文） ——>  作用域
   - 创建AO
   - 找形参，变量声明，赋值为undefined
   - 形参赋值
   - 找函数声明，并把函数体赋值

## 作用域

1. 执行器上下文，每次执行的都是独一无二的
2. 作用域链，链接的都是同一个AO

## 闭包

**内存泄露**

### 立即执行函数

- 针对初始化功能的函数
- 只有表达式才能被执行符号执行（()） 立即执行函数，函数声明后加执行符号无用，函数表达式可以
- 能被执行符号执行的函数，就自动放弃函数名
- 如果在函数声明的前面加上 正（+），负（-），非（!）,或（||），与（&&）函数声明将变成表达式，也将放弃函数名

```javaScript
     function test(a,b,c) {
         console.log(a,b,c)
     }(1,2,3);
```
以上代码不报错，但无意义

<<<<<<< HEAD
##### 命名空间

1. 对象形式
2. 闭包形式
=======
#### 对象

1. 删属性  delete 属性

##### 对象的创建方法  
1. var obj = {}  plainObject 对象字面量/对象直接量
2. 构造函数 
       - 系统自带的构造函数  Object()
       - 自定义
       - 操作符  new

##### 构造函数内部原理

1. 在函数体最前面隐式的添加
  - var this = {};
2. 执行 this.name = XXX;
3. 隐式的添加
  - return this

##### 包装类

var num = new Number(123);
var str = new String('123');
原始值能有方法就是因为隐式发生  new Number()

**原始值不能有属性，不报错，系统会隐式操作**
包装类
```javascript
var str = '123';
//隐式操作   new String('123').length = 2; delete
str.length = 2;
console.log(str) ---> '123'
```

#### 原型

1. 原型是function对象的一个属性，它定义了构造函数制造出来的对象的共有祖先。通过该构造函数产生的对象，可以继承该原型的属性和方法。原型也是对象
2. 利用原型的特点和概念，可以提取共有属性
3. 对象如何查看原型---> 隐式属性_proto_   可以通过这个属性可以修改其原型。可以修改，不能增加，如果没有原型就不能增加
4. 对象如何查看对象的构造函数---> 

##### 原型链

1. 如何构成原型链
2. 原型链上的增删改查
3. 绝大多数对象的最终都会继承自Object.prototype
4. Object.creat(原型)  这个方法的参数可以是一个对象或者一个null，因此造成3中是绝大多数
```javascipt
   var obj = Object.creat(null);
   <!-- 没有原型 -->
```

##### call apply
1. 改变this指向
2. 第一个参数都是对象，call的后面参数为挨个写，apply为实参列表

#### 继承模式

1. 传统继承模式

2. 借用构造函数

3. 共享原型

   - 不能随便改动自己的原型
   Son.prototype = Father.prototype

4. 圣杯模式
   function F(){}
   F.prototype = Father.prototype
   Son.prototype = new F();
```javascript
// 封装圣杯模式继承方法
function inherit(Target,Origin){
  function F(){};
  F.prototype = Origin.prototype;
  Target.prototype = new F();
  Target.prototype.constuctor = Target;
  Taeget.prototype.uber = Origin.prototype;
}

//yahoo
var inherit = (function (){
  function F(){};
  return function (Target,Origin){
    F.prototype = Origin.prototype;
    Target.prototype = new F();
    Target.prototype.constuctor = Target;
    Target.prototype.uber = Origin;
  }
}())
```
>>>>>>> 8f425b78c9472c838ca68fe21a88248f0a788e69

##### 枚举 对象
1. for in   ----- 会拿到原型上的方法(系统设的原型否，自己设置的会)    对象.hasOwnProperty(属性)
            ----   in   判断是否是对象的包括原型（hasOwnProperty，区别）
            ----- instanceof  A instanceof B   看A对象的原型链上  有没有 B的原型

**判断数组和对象**
1. constructor        数组的constructor为array
2. instanceof
3. toString   call   只有它没有问题，以上两个在父子域判断有误

##### this
1. 函数预编译过程this ---> window
2. 全局作用域里this ----> window
3. call/apply 可以改变函数运行时this指向
4. obj.function();  function()里面的this指向obj


##### arguments.callee
得到函数的引用（指向函数自身引用）====立即执行函数需要找到自身（递归）
es5失效
##### func.caller
得到在什么环境下运行
es5失效

#### 三目运算

#### 数组

1. 定义数组

- 构造方法  var arr = new Array(10) 创建长度为10的稀松数组   填小数只有一位参数报错

- 字面量

2. 数组的读写
 - 没毛病

3. 改变原数组
  - push
  - pop   将数组最后一位剪切出来并返回出来
  - shift  弹出数组第一位
  - unshift 与push一样，方向相反，从数组前面加
  - sort    排序  有接口  arr.sort(function (){})   1. 必须写2个形参    2. 看返回值  当返回值为负数，那么前面的数放在前面 正数  后面在前  0 不动
  - reverse  把原数组逆转顺序并返回
  - splice  参数（从第几位开始，截取多少的长度，在切口处添加新的数据），返回截取的数组
4. 不改变原数组  返回一个新数组 关注参数
  - concat 连接数组，返回一个新数组
  - toString  将数组变成字符串
  - slice  参数（从该位开始截取，截取到该位）
  

  - join   （按照此参数把数组进行连接返回字符串）

  - split  （字符串的方法）  
  
  join ---- > split  互逆

  #### 类数组
  
  属性要为索引（数字）属性 ，必须有length属性，最好加上push
  加上splice

  好处
  对象和数组好处和在一起


#### try...catch()

try{

}catch(e){

}

1. 在 try里面发生的错误，不会执行错误后的try里面的代码
2. Error.name的六种值对应的信息
 - EvalError: eval()的使用与定义不一致
 - RangeError: 数值越界
 - ReferenceError: 非法或不能识别的引用数值
 - SyntaxError: 发生语法解析错误
 - TypeError: 操作数类型错误
 - UrlError:URL处理函数使用不当