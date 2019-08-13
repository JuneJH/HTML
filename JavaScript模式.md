# 基本技巧
1. 减少使用全局变量
   - 暗示全局变量
   - 命名空间模式或立即执行函数
   - 使用var声明的全局变量不能删除，而暗示全局变量可以删除（他不是真正的变量，而是全局对象的属性）
   - ES5的严格模式不能这样用
   ```javascripr
   // 获取全局对象
      var global = (function (){
          return this;
      }())
    ```
2. 单一var模式
3. for循环
  - 缓存数组的长度，var len = array.length;
  - 逐步减至0
4. for-in循环    也称枚举   
    - 使用hasOwnProperty()方法来过滤原型链上的属性
