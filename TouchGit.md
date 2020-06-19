# TouchGit

Git代码仓库的本地部署和使用

## 1. Centos上安装Git

作为仓库服务器

```
yum install git
```

## 2. Windows上安装

下载安装包安装即可

## 3. 在本地创建git仓库

创建用户

```
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

建立仓库主目录并初始化

```
mkdir sample
git init sample
```

每往sample文件夹中添加一个文件a.txt，就需要add到暂存区，再发布到仓库中

```
cp a.txt sample/a.txt
cd sample
git add a.txt
git commit -m "填写改动信息"
```

改动过a.txt也要add到暂存区，再发布到仓库中

```
cat b.text >> a.txt
git add a.txt
git commit -m "填写改动信息"
```

## 4. 创建加切换分支

```
git checkout -b dev #-b表示创建
```

合并某分支到当前分支

```
git merge <name>
```

## 5. 发布到GitHub

首先在GitHub上创建好空项目，然后复制好项目链接，再Git bash进入项目根目录

```
git remote add origin  https://gitlab*********************.git  #创建关联
git push -u origin master #推送到GitHub
```

## 6. GitHub下载到本地

进入要放置项目的目录，前提是要将本地公钥上传至GitHub

```
git clone git@github.com:BoolWang/FlearnActy.git
```

## 7. 创建本地shh公钥并上传到GitHub

先查看用户目录下是否有公钥文件，如果没有，则：

```
ssh-keygen -t rsa -C "youremail@example.com"
```

然后将公钥文件添加到GitHub即可

