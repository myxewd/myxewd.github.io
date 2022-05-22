###### 打开Json文档

在你使用Jsql对Json文件进行操作前，需要先打开指定的Json文档，命令如下

```sql
open "{jsonpath}" -charset
```

在这个语句中，`{jsonpath}`代表你的Json文件在你电脑硬盘上的位置，如`C:\example.json`，而charset代表json文件的编码类型，目前支持两种编码

1. UTF8
2. GB2312

在Jsql终端输入以上命令，若无报错信息，则代表Json文件已经成功打开