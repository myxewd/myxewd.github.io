先在Release节中下载MengCgi可执行文件

得到`mengcgi.exe`，在`wnmp`根目录下新建`cgi-bin`目录，放入`mengcgi.exe`

<img src="https://img-1305199327.cos.ap-shanghai.myqcloud.com/202205021903073.png" style="zoom:80%;" />

在`cgi-bin`目录内新建`conf`目录，存储`mengcgi`配置文件

### 主配置文件

```ini
[config]
wwwroot=E:\wwwroot
```

##### 参数解释

| 参数名称       | 作用解释       | 示例       |
| -------------- | -------------- | ---------- |
| config.wwwroot | http服务根目录 | E:\wwwroot |

把以上内容写入`config.ini`，放入`conf`目录

