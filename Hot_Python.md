# Hot_Python

python的常用操作

## 1. `filter`使用匿名函数快速按条件过滤容器内容

```python
a=list(....)
a1=list(filter(lambda x:x==***,a))
```

## 2. 数字转字符串

```python
a=1
b="%s"%a
```

## 3. 创建虚拟环境

首先将要复制的源环境`activate`

```
cd /root_python_dir/Scripts
activate
```

然后切换到要建立的新环境的目录下(空目录)

```
cd ../../new_env
vituralenv new_env
```

