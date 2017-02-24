- 问题

```
编写一个程序，统计出某个文件内以特定后缀名结尾的文件数，并打印。在控制台中输入：$ node 5.js . js //第一个参数：当前目录；第二个参数：需要查找的文件后缀
```

- 答案
```
/*****5.js*****/
//模块调用声明，fs为文件模块
var fs = require('fs')
//模块调用声明，path为路径模块
var path = require('path')
//异步读取文件目录：目录路径，回调函数[异常，目录下所有文件名称的数组]
fs.readdir(process.argv[2], function (err, list) {
  //是否存在异常
  if (err) {
    console.log(err)
  }
  //filter函数取得每个item
  list.filter(function (file) {
    //extname：返回path路径的file文件的拓展名
    //如果文件拓展名等于输入的参数则取得改数据
    return path.extname(file) === '.' + process.argv[3]
  }).forEach(function (file) { //forEach便利file是filter返回的符合的值
    //输出符合后缀的文件名
    console.log(file)
  })
})
```
