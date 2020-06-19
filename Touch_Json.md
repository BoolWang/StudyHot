# Touch_Json

json文件的学习

## 1. Python读写json文件

json模块提供了四个功能

| 名称  | 功能                             |
| ----- | -------------------------------- |
| dumps | 数据类型转换成字符串             |
| dump  | 数据类型转换成字符串并存储到文件 |
| loads | 字符串转换成数据类型             |
| load  | 把文件打开从字符串转换成数据类型 |

### 1.1 dump将数据类型装换成字符串并存储到文件

```python
a=['1','2','3']
with open("file_path","w") as f:
    f.dump(a,f)
```

