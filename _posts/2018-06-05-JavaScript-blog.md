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

>     [element0, element1, ..., elementN]
>     new Array(element0, element1[, ...[, elementN]])
>     new Array(arrayLength)

__arrayLength:__ 支持一个范围在 0 到 232-1 之间的整数。

##  JavaScript 内置对象（Array）
* [属性](#property)
  * [Array.length](#length)
  * [Array.prototype](#prototype)

---

|  | Chrome | Edge | Firefox | IE | Opera | Safari |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| [length](#length)| yes| yes | 1 | yes | yes| yes |
| [prototype](#prototype) | yes| yes | 1 | yes | yes| yes |

---
### 属性
<a id="property"></a>
> 数据属性有四个描述其行为的特性

|  | 默认值 | 描述 |
| :-: | :-: | :-: |
| Configurable | true |  |
| Enumerable | false |  |
| writable | false |  |


#### Array.length
<a id="length"></a>
>``length``属性的属性特征

| 特征 | 默认值 |
| :-: | :-: | :-: |
| Configurable | false |
| Enumerable | false |
| writable | true |

``length`` 属性的值是一个 0 到 2^32-1 的整数。

>     //Uncaught RangeError: Invalid array length;
>     var array = new Array(4294967296);//2^32 = 4294967296

可以通过设置 ``length`` 属性的值来截取数组，或扩展数组。但是， ``length``  属性不一定表示数组中定义值的个数。

>     var array = ['0','1','2'];
>     array.length = 2;
>     console.log(array);//['0','1']
>
>     array.length = 5;
>     console.log(array);//['0','1',undefined,undefined,undefined]
>
>     array.length = 1;//['0']
>     array[5] = '5';
>     console.log(array);//['0',undefined,undefined,undefined,undefined,'5']

#### Array.prototype
<a id="prototype"></a>
>``prototype``属性的属性特征

| 特征 | 默认值 |
| :-: | :-: | :-: |
| Configurable | false |
| Enumerable | false |
| writable | false |

``Array.prototype`` 属性表示 ``Array`` 构造函数的原型，并允许您向所有Array对象添加新的属性和方法。

>     /*
>       如果JavaScript本身不提供 first() 方法，
>       添加一个返回数组的第一个元素的新方法。
>     */
>     if(!Array.prototype.first) {
>         Array.prototype.first = function() {
>             return this[0];
>         }
>     }
>     var array = ['0','1','2'];
>     console.log(array.first());//0

``Array.prototype.constructor``  
所有的数组实例都继承了这个属性，返回对创建此对象的数组函数的引用。
