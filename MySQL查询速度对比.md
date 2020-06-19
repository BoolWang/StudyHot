# MySQL查询速度对比

在用python中的pymysql进行数据库查询时，发现查询速度比在mysql客户端查询的慢，故进行了一些实验来寻找优化查询的方向

## 1. 数据库说明

这里只涉及一个表的查询，表一共有四个字段，1956640条记录，是关于学员的学习记录的表studyh

|      名称      | 数据类型 | 长度 |
| :------------: | :------: | :--: |
|     UserId     |   char   |  50  |
|    CourseId    |   int    |  11  |
| VideoStartTime | datetime |      |
|    SpendSec    |   int    |  11  |

## 2. 查询测试语句

首先用客户端HeidiSQL执行查询整个表的操作

```sql
select UserId from studyh
#查询时间: 0.219 sec. (+ 14.422 sec. network) 
```

在python中执行该语句

```python
cur1=getclient()
query="select UserId from studyh"
start=time.clock()
cur1.execute(query)
stop=time.clock()
print("spendtime:%s sec"%(stop-start))
[out]:spendtime:33.8294654 sec
```

以上操作都是在同一台个人计算机上执行的，为去除网络的影响，然后在树莓派上直接进行相关操作，最后得到如下的测试结果：

| 查询方式     | 时长                               |
| ------------ | ---------------------------------- |
| 远程客户端   | 0.219 sec. (+ 14.422 sec. network) |
| 远程python   | 33.8294654 sec                     |
| 服务器命令行 | 6.46 sec                           |
| 服务器python |                                    |

