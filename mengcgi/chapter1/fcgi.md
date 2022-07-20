由于MengCgi不像·`PHP`自带`PHP-fpm`，所以需要使用`spawn-fcgi`映射端口

spawn-fcgi一般是在Linux上使用，在Windows平台使用VS编译会报错，所以这里免费提供编译好的`x86`程序

```
链接：https://pan.baidu.com/s/1jR44y8xkOAXHd80JjslDng 
提取码：q7ly
```

下载`spawn-fcgi.exe`程序，放到`Wnmp`根目录下

<img src="https://img-1305199327.cos.ap-shanghai.myqcloud.com/202205021855112.png" style="zoom:75%;" />

### 环境变量配置

把你的Wnmp安装目录添加到系统环境变量Path中

例如安装目录为 `C:\Wnmp`

<img src="https://img-1305199327.cos.ap-shanghai.myqcloud.com/202205021857509.png" style="zoom:80%;" />

### Nginx配置

这里映射的端口选择 `8081`

```nginx
location ~ \.mxl$ {
      fastcgi_pass 127.0.0.1:8081;
      fastcgi_index index.mxl;
      include fastcgi.conf;
}
```

把上面这段配置添加到`nginx.conf`的Server字段

