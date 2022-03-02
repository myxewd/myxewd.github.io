### 快速入门

例如在示例Json中，你要查找field数组中所有`location`值为”中国“的对象中的`name`值，那么Json语句就应该为

```sqlite
select('name')WHERE 'field[{n}]'WHOSElocation='中国'
```

Jsql会给出如下返回

```json
{
    "data": [{
        "name": ["泰山"]
    }, {
        "name": ["峨眉山"]
    }]
}
```

要特别注意的是，Jsql遵循严格大小写规则，符号必须为半角符号且字母的大小写情况必须和Json中的字段名称符合。

**祝您使用Jsql愉快**