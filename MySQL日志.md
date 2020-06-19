# MySQL日志

在生产和测试过程中，我们经常需要查看MySQL的的日志信息，或是对数据库进行维护，或是对性能进行评估

## 1. 查看慢查询日志

查询操作时间超过指定时间时会被记录，可以用来对查询语句进行优化

```sql
#查询指定时长
show global variables like  'long_query_time';
#设置时长为2s，注意一定要写成浮点数形式
set global long_query_time = 2.0
#设置日志存储方式"FILE"、"TABLE"均是系统参数
SET GLOBAL log_output = "TABLE";
```

