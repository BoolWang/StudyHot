# Touch_HTML

html入门学习中的问题

## 1. 中文乱码显示

在文件头添加编码格式，如果是用nodepad等编辑器需要保证编辑器的编码格式和`charset`的值一致

```
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
```

## 2. 换行标签

```html
<br/>
```

## 3. 背景图片设置的坑

### 3.1 直接使用background属性

使用绝对路径时可以接受两种格式的路径分隔符`\`和`/`，但要加引号

```html
<body background="G:/Chrome下载/5b66a3b1ddbb1125485eb70884c796ef1.jpg">
    content.......
</body>
```

### 3.2 使用style样式

只能接受`/`路径分隔符，不用加引号

```
<body style="background-image: url(F:/programfiles/brackets/samples/zh-cn/5b66a3b1ddbb1125485eb70884c796ef1.jpg)">
    </body>
```

## 4. 多框架显示（多个html文件组合）

**重要提示：**不能将` <body></body>` 标签与 `<frameset></frameset> `标签同时使用！

```
<frameset cols="25%,75%">
   <frame src="a.htm"></frame>
   <frame src="b.htm"></frame>
</frameset>
```

