---
title: JavaScript之遍历
tags: JavaScript
categories:
  - JavaScript基础
cover: /images/cover_JavaScript基础.jpeg
abbrlink: 3fd07667
date: 2021-02-03 17:46:45
---


### 1. 中断循环：

* continue：中断本次循环。
* break跳出最里层的循环。
* return 直接跳出循环；

```javascript
for (let i = 0, len = array.length; i < len; i++) {
    for (let j = i, lenj = array.length; j < len; j++) {
        if (array[j] == 1) {
            return false;
        }
        console.log('内层循环');
    }
    // console.log('最外层循环');
}

//output
//Illegal return statement
```

提示：for语句是没有局部作用域概念的，所以只有把for语句放在函数中时，才可以使用return语句。

### 2. 遍历数组


#### 2.1 普通for循环遍历

```javascript
//最简单的一种，想中断也可以中断，性能上也还可以
const array = [1, 3, 5, 7, 9];
for (let i = 0; i < array.length; i++) {
    console.log(i,array[i]);
}

// output
0 1
1 3
2 5
3 7
4 9

//优化版
//使用临时变量，将长度缓存起来，避免重复获取数组长度，当数组较大时优化效果比较明显。
//这种方法基本上是所有循环遍历方法性能中最高的一种，并且这一类型的for循环可以通过用break来中断循环
for (let i = 0, len = array.length; i < len; i++) {
    if (array[i] == 7) break;
    console.log(array[i]);
}

// output 1 3 5
```

#### 2.2 for in 遍历

   ```javascript
   const array = [1, 3, 5, 7, 9];
   for (const key in array) {
       console.log(key, array[key]);
   }
   //同上
   
   //for in不仅可以对数组,也可以对enumerable对象操作
    let obj = { a: 1, b: 2, c: 3, d: 'hello world!' }
    for (const key in obj) {
        console.log(key, obj[key], obj.key);  //注意此处
    }
   
   // a 1 undefined
   // b 2 undefined
   // c 3 undefined
   // d hello world undefined
   
   //这是因为  obj.key  计算机底层会变成 obj['key']  并不会将key当作变量处理
   ```


#### 2.3 for each 遍历

   * Array类型自带的，便捷，优雅。
   * 不能中断循环，如下。食之无味，弃之可惜。可以采用some(),every()来实现。

```javascript
array.forEach((element, index, arr) => {
    if (element == 7) return false;
    console.log(element, index, arr);
});

//output
// 1 0 [1,3,5,7,9]
// 3 1 [1,3,5,7,9]
// 5 2 [1,3,5,7,9]
// 9 4 [1,3,5,7,9]
```

#### 2.4 for of 遍历(ES6)
   * 这是最简洁、最直接的遍历数组元素的语法。
   * 这个方法避开了for-in循环的所有缺陷。
   * 与forEach()不同的是，它可以正确响应break、continue和return语句。
   * 性能要好于for-in，但仍然比不上普通for循环。

```javascript
const array=[1,3,5,7,9];
for (const item of array) {
    console.log(item);
}

//output
// 1 3 5 7 9
```

   这里主要介绍一下[Iterator及for of](https://es6.ruanyifeng.com/#docs/iterator)的概念：

   JavaScript目前有四种表示 **集合** 的数据结构：Array、Object、[Set、Map](https://es6.ruanyifeng.com/#docs/set-map)，后两种为ES6新增。有了这四种数据集合，用户可以组合使用它们来定义自己的数据结构，比如数组的成员是Map，Map 的成员是对象。这样就需要一种统一的接口机制，来处理所有不同的数据结构——遍历器（Iterator）。详情请参考阮大佬ECMAScript。

#### 2.5 Array.prototype.some

   * some作为一个用来检测数组是否满足一些条件的函数存在，同样是可以用作遍历的函数签名通forEach
   * 当callback的返回值匹配为true则直接返回true，如果所有的callback匹配均为false，则返回false。

```javascript
array.some((element,index,arr)=>{
    console.log(element,index,arr);
})

//output
// 1 0 [1,3,5,7,9]
// 3 1 [1,3,5,7,9]
// 5 2 [1,3,5,7,9]
// 9 4 [1,3,5,7,9]
```

#### 2.6 Array.prototype.every

```javascript
array.every((element,index,arr)=>{
    console.log(element,index,arr);
})

//output
// 1 0 [1, 3, 5, 7, 9]
```

#### 2.7 Array.prototype.filter

```javascript
array.filter((element,index,arr)=>{
    if(element>7){
        console.log(element,index,arr);
    }
})

//output
//9 4 [1,3,5,7,9]
```

#### 2.8 Array.prototype.map

```javascript
let arr=array.map((currentValue,index,arr)=>{
    return currentValue*2
})
console.log(arr);
```

   

### 3. 遍历对象

#### 3.1 for in

* 尽量用for-in遍历对象，而不是遍历数组。
* 只列举对象的显示成员（自定义成员）。

```javascript
const obj={name:'张三',getName(){console.log(this.name);}}
for (const key in obj) {
    console.log(obj[key]);
}

//output  没有toString,valueOf等内置属性（或称内置成员，隐藏属性和预定义属性）
//张三  getName(){console.log(this.name)}
```

**思考：for in遍历对象输出的顺序是什么？**



