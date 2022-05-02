### 程序限频

只适配于HTTP协议

在`Nginx.conf`的`HTTP`节中`Server`节外添加如下语句

```nginx
limit_req_zone $remote_addr*$arg_imei zone=zone_imei:10m rate=2r/s;
```

rate为限频规则，2r/s为每秒允许两次请求

30r/m代表每分钟三十次请求

----

在MengCgi的`location`节中添加如下语句

```nginx
limit_req zone=zone_imei burst=1;
```

##### 作用

限制请求频率对`MengCgi`非常重要，如果短时间内出现大量请求，可能导致CPU爆满。限频可以在一定程度上阻止上述现象的发生

MengCgi已经优化自身对内存的管理，可以基本做到资源的有效利用和释放，不过这也取决于Worker程序的写法。