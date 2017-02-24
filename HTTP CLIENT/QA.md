- 问题

```
编写一个程序，使用HTTP的GET请求去获得数据，如：$ node 7.js http://www.baidu.com
```

- 答案
```
/*****7.js*****/
//使用http的get请求：命令行的参数，请求函数
require('http').get(process.argv[2], processResponse)

function processResponse (res) {
    //设置编码
    res.setEncoding('utf8')
    //取得数据并打印
    res.on('data', console.log)
    //取得错误并打印
    res.on('error', console.error)
}
```
