# HotPython

python常用技巧

## 1. 动态输出到一行

```python
import sys

n=1000
for i in range(n):
    sys.stdout.write('\r' + "at %s"%i)
    sys.stdout.flush()
```

## 2. 删除列表重复项

```python
#使用set方法
lis=list([1,2,3,3,1,4,5,6,7,1])
uniquelis=list(set(lis))
```

## 3. 程序计时

```python
import time
start=time.clock()
time.sleep(2)#这里表示程序执行时间
stop=time.clock()
spendSec=stop-start
```

## 4.生成随机数

```
#可以用random.shuffle()函数打乱元素的顺序，该函数直接作用于列表本身，没有返回值
a=[[1,2],[2,3],[3,4]]
random.shuffle(a)
#借助这个函数可以快速生成一组介于a,b(a<=x<b)之间且不重复的n个随机数
def random_list(a,b,n):
    import numpy as np
    import random
    arr=np.arange(a,b,1)
    random.shuffle(arr)
    return sorted(arr[:n])
```

## 5. K均值聚类

```
from sklearn.cluster import k_means  #聚类模型函数
from sklearn.metrics import silhouette_score   #对模型进行评估

#聚类至少需要二维的数据，一维数据可以考虑增加一维固定常数来进行聚类
X=[[]]  #二维数据
model=k_means(X, n_clusters=4)   #后一个参数是聚类的数目
score=silhouette_score(X, model[1])  #对训练模型进行评估，分数越接近1效果越好

print(model)
#model是一个列表，返回的是分别是每一类的聚类中心（均值），X中每个元素的标签等
```

