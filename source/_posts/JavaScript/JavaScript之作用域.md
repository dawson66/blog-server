---
title: JavaScript之作用域
tags: JavaScript
categories:
  - JavaScript基础
cover: /images/cover_JavaScript基础.jpeg
abbrlink: b1dec25d
date: 2021-02-03 17:46:45
---

#### 预编译

```javascript
// 现象一
test()  			// test
function test(){
  console.log('test');
}


//现象二 
console.log(a);  //undefined
var a=10;


// => 函数声明整体提升；变量只有声明提升，赋值不提升。
// => 要明白 var a=1; 是两个步骤  声明 赋值
```



1. 暗示全局变量 imply global variable

```javascript
var a=1; 	 
b=2;    //此处的b未声明就赋值，暗示为全局变量


console.log(window.b);  //2

// =>
window={
  a:1,
  b:2
}

// 现象三
 function test1(){
   var a=b=1;
 }
test1();

console.log(b);			//1
console.log(window.a)  // undefined     //访问对象中不存在的属性，那么默认返回的是undefined,而直接访问变量，则直接报错
console.log(a);			// Uncaught ReferenceError: a is not defined  =>  b 暗示为全局变量了 所以可以访问

=> 在函数内部没有声明该变量，却赋值了，那么该变量将会提升到全局（存储到window对象中了）。
```



2. GO  === window

   global object 全局上下文

   **注：**JavaScript中GO可以理解为`window`对象，Node中GO可以理解为`global`对象

   ```javascript
   var a=1;
   function a(){
     console.log('a');
   }
   
   console.log(a);    //
   
   // GO
   // 1. 找变量
   // 2. 找函数声明
   // 3. 执行
   /* 
   	GO={
   		 第一步					第二步           第三步
   		a:undefined -> function a(){} -> 1;
   	}
   */
   ```

   

