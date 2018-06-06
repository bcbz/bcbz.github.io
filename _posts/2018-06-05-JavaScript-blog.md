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

##  JavaScript 内置对象（Array）
### 描述
#### 创建数组
```JavaScript
/*
  数组字面量表示法
  [element0, element1, ..., elementN]
*/
var array = ['1','2','3'];
var array = [];
/*
  错误实例
  下列两种方式由于浏览器的实现方式不同会导致出现不同的项
*/
var array = ['1','2',];//IE8及之前value包含3项每项的值为1,2,null；在其他浏览器中value包含两项1,2
var array = [,,,];
/*
  Array构造函数创建
  new Array(element0, element1[, ...[, elementN]])
  new Array(arrayLength)
*/
var array = new Array('1','2','3');
var array = new Array(20);
```
``arrayLength`` 支持一个范围在 0 到 232-1 之间的整数。
### 目录
* [属性](#property)
  * [Array.length](#length)
  * [Array.prototype](#prototype)
* [方法](#method)
  * [Array.slice()](#slice)
  * [Array.toLocaleString()](#toLocaleString)
  * [Array.toString()](#toString)
  * [Array.concat()](#concat)
  * [Array.join()](#join)
  * [Array.pop()](#pop)
  * [Array.push()](#push)
  * [Array.reverse()](#reverse)
  * [Array.shift()](#shift)
  * [Array.sort()](#sort)
  * [Array.splice()](#splice)
  * [Array.unshift()](#unshift)
  * [Array.every()](#every)
  * [Array.filter()](#filter)
  * [Array.forEach()](#forEach)
  * [Array.indexOf()](#indexOf)
  * [Array.isArray()](#isArray)
  * [Array.lastIndexOf()](#lastIndexOf)
  * [Array.map()](#map)
  * [Array.reduce()](#reduce)
  * [Array.reduceRight()](#reduceRight)
  * [Array.some()](#some)

---
| 兼容性 | IE | Chrome | Edge | Firefox | Opera | Safari |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| [length](#length) | Yes | Yes | Yes | 1 | Yes | Yes |
| [prototype](#prototype) | Yes | Yes | Yes | 1 | Yes | Yes |
| [slice](#slice) | Yes | Yes | Yes | 1 | Yes | Yes |
| [toLocaleString](#toLocaleString) | Yes | Yes | Yes | 1 | Yes| Yes |
| [toString](#toString) | Yes | Yes | Yes | 1 | Yes| Yes |
| [concat](#concat) | 5.5 | 1 | Yes | 1 | Yes| Yes |
| [join](#join) | 5.5 | 1 | Yes | 1 | Yes| Yes |
| [pop](#pop) | 5.5 | 1 | Yes | 1 | Yes| Yes |
| [push](#push) | 5.5 | 1 | Yes | 1 | Yes| Yes |
| [reverse](#reverse) | 5.5 | 1 | Yes | 1 | Yes| Yes |
| [shift](#shift) | 5.5 | 1 | Yes | 1 | Yes| Yes |
| [sort](#sort) | 5.5 | 1 | Yes | 1 | Yes| Yes |
| [splice](#splice) | 5.5 | 1 | Yes | 1 | Yes| Yes |
| [unshift](#unshift) | 5.5 | 1 | Yes | 1 | Yes| Yes |
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
| [copyWithin](#copyWithin) | ``No`` | 45 | 12 | 32 | 32 | 9 |
| [entries](#entries) | ``No`` | 38 | Yes | 28 | 25 | 8 |
| [fill](#fill) | ``No`` | 45 | Yes | 31 | Yes | 8 |
| [find](#find) | ``No`` | 45 | Yes | 25 | Yes | 8 |
| [findIndex](#findIndex) | ``No`` | 45 | Yes | 25 | Yes | 8 |
| [from](#from) | ``No`` | 45 | Yes | 32 | Yes | 9 |
| [includes](#includes) | ``No`` | 47 | 14 | 43 | 34 | 9 |
| [keys](#keys) | ``No`` | 38 | Yes | 28 | 25 | 8 |
| [of](#of) | ``No`` | 45 | Yes | 25 | Yes | 9 |



---
<a id="property"></a>
### 属性
- 数据属性

| 特性 | 默认值（在创建新属性的时） | 描述 |
| :-: | :-: | :-: |
| Configurable | true | 表示能否通过 delete 删除属性从而定义属性，能否修改属性的特性，或者能否把属性修改为访问器属性。 |
| Enumerable | true | 表示能否通过 for-in 循环属性。 |
| writable | true | 表示能否修改属性的值。 |
| value | undefined | 包含这个属性的数据值。 |

- 访问器属性

| 特性 | 默认值 | 描述 |
| :-: | :-: | :-: |
| Configurable | true（在对象上直接定义的属性） | 表示能否通过 delete 删除属性从而定义属性，能否修改属性的特性，或者能否把属性修改为数据属性。 |
| Enumerable | true（在对象上直接定义的属性） | 表示能否通过 for-in 循环属性。 |
| Get | undefined | 在读取属性时调用的函数。 |
| Set | undefined | 在写入属性时调用的函数。 |

>[JavaScript属性类型专题详情][attributeType]

<a id="length"></a>
#### Array.length

- ``length``属性的属性特性

| 特性 | 默认值 |
| :-: | :-: |
| Configurable | false |
| Enumerable | false |
| writable | true |

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
| :-: | :-: |
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

<a id="slice"></a>
#### Array.slice()
- ``slice()`` 方法返回一个从开始到结束（不包括结束）选择的数组的一部分浅拷贝到一个新数组对象。且原始数组不会被修改。
```JavaScript
  Array.slice();
  Array.slice(begin);
  Array.slice(begin,end);
```
  ``begin``可选。从该索引处开始提取原数组中的元素（从0开始计算）。

  - 如果该参数为负数，则表示从原数组中的倒数第几个元素开始提取，slice(-2)表示提取原数组中的倒数第二个元素到最后一个元素（包含最后一个元素）。

  - 如果省略 begin，则 slice 从索引 0 开始。

  ``end``可选。提取原数组中索引从 begin 到 end 的所有元素（包含begin，但不包含end）。

  - 如果该参数为负数， 则它表示在原数组中的倒数第几个元素结束抽取。 slice(-2,-1)表示抽取了原数组中的倒数第二个元素到最后一个元素。

  - 如果 end 大于数组长度，slice 也会一直提取到原数组末尾。

```JavaScript
  var array = ['0','1','2','3','4','5']
  console.log(array.slice());//['0','1','2','3','4','5']
  console.log(array.slice(2));//['2','3','4','5'] 正数时索引从0开始计算
  console.log(array.slice(-1));//['5'] 倒数时索引从1开始计算
  console.log(array.slice(3,5));//['3','4']
  console.log(array.slice(-4,-2));//[2'，'3'] 倒数时索引从1开始计算

  var array_slice = array.slice();
  array_slice.push('6');
  console.log(array_slice);//['0','1','2','3','4','5','6']
  console.log(array);//['0','1','2','3','4','5']
```

- ``slice`` 不修改原数组，只会返回一个浅复制了原数组中的元素的一个新数组。原数组的元素会按照下述规则拷贝：
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
<a id="toLocaleString"></a>
#### Array.toLocaleString()
 返回一个字符串表示数组中的元素。数组中的元素将使用各自的 toLocaleString 方法转成字符串，这些字符串将使用一个特定语言环境的字符串（例如一个逗号 ","）隔开。

<a id="toString"></a>
#### Array.toString()
返回一个字符串，表示指定的数组及其元素。

<a id="concat"></a>
#### Array.concat()
创建一个新的数组，它由被调用的对象中的元素组成，每个参数的顺序依次是该参数的元素（如果参数是数组）或参数本身（如果参数不是数组）。它不会递归到嵌套数组参数中。
- 对象引用（而不是实际对象）：__concat__ 将对象引用复制到新数组中。 原始数组和新数组都引用相同的对象。 也就是说，如果引用的对象被修改，则更改对于新数组和原始数组都是可见的。 这包括也是数组的数组参数的元素。
- 数据类型如字符串，数字和布尔（不是String，Number 和 Boolean 对象）：concat将字符串和数字的值复制到新数组中。

```JavaScript
/*
  语法
  var new_array = old_array.concat(value1[, value2[, ...[, valueN]]]);
*/

var array1 = ['1','2','3'];
var array2 = ['4'];
var array3 = ['5'];
var array4 = [['6']];
var array_concat1 = array1.concat('3','4');
console.log(array_concat1);//['1','2','3','3','4'];

var array_concat2 = array1.concat('3',array2);
console.log(array_concat2);//['1','2','3','3','4'];

var array_concat3 = array1.concat(array2,array3);
console.log(array_concat3);//['1','2','3','4','5'];

//对于引用类型来说修改原数据同时会体现在新数组上。修改新数组也会反应在原数据上
var array_concat4 = array1.concat(array4);
console.log(array_concat4);//['1','2','3',['6']];
array4[0].push('0');
console.log(array_concat4);//['1','2','3',['6','0']];
array_concat4[3].push('2');
console.log(array_concat4);//[['6','0','2']];
 ```

<a id="join"></a>
#### Array.join()
将一个数组（或一个类数组对象）的所有元素连接成一个字符串并返回这个字符串。
```JavaScript
/*
  var str = Array.join(separator);
  separator 分隔符
  返回值为字符串类型
*/
var array = ['1','2','3'];
console.log(array.join());//1,2,3 参数为空时默认','分隔
console.log(array.join(''));//123
console.log(array.join('+'));//1+2+3
```

<a id="pop"></a>
#### Array.pop()
从数组中删除最后一个元素，并返回该元素的值。此方法更改数组的长度。
```JavaScript
var array = ['1'];
var str1 = array.pop();
console.log(array);//[]
console.log(array.length);//0
console.log(str1);//'1'

var str2 = array.pop();
console.log(array);//[]
console.log(str2);//undefined
```

<a id="push"></a>
#### Array.push()
将一个或多个元素添加到数组的末尾，并返回新数组的长度。
```JavaScript
/*
  Array.push(element1, ..., elementN)
*/
var array = ['1','2','3'];
var array_push = array.push('3');
console.log(array);//['1','2','3','3']
console.log(array_push);//4
```
<a id="reverse"></a>
#### Array.reverse()
方法颠倒数组中元素的位置，并返回该数组的引用。如果只是反转数组原来的顺序，``Array.reverse()``效率更高。
```JavaScript
var array = ['1','2','3','4'];
array.reverse();
console.log(array);//['4','3','2','1']
```

<a id="shift"></a>
#### Array.shift()
从数组中删除第一个元素，并返回该元素的值。此方法更改数组的长度。
```JavaScript
var array1 = ['1','2','3'];
var str1 = array1.shift();
console.log(array1);//['2','3']
console.log(array1.length);//2
console.log(str1);//'1'

var array2 = [];
var str2 = array2.pop();
console.log(array2);//[]
console.log(str2);//undefined
```

<a id="sort"></a>
#### Array.sort()
对数组的元素进行排序，并返回数组。
```JavaScript
arr.sort()
arr.sort(compareFunction)
```
``compareFunction``可选用来指定按某种顺序进行排列的函数，如果省略，元素按照转换为的字符串的各个字符的Unicode位点进行排序。

```JavaScript
var array1 = ['4','1','2','3'];
var array_sort1 = array1.sort();
var array2 = ['watermelon','Appale','appale','Banana'];
var array_sort2 = array2.sort();
console.log(array1);//['1','2','3','4'];
console.log(array_sort1);//['1','2','3','4'];
console.log(array2);//['Appale','Banana','appale','watermelon']
console.log(array_sort2);//['Appale','Banana','appale','watermelon']
```
- 如果没有指明 compareFunction ，那么元素会按照转换为的字符串的诸个字符的Unicode位点进行排序。例如 "Banana" 会被排列到 "cherry" 之前。当数字按由小到大排序时，9 出现在 80 之前，但因为（没有指明 compareFunction），比较的数字会先被转换为字符串，所以在Unicode顺序上 "80" 要比 "9" 要靠前。

- 如果指明了 compareFunction ，那么数组会按照调用该函数的返回值排序。即 a 和 b 是两个将要被比较的元素：
  - 如果 compareFunction(a, b) 小于 0 ， a 会被排列到 b 之前。
  - 如果 compareFunction(a, b) 等于 0 ， a 和 b 的相对位置不变。
  - 如果 compareFunction(a, b) 大于 0 ， b 会被排列到 a 之前。
  - compareFunction(a, b) 必须总是对相同的输入返回相同的比较结果，否则排序的结果将是不确定的。

```JavaScript
/*
  自定义排序规则；按年龄排序
*/
var array = [
  {name:'bcbz',age:'26'},
  {name:'bcyz',age:'24'},
  {name:'bc',age:'100'}
];

function compare(a,b){
  return a.age-b.age;
}

array.sort(compare);
console.log(array);
/*
  var array = [
    {name:'bcyz',age:'24'},
    {name:'bcbz',age:'26'},
    {name:'bc',age:'100'}
  ];
*/
```
<a id="splice"></a>
#### Array.splice()

<a id="unshift"></a>
#### Array.unshift()
将一个或多个元素添加到数组的开头，并返回新数组的长度。
```JavaScript
var array = ['1','2','3'];
var array_unshift = array.unshift('4','5');
console.log(array);//['4','5','1','2','3']
console.log(array_unshift);//5

array.unshift(['2','3']);
console.log(array);//[['2','3'],'4','5','1','2','3']
```
> IE7及更早的版本对 JavaScript 的实现中存在一个偏差，其 unshift()方法总是返回 undefined 而不是数组的新长度。IE8在非兼容模式下回返回正确的长度值。

<a id="every"></a>
#### Array.every()

<a id="filter"></a>
#### Array.filter()

<a id="forEach"></a>
#### Array.forEach()

<a id="indexOf"></a>
#### Array.indexOf()

<a id="isArray"></a>
#### Array.isArray()

<a id="lastIndexOf"></a>
#### Array.lastIndexOf()

<a id="map"></a>
#### Array.map()

<a id="reduce"></a>
#### Array.recude()

<a id="reduceRight"></a>
#### Array.reduceRight()

<a id="some"></a>
#### Array.some()


[attributeType]:https://bcbz.github.io/2018/06/05/JavaScript-blog/#slice
