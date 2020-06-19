# pyMongo

python远程连接mongodb数据库

## 1. 安装

```bash
pip install pymongo
```

## 2. 连接

```python
import pymongo as pmg
myclient=pmg.MongoClient(host=<ipaddr>,port="27017",username="root",password="******",authSource="admin")
#获取数据库列表
dblist = myclient.list_database_names()
print(dblist)
```

## 3. 读取集合

```
#切换到数据库
mydb=myclient[<dbname>]
#切换到集合
mycol=mydb[<colname>]
```

## 4. 插入文档到集合

```
mydoc={"name": "hello mongo 333", "age": "19"}
obj=mycol.insert_one(mydoc)
```

这里要注意的是在插入文档的时候键名也需要加引号变为字符串，否则会被python识别成变量