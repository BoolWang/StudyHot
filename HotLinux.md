# HotLinux

Linux命令行常用操作

## 1. 查看命令所在位置

```bash
which ls
```

## 2. 首次登陆设置root密码

```
sudo passwd root
```

## 3. 查看系统版本信息

```shell
lsb_release -a
```

## 4. 查看系统是32还是64位

```shell
getconf LONG_BIT
```

## 5. 安装系统自带的上传下载插件

```shell
yum install -y lrzsz
```

使用

```
上传：rz
下载：sz 
```

## 6. 创建新用户

```
useradd -m 用户名
```

## 7.ssh

生成本机秘钥

```
ssh-keygen -t rsa
```

## 8. 配置普通用户到sudoers中

```
nano /etc/sudoers
```

在`root    ALL=(ALL)	ALL`一行下面添加

```
普通用户名    ALL=(ALL)	ALL
```

