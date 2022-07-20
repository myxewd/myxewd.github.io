使用spawn-fcgi启动mengcgi处理程序

```sh
spawn-fcgi -f ./cgi-bin/echo-cpp.exe -a 127.0.0.1 -p 8081
```

启动Nginx，mengcgi主程序的安装与启动过程完成