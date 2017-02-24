- 问题

```
编写一个程序，使用HTTP的GET请求去获得命令行每个参数中的数据，如：$ node 9.js http://www.baidu.com http://www.baidu.com http://www.baidu.com
```

- 答案
```
/*****9.js*****/
var http = require('http')
//保存数据的数组
var feed = []
//标记数
var count = 0
//从参数数组中取出从下标为2到结束的数组
//如：[2,3,1,5,6].slice(2) ==> [1,5,6]
var url = process.argv.slice(2)

function allDone () {
    //每次成功的请求count都会+1
    //因为这个函数是在get请求后触发的，所以feed的长度早都增长为forEach的次数
    //当count===feed.length时，说明每个请求都已经完成
    count += 1
    if (count === feed.length) {
      feed.forEach(function (value) {
         console.log(value)
       })
     }
}

//对参数中的url进行遍历
url.forEach(function (value, index) {
  feed[index] = ''
  //使用get请求
  http.get(value, function (response) {
    response.setEncoding('utf8')
    response.on('data', function (data) {
      feed[index] += data
    })
    //数据接收完毕
    response.on('end', allDone)
  })
})
```
