
- 问题

```
编写一个程序，使用异步文件函数读取文件并打印输出文件内的行数，在控制台中输入需要读取的文件，如:$ node 4.js 4.js
```

- 答案
```
/*****4.js*****/
//模块调用声明，fs为文件模块
var fs = require("fs");
//同步读取文件：文件路径，编码格式(可选)，回调函数[异常，文件内容]
fs.readFile(process.argv[2],'utf-8',function(err,data) {
   //如果出现异常，则打印输出异常并抛出
   if (err) {
       console.log(err);
       throw err;
   }
   //打印文件内容
   console.log(data)
   //如果文件内容不等于空
   if (data != undefined) {
      //通过换行符切分内容
       var segments = data.split('\n');
       //输出内容的行数
       console.log(segments.length-1);
   }
    
});
```
