### 环境变量

URL = 返回服务器地址   
PATH_INFO = 客户端提供的路径信息   
APPL_PHYSICAL_PATH = 与应用程序元数据库路径相应的物理路径  		   
PATH_TRANSLATED = 通过由虚拟至物理的映射后得到的路径   
SCRIPT_NAME = 执行脚本的名称   
QUERY_STRING = 查询字符串內容   
HTTP_REFERER = 请求的字符串內容   
SERVER_PORT = 接受请求的服务器端口号   
REMOTE_ADDR = 发出请求的远程主机的IP地址   
REMOTE_HOST = 发出请求的远程主机名称   
LOCAL_ADDR = 返回接受请求的服务器地址   
HTTP_HOST = 返回服务器地址  		   
SERVER_NAME = 服务器的主机名、DNS地址或IP地址   
REQUEST_METHOD = 提出请求的方法比如GET、HEAD、POST等等   
SERVER_PORT_SECURE = 如果接受请求的服务器端口为安全端口时，则为1，否则为0   
SERVER_PROTOCOL = 服务器使用的协议的名称和版本   
SERVER_SOFTWARE = 应答请求并运行网关的服务器软件的名称和版本   
ALL_HTTP = 客户端发送的所有HTTP标头，前缀HTTP_   
ALL_RAW = 客户端发送的所有HTTP标头,其结果和客户端发送时一样，没有前缀HTTP_ 		   
APPL_MD_PATH = 应用程序的元数据库路径   
CONTENT_LENGTH = 客户端发出內容的长度   
HTTPS = 如果请求穿过安全通道（SSL），则返回ON如果请求来自非安全通道，则返回OFF   
INSTANCE_ID = IIS实例的ID号   
INSTANCE_META_PATH = 响应请求的IIS实例的元数据库路径   
HTTP_ACCEPT_ENCODING = 返回內容如：GZIP,DEFLATE   
HTTP_ACCEPT_LANGUAGE = 返回內容如：EN-US   
HTTP_CONNECTION = 返回內容：KEEP-ALIVE   
HTTP_COOKIE = 返回内容：Cookie的值   
HTTP_USER_AGENT = 取出用户浏览器类型 返回內容：MOZILLA/4.0(COMPATIBLE;MSIE6.0;WINDOWSNT5.1;SV1) 		   
AUTH_PASSWORD = 当使用基本验证模式时，客户在密码对话框中输入的密码   
AUTH_TYPE = 是用户访问受保护的脚本时，服务器用於检验用户的验证方法   
AUTH_USER = 代证的用户名  
CONTENT_TYPE = 客户发送的FORM內容或HTTPPUT的数据类型。

###### 请求头字段获取

例如请求头中有一个`AuthToken`字段，那么可以在子配置的`serverVar`中填入`HTTP_AUTHTOKEN`来获取。变量名字母必须大写，

----

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
| 8    | 服务器变量Json长度                                        |
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