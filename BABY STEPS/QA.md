- 问题

```
编写一个程序，可以从命令行接收一个或多个数字作为参数，并把这些数字的和输出到控制台相当与编写一个sum(...)函数
```

- 答案
```
/*****2.js*****/
var sum = 0;
//因为process.argv数组的前两个参数永远是路径，所以从2开始
for (var i=2;i<process.argv.length;i++) {
    sum += Number(process.argv[i]);
}

console.log(sum);
```
