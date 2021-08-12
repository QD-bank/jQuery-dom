# jQuery基本功能

虽然jQuery已经是一门过时的语言，但是学习jQuery对之后写代码和封装库很有帮助，为以后学习Vue / React起到一个过度作用，因为jQuery也蕴含了非常多的变成套路

## 目录

> 1.获取元素
> 2.链式操作
> 3.创建元素
> 4.移动元素
> 5.修改元素的属性

## 获取元素

选择表达式可以是CSS选择器————代码：

```javascript

$(document) //选择整个文档对象

$('#myId') //选择ID为myId的网页元素

$('div.myClass') // 选择class为myClass的div元素

$('input[name=first]') // 选择name属性等于first的input元素

```

或者是jQuery特有的表达式

```javascript

$('a:first') //选择网页中第一个a元素

$('tr:odd') //选择表格的奇数行

$('#myForm :input') // 选择表单中的input元素

$('div:visible') //选择可见的div元素

$('div:gt(2)') // 选择所有的div元素，除了前三个

$('div:animated') // 选择当前处于动画状态的div元素

```

## 链式操作

链式操作是jQuery的设计想之一，最终选中网页元素以后，可以对它进行一系列操作，并且所有操作可以连接在一起，以链条的形式写出来

代码：

```javascript

$('div').find('h3').eq(2).html('hello')

//分解开来，就是

$('div') //找到div元素

　　　.find('h3') //选择其中的h3元素

　　　.eq(2) //选择第3个h3元素

　　　.html('Hello'); //将它的内容改为Hello

```
通过链式操作，可以使用简洁的代码完成工作，它的原理在于使用返回的api操作对应的元素

jQuery还提供了.end()方法，是的结果集可以后退一步

代码：

```javascript

　$('div')

　　　.find('h3')

　　　.eq(2)

　　　.html('Hello')

　　　.end() //退回到选中所有的h3元素的那一步

　　　.eq(0) //选中第一个h3元素

　　　.html('World'); //将它的内容改为World

```

## 创建元素

```javascript

$('<ul>ul element</ul>')//创建ul元素

$('<li class="new">new list item</li>')//创建class为new的li元素

$('ul').append('<li>list item</li>')//将li元素添加为ul元素的子元素

```

## 移动元素

jQuery提供了两组方法两操作元素在网页中的位置移动：

* 直接移动该元素

* 移动其它元素

方法一：使用.insertAfter(),把元素移动到另一个元素后面：

```javascript

　$('div').insertAfter($('p'));

```

方法二：使用.after()，把元素移动到另一个元素前面：

```javascript

　　$('p').after($('div'));

```

两种方法效果看上去是一样的，但它们返回的元素不一样，.insertAfter()返回div元素，.after()返回p元素

使用这种模式的操作方法，一共有四队：

```javascript

.insertAfter()和.after()：在现存元素的外部，从后面插入元素

.insertBefore()和.before()：在现存元素的外部，从前面插入元素

.appendTo()和.append()：在现存元素的内部，从后面插入元素

.prependTo()和.prepend()：在现存元素的内部，从前面插入元素

```

## 修改元素属性

jQuery 支持使用同一个方法，来完成取值和赋值的操作。是取值还是赋值，由参数来控制，不传参数则表示取值，传入参数则表示赋值。

常用的取值和赋值方法如下：

```javascript

$('#p').attr('class')//获取id为p的元素的class属性

$('#p').attr('class','red')//如果有第二个参数，就是给p元素的class加一个red属性

//这是一个很有意思的例子。因为这是jQuery的一个巧妙的设计。这是一个getter/setter模式。就是指这个函数，既可以读也可以写。

$('#p').addClass('blue') 给id为p的元素增加一个blue的class属性

$('#p').removeClass('yellow') 删除id为p的元素的yellow的class属性

```