- 问题

```
编写一个程序，使用HTTP的GET请求去获得数据，如：$ node 8.js http://www.baidu.com
```

- 答案
```
//需要安装bl
//$ npm install bl
/*****8.js*****/
require('http').get(process.argv[2], function (response) {
  response.pipe(require('bl')(function (err, data) {
    if (err) {
      return console.error(err)
    }
    data = data.toString()
    console.log(data.length)
    console.log(data)
  }))
})
```
