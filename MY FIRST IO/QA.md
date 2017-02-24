- 问题

```
编写一个程序，使用同步文件函数读取文件并打印输出文件内的行数，在控制台中输入需要读取的文件，如:$ node 3.js 3.js
```

- 答案
```
/*****3.js*****/
//模块调用声明，fs为文件模块
var fs = require("fs");
//同步读取文件：文件路径，编码格式(可选)
var contents = fs.readFileSync(process.argv[2]);
if (contents != undefined) {
    //计算文件内一共有多少行
    var lines = contents.toString().split('\n').length-1;
    console.log(lines);
}
```
