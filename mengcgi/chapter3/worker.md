MengCgi用命令行方式启动Worker程序，参数如下

| 位置 | 解释                                                      |
| ---- | --------------------------------------------------------- |
| 0    | 请求方式（GET/POST）                                      |
| 1    | 链接变量（Query String）的变量地址                        |
| 2    | 链接变量长度                                              |
| 3    | Post提交的数据的变量地址。默认为0                         |
| 4    | Post提交的数据长度.默认为0                                |
| 5    | Cookie数据变量地址                                        |
| 6    | Cookie数据长度                                            |
| 7    | 要求的服务器变量变量地址                                  |
| 8    | 服务器变量Json长度（变量值经过Base64编码）                |
| 9    | 客户端IP（1.1.1.1）                                       |
| 10   | MengCgi内部句柄，在处理完成后请传递给 Worker_Callback方法 |
| 11   | MengCgi Pid 用于OpenProcess                               |
| 12   | Worker_Callback方法地址。用于远程Call                     |

##### GMT时间示例

Sun, 01 May 2022 13:38:56 GMT

### _Call参数解释

| 参数名称       | 用途解释                                                     | 示例值 |
| -------------- | ------------------------------------------------------------ | ------ |
| Proc_handle    | MengCgi进程句柄                                              | 100    |
| addr           | Worker_Callback方法地址                                      | /      |
| mcgi_output    | 返回的Document数据，需要事先在MengCgi进程中创建远程内存后传递内存地址整数 | /      |
| mcgi_extradata | Header、Cookies等数据，内存地址                              | /      |

##### ExtraData示例

```Json
{
    "headers": [
        {
            "fieldname": "header_field1",
            "fieldvalue": "a1"
        },
        {
            "fieldname": "header_field2",
            "fieldvalue": "b2"
        }
    ],
    "cookies": [
        {
            "cookiename": "cexample",
            "value": "test",
            "expire": "Sun, 01 May 2022 13:38:56 GMT",
            "wwwpath": "/admin",
            "domain": "xyjerry.com"
        }
    ],
    "status": "200 OK",
    "thread_handle": 12345
}
```

具体见 Demo 例程

**请一定先充分理解Demo中的每一行代码的意义，再进行开发。否则可能造成内存溢出，程序崩溃等后果**