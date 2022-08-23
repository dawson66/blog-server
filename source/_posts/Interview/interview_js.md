---
title: 【基础】50个JavaScript知识点
tags:
  - Interview
cover: /images/cover_JavaScript基础.jpeg
categories:
  - Interview
abbrlink: 80ea8f61
date: 2021-06-07 20:03:30
---
### 一面

注重基础知识的掌握和理解

1. **var、let、const的区别**

   ```javascript
   let 不存在变量提升，不能重复定义，会产生块级作用域，存在暂时性死区
   const 声明就得赋值，变量的值不得改动
   ```

   * [一道面试题引发的“血案”](https://juejin.cn/post/6844903684204314638)

2. **变量提升&作用域**

   * [图解作用域及闭包](https://juejin.cn/post/6844903603145015310)
   * [深入理解Javascript作用域和作用域链](https://juejin.cn/post/6844903797135769614)

3. **字符串相关**

   * 获取字符串长度的方法？

     ```javascript
     // 1. 
     
     // 2.
     
     // 3.
     
     请自我总结～
     ```

4. **原型链**

   * [用自己的方式（图）理解constructor、prototype、proto和原型链](https://juejin.cn/post/6844903837623386126)

5. **This**

   * [嗨，你真的懂this吗](https://juejin.cn/post/6844903805587619854)
   * [Js中this的用法](https://xieyufei.com/2016/09/18/Explain-Js-This.html)
   * [通过运行机制看this绑定、作用域、作用域链和闭包](https://juejin.cn/post/6844904007027146766)
   * [JavaScript—this的六道坎](https://blog.crimx.com/2016/05/12/understanding-this/)

6. **闭包**

   * [图解JS闭包形成的原因](https://segmentfault.com/a/1190000011504517)

7. **继承**

   * ```javascript
     // 代码实现继承
     
     
     ```

8. 请问new执行的操作

   1. 创建一个全新的对象
   2. 这个新对象会被执行[[Prototype]]连接
   3. 这个新对象会绑定到函数调用的this
   4. 如果函数没有返回其他对象，那么new表达式中的函数调用会自动返回这个新对象

9. 你了解Object.create吗？(vue,vuex源码中经常使用该方法来初始化一个新对象)

   * [详解Object.create(null)](https://juejin.cn/post/6844903589815517192)



### 二面

侧重考察知识面、高阶知识、深入原理等

1. setTimeout和setInterval和requestAnimationFrame

   * [关于setInterval与setTimeout作用域问题](https://my.oschina.net/huskydog/blog/1553720)
   * [注意点——setTimeout、setInterval使用](https://juejin.cn/post/6844903501651247118)
   * [你真的了解setTimeout和setInterval吗？](http://qingbob.com/difference-between-settimeout-setinterval/)
   * [关于setTimeout](https://juejin.cn/post/6844903573826830343)
   * [深度解密setTimeout和setInterval——为setInterval正名！](https://juejin.cn/post/6844903773622501383)
   * [从setTimeout/setInterval看js线程](https://palmer.arkstack.cn/2017/12/%E4%BB%8EsetTimeout-setInterval%E7%9C%8BJS%E7%BA%BF%E7%A8%8B/?hmsr=toutiao.io&utm_medium=toutiao.io&utm_source=toutiao.io)
   * [你知道的requestAnimationFrame【从0到0.1】](https://juejin.cn/post/6844903761102536718)

2. Json.parse(Json.stringify())的缺点

   ```javascript
   在JSON.stringify()阶段
   
   1.如果obj里面有时间对象，则JSON.stringify后再JSON.parse的结果，时间将只是字符串的形式，而不是对象的形式
   
   2.如果obj里有RegExp(正则表达式的缩写)、Error对象，则序列化的结果将只得到空对象
   
   3、如果obj里有函数，undefined，则序列化的结果会把函数或 undefined丢失
   
   4、如果obj里有NaN、Infinity和-Infinity，则序列化的结果会变成null
   
   5、JSON.stringify()只能序列化对象的可枚举的自有属性，例如 如果obj中的对象是有构造函数生成的， 则使用JSON.parse(JSON.stringify(obj))深拷贝后，会丢弃对象的constructor
   
   6、如果对象中存在循环引用的情况也无法正确实现深拷贝
   ```

3. **遍历**

   * 文章：[javascript遍历对象、数组总结](https://www.cnblogs.com/chenyablog/p/6477866.html)
   * 对象遍历
   * 数组遍历

4. **严格模式**

5. **设计模式**

   * [菜鸟教程-设计模式](https://www.runoob.com/design-pattern/factory-pattern.html)
   * [Javascript设计模式es6(23种)](https://juejin.cn/post/6844904032826294286)
   * [Javascript中常见的十五种设计模式](https://www.cnblogs.com/imwtr/p/9451129.html)

