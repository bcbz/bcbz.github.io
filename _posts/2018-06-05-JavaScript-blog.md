---
layout:     post
title:      JavaScript
subtitle:   JavaScript 内置对象（Array）
date:       2018-06-05
author:     bcbz
header-img: img/posts/markdown-readme/post-bg-coffee.jpg
catalog: true
tags:
    - JavaScript
    - Array
---
## 描述
##### 创建数组
```JavaScript
[element0, element1, ..., elementN]
new Array(element0, element1[, ...[, elementN]])
new Array(arrayLength)
```
``arrayLength`` 支持一个范围在 0 到 232-1 之间的整数。

##  JavaScript 内置对象（Array）
* [属性](#property)
  * [Array.length](#length)
  * [Array.prototype](#prototype)
* [方法](#method)
  * [Array.slice()](#slice)
---

| 兼容性 | Chrome | Edge | Firefox | IE | Opera | Safari |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| [length](#length)| Yes| Yes | 1 | yes | Yes| Yes |
| [prototype](#prototype) | Yes| Yes | 1 | Yes | Yes| Yes |

---
<a id="property"></a>
### 属性
- 数据属性有四个描述其行为的特性

|  | 默认值 | 描述 |
| :-: | :-: | :-: |
| Configurable | True |  |
| Enumerable | False |  |
| writable | False |  |
| value |  |  |

<a id="length"></a>
#### Array.length

- ``length``属性的属性特征

| 特征 | 默认值 |
| :-: | :-: | :-: |
| Configurable | False |
| Enumerable | False |
| writable | True |

- ``length`` 属性的值是一个 0 到 2^32-1 的整数。
```JavaScript
  //Uncaught RangeError: Invalid array length;
  var array = new Array(4294967296);//2^32 = 4294967296
```
- 可以通过设置 ``length`` 属性的值来截取数组，或扩展数组。但是， ``length``  属性不一定表示数组中定义值的个数。
```JavaScript
  var array = ['0','1','2'];
  array.length = 2;
  console.log(array);//['0','1']

  array.length = 5;
  console.log(array);//['0','1',undefined,undefined,undefined]

  array.length = 1;//['0']  
  array[5] = '5';
  console.log(array);//['0',undefined,undefined,undefined,undefined,'5']
```
<a id="prototype"></a>
#### Array.prototype
- ``prototype``属性的属性特征

| 特征 | 默认值 |
| :-: | :-: | :-: |
| Configurable | False |
| Enumerable | False |
| writable | False |

- ``Array.prototype`` 属性表示 ``Array`` 构造函数的原型，并允许您向所有Array对象添加新的属性和方法。
```JavaScript
/*
  如果JavaScript本身不提供 first() 方法，
  添加一个返回数组的第一个元素的新方法。
*/
if(!Array.prototype.first) {
  Array.prototype.first = function() {
    return this[0];
  }
}
var array = ['0','1','2'];
console.log(array.first());//0
```
- ``Array.prototype.constructor``  
所有的数组实例都继承了这个属性，返回对创建此对象的数组函数的引用。

<a id="method"></a>
### 方法

| 兼容性 | IE | Chrome | Edge | Firefox | Opera | Safari |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| [slice](#slice)| Yes | Yes | Yes | 1 | Yes| Yes |
| [toLocaleString](#toLocaleString)| Yes | Yes | Yes | 1 | Yes| Yes |
| [toString](#toString)| Yes | Yes | Yes | 1 | Yes| Yes |
| [concat](#concat)| 5.5 | 1 | Yes | 1 | Yes| Yes |
| [join](#join)| 5.5 | 1 | Yes | 1 | Yes| Yes |
| [pop](#pop)| 5.5 | 1 | Yes | 1 | Yes| Yes |
| [push](#push)| 5.5 | 1 | Yes | 1 | Yes| Yes |
| [reverse](#reverse)| 5.5 | 1 | Yes | 1 | Yes| Yes |
| [shift](#shift)| 5.5 | 1 | Yes | 1 | Yes| Yes |
| [sort](#sort)| 5.5 | 1 | Yes | 1 | Yes| Yes |
| [splice](#splice)| 5.5 | 1 | Yes | 1 | Yes| Yes |
| [unshift](#unshift)| 5.5 | 1 | Yes | 1 | Yes| Yes |
| [every](#every) | 9 | Yes | Yes | 1.5 | Yes | Yes |
| [filter](#filter) | 9 | Yes | Yes | 1.5 | Yes | Yes |
| [forEach](#forEach) | 9 | Yes | Yes | 1.5 | Yes | Yes |
| [indexOf](#indexOf) | 9 | Yes | Yes | 1.5 | Yes | Yes |
| [isArray](#isArray) | 9 | 5 | Yes | 4 | 10.5 | 5 |
| [lastIndexOf](#lastIndexOf) | 9 | Yes | Yes | 1.5 | Yes | Yes |
| [map](#map) | 9 | Yes | Yes | 1.5 | Yes | Yes |
| [reduce](#reduce) | 9 | Yes | Yes | 3 | 10.5 | 4 |
| [reduceRight](#reduceRight) | 9 | Yes | Yes | 3 | 10.5 | 4 |
| [some](#some) | 9 | Yes | Yes | 1.5 | Yes | Yes |
| [copyWithin](#copyWithin) | <font color=red>No</font> | 45 | 12 | 32 | 32 | 9 |
| [entries](#entries) | <font color=red>No</font> | 38 | Yes | 28 | 25 | 8 |
| [fill](#fill) | <font color=red>No</font> | 45 | Yes | 31 | Yes | 8 |
| [find](#find) | <font color=red>No</font> | 45 | Yes | 25 | Yes | 8 |
| [findIndex](#findIndex) | <font color=red>No</font> | 45 | Yes | 25 | Yes | 8 |
| [from](#from) | <font color=red>No</font> | 45 | Yes | 32 | Yes | 9 |
| [includes](#includes) | <font color=red>No</font> | 47 | 14 | 43 | 34 | 9 |
| [keys](#keys) | <font color=red>No</font> | 38 | Yes | 28 | 25 | 8 |
| [of](#of) | <font color=red>No</font> | 45 | Yes | 25 | Yes | 9 |
---
<a id="slice"></a>
#### Array.slice()
``slice()`` 方法返回一个从开始到结束（不包括结束）选择的数组的一部分浅拷贝到一个新数组对象。且原始数组不会被修改。
```JavaScript
  Array.slice();
  Array.slice(begin);
  Array.slice(begin,end);
```
``begin``可选。从该索引处开始提取原数组中的元素（从0开始计算）。

如果该参数为负数，则表示从原数组中的倒数第几个元素开始提取，slice(-2)表示提取原数组中的倒数第二个元素到最后一个元素（包含最后一个元素）。

如果省略 begin，则 slice 从索引 0 开始。

``end``可选。提取原数组中索引从 begin 到 end 的所有元素（包含begin，但不包含end）。

如果该参数为负数， 则它表示在原数组中的倒数第几个元素结束抽取。 slice(-2,-1)表示抽取了原数组中的倒数第二个元素到最后一个元素。

如果 end 大于数组长度，slice 也会一直提取到原数组末尾。

```JavaScript
  var array = ['0','1','2','3','4','5']
  console.log(array.slice());//['0','1','2','3','4','5']
  console.log(array.slice(2));//['2','3','4','5'] 正数时索引从0开始计算
  console.log(array.slice(-1));//['5'] 倒数时索引从1开始计算
  console.log(array.slice(3,5));//['3','4']
  console.log(array.slice(-4,-2));//[2'，'3'] 倒数时索引从1开始计算

  var array_slice = array.slice();
  array_slice.push('6');
  console.log(array_slice);//['0','1','2','3','4','5'，'6']
  console.log(array);//['0','1','2','3','4','5']
```

###### 描述
``slice`` 不修改原数组，只会返回一个浅复制了原数组中的元素的一个新数组。原数组的元素会按照下述规则拷贝：
- 如果该元素是个对象引用 （不是实际的对象），slice 会拷贝这个对象引用到新的数组里。两个对象引用都引用了同一个对象。如果被引用的对象发生改变，则新的和原来的数组中的这个元素也会发生改变。
- 对于字符串、数字及布尔值来说（不是 String、Number 或者 Boolean 对象），slice 会拷贝这些值到新的数组里。在别的数组里修改这些字符串或数字或是布尔值，将不会影响另一个数组。

```JavaScript
  var array = [{name:'bcbz',age:'100'},'1','2',true];
  var array_slice = array.slice();
  array_slice[0].name = 'bcyz';
  array_slice[1] = '-1';
  array_slice[3] = false;
  console.info(array);//[{name:'bcyz',age:'100'},'1','2',true];
  console.info(array_slice);//[{name:'bcyz',age:'100'},'-1','2',false];
```
