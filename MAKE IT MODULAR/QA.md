- 问题

```
编写一个程序，统计出某个文件内以特定后缀名结尾的文件数，并打印。在控制台中输入：$ node 5.js . js //第一个参数：当前目录；第二个参数：需要查找的文件后缀
ps:这个是要使用两个文件来实现
```

- 答案
```
/*****6.js*****/
//require()：加载模块函数
//第二个()是model里的函数参数
require('./module_6')(process.argv[2], process.argv[3], function (error, list) {
  //判断是否有异常
  if (error) {
    return console.log(error)
  }
  
  //遍历list并打印输出entry数据
  list.forEach(function (entry) {
    console.log(entry)
  })
})

/*****model_6.js*****/
//模块调用声明，fs为文件模块
var fs = require('fs')
//模块调用声明，path为路径模块
var path = require('path')
//定义模块为一个类。也就是初始化时要带这三个参数，这也就是6.js中的第二个括号
module.exports = function (directory, filter, callback) {
  //下面的代码和5.js相似
  fs.readdir(directory, function (error, list) {
    if (error) {
      return callback(error)
    }

    list = list.filter(function(item) {
       return path.extname(item) === '.' + filter 
    })
    
    //使用回调函数用来输出
    callback(null,list)
  })
}
```
