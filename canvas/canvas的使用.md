## Canvas

### canvas简介

​	canvas通过<canvas>标签，创造了一个固定大小的画布，公开一个或者多个渲染上下文，其可以用来绘制和处理展示的内容。

​	在刚创建canvas画布的时候（初始化），画布是空白的，因此我们需要js脚本来找到渲染上下文，由此开始我们的绘制	

```javascript
	...
	let canvas = document.querySelector('canvas')
	let ctx = canvas.getContext() //这就是canvas的上下文对象
	...
```

​	通过canvas的上下文对象，我们可以在画布上绘制自己想要绘制的图形

### 检查支持性

​	替换内容 是为了处理 不支持canvas标签元素的浏览器的，通过检查 `canvas.getContext()`方法是否存在，就可以检查浏览器的支持性。由此，上面一段的代码就变为

```javascript
	...
	let canvas = document.querySelector('canvas')
	let ctx = null
    if(canvas.getContext) {
        ctx = canvas.getContext()
        // ... canvas: draw code		
    }else {
        ... canvas-unsupported: instead draw code
    }
```

### 一个小例子

​	通过canvas，绘制两个有部分重叠在一起的矩形

```html
	<!DOCTYPE html>
    <html>
        <head>
          <meta charset="utf-8">
          <title>Page Title</title>
        </head>
        <body>
          <canvas width="500" height="500"></canvas> 
        </body>
        <script>
          let canvas = document.querySelector('canvas')
          let ctx = null
          if(canvas.getContext) {
            ctx = canvas.getContext('2d')

            ctx.fillStyle = 'rgb(200, 0, 0)'
            ctx.fillRect(10, 10, 55, 50)

            // antoer rect
            ctx.fillStyle = 'rgba(0, 0, 200, .5)'
            ctx.fillRect(30, 30, 55, 50)


          }else {
            alert('当前浏览器不支持canvas，请更换浏览器')
          }
        </script>
    </html>
```

​	成品图：

![1553151947484](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553151947484.png)



### 	