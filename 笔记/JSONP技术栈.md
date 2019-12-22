## 简单的前后端交互

前面学习了这么多，都是在和页面打交道，不管是HTML、CSS、JavaScript，DOM，都没有跑出浏览器，那今天来学习下和后台交互。

当我点击付款按钮时，页面的数值会减小；当我刷新页面时，内容不会改变，该怎么实现呢？

先写一个简单的node.js脚本,让页面能够正常运行

1. 创建一个文件夹里面创建两个文件
2. 新建一个脚本文件
3. 新建一个index.html文件
4. 打开服务器,就可以看到自己的页面了

### 脚本文件

```JS
  var http = require('http')
  var fs = require('fs')
  var url = require('url')
  var port = process.argv[2]
  if(!port){
      console.log('请指定端口号好不啦？\nnode server.js 8888 这样不会吗？')
      process.exit(1)
  }
    
  var server = http.createServer(function(request, response){
  var parsedUrl = url.parse(request.url, true)
  var pathWithQuery = request.url 
  var queryString = ''
  if(pathWithQuery.indexOf('?') >= 0){ queryString = pathWithQuery.substring(pathWithQuery.indexOf('?')) }
  var path = parsedUrl.pathname
  var query = parsedUrl.query
  var method = request.method


  /******** 从这里开始看，上面不要看 ************/

  if(path === '/'){
    var string = fs.readFileSync('./index.html','utf8')
    response.setHeader('Content-Type','text/html;charset=utf-8')
    response.write(string)
    response.end()
  }else if(path === '/css/style.css'){
    var string = fs.readFileSync('./css/style.css','utf8')
    response.setHeader('Content-Type','text/css')
    response.write(string)
    response.end()
  }else if(path === '/js/main.js'){
    var string = fs.readFileSync('./js/main.js','utf8')
    response.setHeader('Content-Type','text/javascript;charset=utf-8')
    response.write(string)
    response.end()
  }else{
    response.statusCode = 404
    response.setHeader('Content-Type','text/html;charset=utf-8')
    response.end('找不到对应的路径,你需要自行修改 index.js')
  }
  
  /******** 代码结束，下面不要看 ************/
})

server.listen(port)
console.log('监听 ' + port + ' 成功\n请用在空中转体720度然后用电饭煲打开 http://localhost:' + port)
```

### HTML 文件

```HTML
<!DOCTYPE html>
<html>
<head>
    <title>首页</title>
</head>
<body>
    <h5>你的余额是<span id="amount">100</span></h5>
    <button id="button">付款</button>
    <script>
        let button = document.getElementById('button')
        let amount = document.getElementById('amount')
        
        button.addEventListener('click',function(){
            amount.textContent = +amount.textContent - 1
            console.log(1)
        })
    </script>
</body>
</html>
```

当我们点付款的时候，100会往下减小，但是当我们刷新页面的时候，又变成了100。

这里我们只是在浏览器上面操作页面内容，数据没有长久的存储在数据库里面，所以当我们刷新页面时，它又回到初始状态，这显然不是我们要的效果。

我们该怎么解决这个问题呢?

### 用占位符替换页面数据

我们在刚才的当前文件夹中新建一个文件，作为我们的数据库，现在我们把100元写在数据库里。

数据库简单的讲就是一个能长久存储数据的地方，文件是数据库最简单的形式。

```
touch db
echo '100' > db
```

`index.html`中的100用一个占位符替代，这个占位符要和页面中其他变量不重复，实际上页面上的数据，前端是不需要知道的，用一个占位符站位即可，发送请求，后端程序员去读数据库里的内容，返回给前端。

```
<span id="amount">&&&amount&&&</span>
```

在脚本中`if(path === '/index.html')`里加一个替换占位符语句。

```
var amount = fs.readFileSync('./index','utf8')        //文件中的数据类型是String
string = string.replace('&&&amount&&&',amount)
```

重启服务器后，刷新页面后我们看到的100是数据库里的数据，当我们点击付款时，变化的是数据库里面的数据，和前端没有关系，但是当我们刷新页面后，依旧回到初始状态，没有保存最新的数据。

我点付款的时候应该发送一个请求告诉服务器，请把数据库里的100变成99，然后刷新页面；我不对页面做操作改变它的数据了，那我点付款的时候，发起一个请求，应该怎么做呢？

可以发请求的标签有`img`、`link`、`script`、`form`表单，当我们点击按钮应该发送`POST`请求，因为是更新数据库内容，所以这里只有`form`表单能发送`POST`请求。

## `form`表单发请求

```
<form action="pay" method="post">
    <input type="submit" value="付款">
</form>    
```

在服务器里面增加一个`/pay`请求路径。

```
if(path === '/pay' && method.toUpperCase() === 'POST'){
    var amount = fs.readFileSync('./db','utf8')
    var newAmount = amount - 1
    fs.writeFileSync('./db',newAmount)
    response.write('success')        //成功后给用户返回
    response.end()
}
```

当我点付款的时候，会看当前页面会跳转到`/pay`路径下的页面，表示成功了。

点击浏览器的返回上一页，刷新下当前页面，之前的100变成了99，无论怎么刷新或者重新打开，数据都是之前的操作过结束后的数据。

这里前端要写的就是`form`表单，后端如果发现是某个路径并且是`POST`请求，就去操作数据库。

这是旧时代的操作，`form`表单一旦提交了都会刷新当前页面，给用户造成了不好的体验。有个程序员想出了用`iframe`解决页面刷新的问题，操作成功后在`iframe`打卡跳转页面。

### iframe 表单刷新页面

```
<form action="pay" method="post" target="success">
    <button id="button">付款</button>
</form>
<iframe name="success" src="about:blank" frameborder="0"></iframe>
```

有个程序员觉得页面中多出一个东西总是怪怪的，绞尽脑汁又想出了动态创建`img`标签的方法

## 动态创建`img`标签发送请求

有洁癖的程序员总是能想出更好的解决方法，接着来看下动态创建`img`标签的发送请求的方法。

脚本中增加`/pay`路径下应该这样写

```
 if(path === '/pay'){
      var string = fs.readFileSync('./db','utf8')
    var newAmount = string - 1
    if(Math.random() > 0.5){
        fs.writeFileSync('./db',newAmount)
        response.setHeader('Content-type','image/jpeg')
        response.statusCode = 200
        response.write(fs.readFileSync('./1.jpeg'))
    }else{
        response.statusCode = 400
        response.write('alert("fail")')
    }
    response.end()
  }
```

因为`img`标签，只能发送`GET`请求，所以这里就不做`method`判断了。

**JS 文件**

```
button.addEventListener('click',function(e){
    let image = document.createElement('img')
    image.src = '/pay'
    img.onload = function(){
        alert('success')
        window.location.reload()
    }
    img.onerror = function(){
        alert('fail')
    }
})
```

`onload`和`onerror`是提示用户成功了还是失败，在`onload`里面加上一个`window.location.reload()`成功后会自动刷新页面。

动态创建`img`标签的方法，必须要返回真实的图片，浏览器才能知道操作成功了，不然`onload`一直不会成功，虽然数据库已经修改成功了，但浏览器只要没接收到图片，就会执行`onerror`，这也是它的局限所在——必须要返回真是图片。

同时**刷新页面会造成浏览器重新渲染**，所以当浏览器接收到响应时，前端应该在页面上自动减`1`，用户并不会知道这中间发生了什么。

## 动态创建`script`标签——SRJ方案

用`a`标签发送请求太浪费资源了，这时又有人想出了用`script`标签发请求，这就是优秀程序员和普通程序员之间的差距啊。

下面来看看是怎么实现的：

```
button.addEventListener('click',function(){
    var script = document.createElement('script')
    script.src = '/pay'
    document.body.appendChild(script)    //必须要将创建出来的Script放在页面中才可以
    script.onload = function(){
        alert('sucess')
    }
})
```

`/pay`路径下的代码

```
if(path === '/pay'){  
      var string = fs.readFileSync('./db','utf8')
    var newAmount = string - 1
    fs.writeFileSync('./db',newAmount)
    response.setHeader('Content-type','application/js')
    response.statusCode = 200
    response.write('alert("success1")')
    response.end()
  }
```

当我点付款时，成功后首先执行脚本里面的`script`，执行完了之后才执行`main.js`内的`onload`。

因为脚本中的`script`先执行，所以`main.js`里面就不需要提示用户了，直接后台给提示内容就可以了。

如下：

```
response.write(`alert("success")
amount.innerText = amount.innerText -1`)    //ES6字符串方法
```

到这里聪明的你应该也发现了一个问题，当我点付款时，不管成功与否都会创建一个`script`，对于程序员来说是无法接受的，所以要用`onload`和`onerror`去监听，不管成功与否都将它删除掉。这里虽然删掉了但它还是在内存中。

```
script.onload = function(e){
    e.currentTarget.remove()
}
script.onerror = function(e){
    e.currentTarget.remove()
}
```

动态创建`script`方法发送请求叫做——**SRJ方案（全称 Server rendered javascript）**，在 ajax 出来以前，无刷新局部更新页面内容的最好的方案。

## 请求另一个网站的`script`

在页面中引入一个`script`时，一定要在当前域名吗？

NO！！！我们在页面中引入的各种库，不都是引入别人的网站的`script`嘛

那这样的话，是不是可以操作别人网站的`/pay`，所以`GET`请求太不安全，太容易伪造了，所以大部分的`/pay`都用`POST`请求去做。

```
PORT=8002 node index.js 可以开多个端口
```

`SRJ`方案前后端耦合太紧密了，需要后端对页面了解太清楚。

其实前端提供一个`xxx()` API就可以了。

```
response.write(`
xxx.call(undefined,'success')
`)
```

前端提供 API 的方法，其实解耦还没有解的很干净，我们在设置`script`的`src`时可以直接设置请求参数，脚本只需要取这个参数就可以了，至于具体叫什么名字不重要

```
script.src = 'http://baidu.com:8002/pay?callbackName=xxx'
response.write(`
    ${query.callbackName}.call(undefined,'success')
`)
```

到这里已经是很好的方案了，但是有一个问题是，调用函数传递的参数，前端怎么知道呢？如果不确定，到时候出了问题就要各自扯皮了，这时候`JSON`应运而出。

## JSONP方案

`JSONP`用`JSON`的格式进行参数传递，解决了两个网站之间的交流。至于为什么叫`JSONP`，应该是大括号左边的叫做`左padding`，右边的叫做`右padding`，连接起来就叫做`JSONP`。

```
${query.callbackName}.call(undefined,{
    "success": true
    "left": ${newAmount}
})
```

### 用文字叙述 JSONP

请求方:`qq.com`的前端程序员(浏览器)
响应方:`baidu.com`的后端程序员(服务器)

1. 请求方创建`script` ,`src`指向相应方同事传一个查询参数 `?callbackName=xxx`
2. 响应方根据查询参数`callbackName`,构造形如`xxx.call(undefined,'你要的数据')`这样的响应
3. 浏览器接收到响应，`xxx.call(undefined,'你要的数据')`
4. 那么请求方就知道了它要的数据

这就是`JSONP`

### 约定:

1. callbackName -> callback
2. xxx -> 随机数

按照约定写一下

```
button.addEventListener('click',funcion(e){
    let script = document.createElement('script')
    let functionName = parseInt(Math.random()*1000000)        //这个函数名是随机数
    window[functionName] = function(result){    //result是服务器返回的结果
        if(result === 'success'){
            amount.innerText = amount.innerText - 1
        }
    }

    script.src = 'http://baidu.com:8002?callback=' + functionName    //写在参数里面
    document.body.appendChild(script)
    script.onload = function(e){
        e.currentTarget.remove()
        delete window[functionName]    //如果成功了要干掉这个函数
    }
    script.onerror = function(e){
        alert("false")
        e.currentTarget.remove()
        delete window[functionName]    //如果失败了也要干掉这个函数

    }
})
```

## jQuery实现

用jQuery就能非常方便的使用

```
button.addEventListener('click',function(){
    $.ajax({
        url: "http://baidu.com:8002/pay"
        dataType: "JSONP"
        success:function(response){
            console.log(response)
        }
    })
})
```

## `JSONP`为什么不支持`POST`请求

1. 因为`JSONP`是通过动态创建`script`实现的
2. 动态创建`script`只有GET请求没有`POST`请求