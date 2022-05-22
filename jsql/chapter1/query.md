##### 条件查询

可以通过Jsql查询Json中符合特定条件的数据，具体命令如下

```sqlite
select('field1','field2','field3')WHERE 'ROOTPATH'WHOSE{cmpfield1}='cmpvalue1'{cmpfield2}='cmpvalue2'
```

格式必须符合上述标准，除了在WHERE后面有一个空格外，在语句除了文本以外的任何地方都不应再出现空格符号

select后面小括号`()`中的`field1`,`field2`,`field3`代表你要读取的字段名称，这个名称基于WHERE后ROOTPATH，例如ROOTPATH为`data.myxewd`，那么查询的数据就为Json表示法`data.myxewd.field1`,`data.myxewd.field2`,`data.myxewd.field3`取出的数据。所需要查询的字段个数在区间[1,+∞)范围内，即可通过(‘field1','field2','field3',...,'fieldn')表示。

ROOTPATH代表需要查询的数据在Json文档中的上级节点路径，例如在JSON

```json
{
    "name": "测试Json",
    "field": [
        {
            "location": "中国",
            "name": "泰山",
            "special":"spec"
        },
        {
            "location": "俄罗斯",
            "name": "贝加尔湖"
        },
        {
            "location": "美国",
            "name": "夏威夷岛"
        },
        {
            "location": "中国",
            "name": "峨眉山"
        },
        {
            "location": "澳大利亚",
            "name": "大沙漠"
        }
    ]
}
```

要查询field数组中`location`值为”中国“且`name`值为”泰山“的对象的`special`值，ROOTPATH就应为`field[1]`，是包含数据的对象。当然，这里的ROOTPATH支持一些特殊规则。例如以上JSON，在包含数组的情况下，ROOTPATH可以为`field[{n}]`，在这里{n}代表遍历整个数组所含对象，支持多层嵌套规则，如`a[{n}].b.c[{n}].d.[1].[{n}]`，Jsql会自动识别并转换。

在WHOSE后面，就是所需读取数据的条件。当然你也可以去掉整个WHOSE子语句，那么Jsql返回的就是所有ROOTPATH下指定的字段数据。

{cmpfield}代表条件数据所在的字段名，在实际的Jsql语句中是不包含大括号的。当Jsql读取到ROOTPATH.cmpfield的值与cmpvalue的值相同时，即认为现行对象是符合筛选条件，会将现行结果加入到返回的数据中。Jsql支持多个cmpfield存在，每个条件格式为`{cmpfield}='cmpvalue'`，多个条件之间不需要任何分隔符。