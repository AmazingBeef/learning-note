[TOC]



## Fetch

### 1. H5对于ajax请求提供了方法： Fetch

​	fetch是与es6一同出来的，使用的是Promise对象，因此可以解决异步交互回调地狱问题

### 2. fetch的基本用法

### 	1. 参数：

​			param1：url

​			param2：额外选项

```javascript
	fecth('url', {});
```

### 	2. get请求:

```javascript
// get使用方式
/*
  fetch('http://localhost:2333/?a=1&b=2') // get请求传参
*/
  fetch('http://localhost:2333/')
      .then(res => {
      	return res.text()
      })
      .then(res => {
      	console.log(res)
      })
```

### 	3.post请求

​		当调用post请求的时候，如果后端是nodejs，并且调用的是express模块，必须加上

```javascript
            app.use(express.json())
            app.use(express.urlencoded({extended: true}))	
```

​		这两个模块，才可以读取到fetch post发送过来的参数

​	

```javascript
   const form = new FormData();
                form.append('goudan', '123');
                form.append('xiaoming','123');
                fetch('http://localhost:2333/', {
                    method: 'POST',
                    body: form,
                    headers: {
                        'Content-type': 'application/x-www-form-urlencoded'
                    }
                }).then(res => res.json()).then(data => {	
                    console.log(data)
                })
```

### 	4. 额外选项：

​			credentials: 是否发送cookie  //  include, same-origin, *omit

​			