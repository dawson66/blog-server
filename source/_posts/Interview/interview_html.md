---
title: 高频面试题汇总之HTML
tags: HTML&CSS
cover: cover_interview_html_03.jpeg
categories:
  - Interview
typora-root-url: ./interview_html
copyright _author: xiaoming
copyright_ author _href: 'https://xxxxxx.com'
abbrlink: 21b30e37
date: 2021-06-07 20:05:30
---



###### 1. HTML5新增的内容有哪些？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 2. HTML5新增的语义化标签有哪些？说一下你对语义话标签的理解？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 3. 网络中使用最多的图片格式有哪些？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 4. 视频/音频标签的使用？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 5. 说一下HTML5 Drag API使用？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 1. JavaScript有哪几种数据类型？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### . ？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### . ？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### . ？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### . ？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### . ？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### . ？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### . ？

<details><summary><b>Anwser</b></summary>
<p>



</p> 
</details>

---

###### 

### DOM事件类型

1. **请问DOM事件级别**

   ```javascript
   DOM 0级：dom.onclick=function(){}
   DOM 2级：document.addEventListener('click',()=>{})
   DOM 3级：document.addEventListener('keyup',()=>{})
   ```

2. **DOM事件模型**

   * 捕获
   * 冒泡

3. **DOM事件流**

   * 捕获>目标阶段>冒泡

   * 扩展：

     * 描述DOM事件捕获的具体流程？

       ```javascript
       window>document>html>body
       ```

   * 延伸：如何获取html?

     ```javascript
     document.documentElement
     ```

4. **Event对象**

   * 概念：[Event](https://developer.mozilla.org/zh-CN/docs/Web/API/Event)

   * 问题：Event对象的常见应用？

     ```javascript
     event.preventDefault()
     event.stopPropagation()
     event.stopImmediatePropagation()
     event.target
     event.currentTarget
     ```

   * 延伸：

     * [js中的stopImmediatePropagation方法和stopPropagation方法的区别](https://www.cnblogs.com/EnSnail/p/9796237.html)
     * [event.target和event.currentTarget的区别](https://www.cnblogs.com/yzhihao/p/9398917.html)

5. **自定义事件**

   * 可以用Event或者[CustomEvent](https://developer.mozilla.org/zh-CN/docs/Web/API/CustomEvent)

     ```javascript
     // CustomEvent实现自定义事件
     
     // 请后续亲自练习补充
     ```

   * 延续：Event和CustomEvent的区别是CustomEvent可以传参

6. **fastclick的作用是什么？**

   * [fastclick](https://github.com/ftlabs/fastclick)
   * 主要解决的是移动端点击300ms延迟，具体参考fastclick官网介绍及用法
   * 延伸：fastclick原理？
     * 利用event.preventDefault()阻止默认行为，然后派发自定义click事件

