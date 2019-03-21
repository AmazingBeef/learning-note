[TOC]

## canvas绘制基本图形

### canvas绘制矩形

​	canvas 绘制矩形，是通过上下文对象的rect方法来指定绘制矩形的起点以及长宽， 如`ctx.rect(0, 0, 100, 100)`则为以(0,0), 为起点，绘制长宽为100, 100的矩形

#### 绘制矩形-例子:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body onload="draw()">
  <canvas></canvas>
</body>
<script>
  function draw() {
    let canvas = document.querySelector('canvas')
    let ctx = canvas.getContext('2d')
    // method 1
    ctx.rect(50, 50, 50, 50)
    ctx.fillStyle = 'hotpink'
    ctx.fill()
    ctx.rect(100, 100, 50, 50)
    ctx.strokeStyle = 'skyblue'
    ctx.stroke()
  }
</script>
</html>
```

​	这样就绘制了两个矩形，但是由于绘画时绘制路径没有停下，又或者使用的不是复合方法来绘制，导致了以边框方法绘制的矩形的边框效果也会影响到填充矩形元素。

​	![1553153079179](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553153079179.png)

##### 解决方法1:

​	使用复合函数`fillRect() 和  strokeRect()`来分开绘制可以避免这个问	

```javascript
	...
    ctx.fillStyle = 'hotpink'
    ctx.fillRect(50, 50, 50, 50)
    ctx.strokeStyle = 'skyblue'
    ctx.strokeRect(100, 100, 50, 50)
    ...
```

##### 解决方法2:

​	控制绘制路径来避免这个问题:

​	绘制路径是canvas绘制路径的基本元素。路径就是通过不同颜色、宽度的线段或者曲线相连城的不同点的集合。

​	用到的函数有

​	beginPath(): 新建一条路径，生成之后，图形绘制命令会被指向到路径上生成路径

​	closePath(): 闭合路径之后，图形绘制命令又被指向到上下文对象中(注意，对于闭合的路径，closePath函数式不需要的，这个函数会绘制一条由当前点到开始点的直线来闭合图形)

​	stroke(): 通过线条来绘制轮廓

​	fil(): 通过填充路径的内容来生成实心的图形（注意，如果路径中的点没有闭合，canvas会自动将将缺口自动闭合)	

```javascript
  	...
    ctx.beginPath()
    ctx.rect(50, 50, 50, 50)
    ctx.fillStyle = 'hotpink'
    ctx.fill()
    ctx.closePath()
    
    ctx.beginPath()
    ctx.rect(100, 100, 50, 50)
    ctx.strokeStyle = 'skyblue'
    ctx.stroke()
    ctx.closePath()
    ...
```

​	由此 就可以绘制出互不干扰的两个图形

​	![1553154439761](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553154439761.png)	

### 绘制三角形

​	绘制三角形，就是在路径中创建三个点，并未他们添加轮廓	

```javascript
		...
		let canvas = document.querySelector('canvas')
		let ctx = canvas.getContext('2d')
		ctx.beginPath()
		// 指定开始的点
		ctx.moveTo(75, 50)
		ctx.lineTo(100, 75)
		ctx.lineTo(100, 25)
		// 如果调用fill方法无需添加以下 （两种方式闭合）
		// ctx.lineTo(75, 50) // 手动闭合
		// ctx.closePath() //关闭路径来自动闭合
		// ctx.stroke()
		ctx.fill()
```

### 绘制圆形（圆弧)

