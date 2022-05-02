### 子配置文件

子配置文件放置于wwwroot目录内，每个文件对应一个Mengcgi - Worker程序。例如文件位于/wwwroot/eg.xml，浏览器访问 http://example.com/eg.xml 时MengCgi会通过读取eg.xml中的参数运行 Worker 程序来实现交互。

```xml
<config>
    <worker>\cgi-bin\test.exe</worker>
	<server_var></server_var>
	<show_version>false</show_version>
</config>
```

| 参数名称            | 作用解释                                               | 示例              |
| ------------------- | ------------------------------------------------------ | ----------------- |
| config.worker       | 处理程序路径                                           | \cgi-bin\test.exe |
| config.server_var   | MengCgi传入处理程序的FastCgi服务器变量，以半角逗号分割 | 暂无              |
| config.show_version | 是否在 X-Powered-by 显示MengCgi标识                    | true              |

### 示例

<img src="https://img-1305199327.cos.ap-shanghai.myqcloud.com/202205021909690.png" style="zoom:80%;" />