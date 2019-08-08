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