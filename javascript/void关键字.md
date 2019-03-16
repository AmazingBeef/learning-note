[TOC]

# void 关键字

### 定义变量为void 0；

将变量值定义为 void 0，

```javascript
var a = void 0；
```

等同于将变量定义为undefined。

这种写法的好处在与:

 	1. 防止undefined被重写（undefined不是关键字，在ES5之前，undefined是可以被重写的，于是就导致了一些极端情况下undefined会出现一些差错
 	2. 节省字节（比undefined 节省了3个字节）

类似节省字节的写法还有：

```javascript
//取整
parseInt(a,10); //Before
Math.floor(a); //Before
a>>0; //Before
~~a; //After
a|0; //After
// 位运算符 | 不是按照64位格式操作，而是按照32位整数进行运算，因此会无视小数部分的值。 同时，位运算符特点： 将运算符前后数字 转换位二进制数，对位上只要有一个位1，就位1.

//四舍五入
Math.round(a); //Before
a+.5|0; //After // 位运算符取整

//内置值
undefined; //Before
void 0; //After, 快
0[0]; //After, 略慢

//内置值
Infinity;
1/0;

//布尔值短写法
true; //Before
!0; //After

//布尔值短写法
false; //Before
!1; //After
```



### void后跟表达式

执行表达式的内容，同时返回undefined

```
console.log(void(alert('弹框被打开')));

//reuslt:
弹框： 弹框被打开
undefined
```

### 在a标签中的href链接属性使用void

在href属性中使用void，比如：

```html
<a href="javascript:void(0);" >这个链接不做跳转动作</a>
```

表示这个了超链接不做跳转动作(成为死链接)。

由此，就可以在点击不跳转页面的情况下，执行各种方法。

比如，提交表单：

```html
< a href="javascript:void(document.form.submit();)">提交表单</a>
```

