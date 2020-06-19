# mongodb服务器端的操作

特指Linux系统服务器

## 1. 启动

```bash
mongod -f mongod.conf
```

参数`mongodb.conf`需要给出具体路径，一般默认在`/etc/`目录下

## 2. 关闭

```bash
pkill mongod
```

## 3. 开机自启

编辑开机文件`/etc/rc.local`，在最后一行插入启动命令

```bash
vi /etc/rc.local
mongod -f mongod.conf
```

## 4. 打开mongo shell(带用户认证)

```bash
mongo -u <username> -p --authenticationDatabase <databasename>
```

