# 加载和执行

1. 雅虎特别小组提出的规则: 将脚本放在底部
2. 组织脚本，将几个js文件打包合并，可用打包工具
3. 无阻赛的脚本:　在页面加载完成后加载js代码
   - 延迟的脚本--defer属性：指明本元素所含的脚本不会修改DOM。兼容性差（IE,Firefox 3.5）
   - 动态脚本元素--DOM方法创建script标签(通用)

   ```javaScript
        var script = document.createElement("script");
        script.type = "text/javascript";
        script.src = "你需要的路径";
        document.getElementsByTagName("head")[0].appendChild(script);
   ```

   - XMLHttpRequest脚本注入

    ```javaScript
       var xhr = new XMLHttpRequest();
       xhr.open("get","路径",true);
       xhr.onreadystatechange = function(){
           if(xhr.readyState == 4){
               if(xhr.status >= 200 && xhr.status < 300 || xhr.status == 304){
                   var script = document.creatElement("script");
                   script.type = "text/javascript";
                   script.text = xhr.responseText;
                   document.body.appendChild(script);
               }
           }
       }
    ```

    - 推荐的无阻赛模式
  
## 直接量
- 字符串 数字 布尔值 对象 数组 函数 正则表达式 null undefined
