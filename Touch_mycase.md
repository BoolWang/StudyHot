# 基于Flask框架的Web前端开发

用于实现部门内部的数据分析case的可视化

## 1. 需要用到的技术

| 名称             | 用途                                                         |
| ---------------- | ------------------------------------------------------------ |
| HTML             | 前端页面的基本框架                                           |
| CSS              | 对前端页面进行修饰                                           |
| JavaScript       | 可以理解为前端的脚本语言，可以控制前端页面的动态内容，也可以实现与后端的数据交互 |
| JavaScript--ajax | 前端连接后端数据接口的工具                                   |
| Flask            | python的轻量级web开发框架，与一般的python项目不同的是它可以编写可与ajax连接的数据接口 |
| echarts          | 可视化图表样式库                                             |

## 2. 开始——创建Flask项目

用pycharm创建一个Flask项目，该项目的python环境`需要安装flask包`，项目的目录结构为：

```
-projectName
	-static      #目录，用于存放静态资源，例如css样式库、JavaScript依赖包等
	-templates   #目录，用于存放网页，HTML文件
	-projectName.py   #python文件，用于启动整个项目
```

## 3. 确定需求——编写HTML文件

首先在项目的`templates`目录下创建`index.html`文件

这里需要用到HTML页面布局的相关知识

## 4. ajax接口测试

首先在`h5页面`中创建要显示的可变变量，用id唯一标识

```
<p id="t1"></p>
```

然后在JavaScript代码部门将id与变量绑定

```
var t1=document.getElementById("t1")
t1.innerText="这是可变变量控制测试"
```

再在JavaScript代码部分编写读取flask接口消息的函数

```
function gettext(){
		var _url="/settext";//flask框架中的接口url
		var xmlhttp; 
		if (window.XMLHttpRequest) 
		  {// code for IE7+, Firefox, Chrome, Opera, Safari 
		  xmlhttp=new XMLHttpRequest(); 
		  } 
		else 
		  {// code for IE6, IE5 
		  xmlhttp=new ActiveXObject("Microsoft.XMLHTTP"); 
		  }
		xmlhttp.open("GET",_url,false)
		xmlhttp.send()
		return xmlhttp.responseText;
	}
```

同时在python中编写好flask接口

```
@app.route('/settext')	
def settext():
	return "ajax从flask传参测试"
```

## 5. echarts绘图测试

绘图的代码同样要在JavaScript中编写，绘图需要三个重要元素

| 绘图的位置 | 同样现在页面中通过唯一id指定      |
| ---------- | --------------------------------- |
| 绘图的样式 | 从echarts官网下载对应的option对象 |
| 绘图的数据 | 根据option对象内容灵活设置        |

首先需要在页面中给图表画布指定位置

```
<div id="testfig1" style="width: 1350px; height: 600px;"></div>
```

**这里一定要指定画布的宽度和高度，否则后面会报错**

还需要引入echarts相关支撑`.js`文件

```
<script src="../static/js/jquery.js" type="text/javascript" charset="utf-8"></script>
<script src="../static/js/echarts-all.js" type="text/javascript" charset="utf-8"></script>
```

然后先生成echarts对象，如果不指定画布的高和宽就无法生成

```
var fig1=document.getElementById("testfig1")
var mycharts=echarts.init(fig1) //生成echarts对象，需要参数fig1来初始化，即告诉JavaScript该在哪个位置生成对像
```

接下来去官网找到绘图的样式

```
option = {
    xAxis: {
        type: 'category',
        data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
    },
    yAxis: {
        type: 'value'
    },
    series: [{
        data: [820, 932, 901, 934, 1290, 1330, 1320],
        type: 'line'
    }]
};
```

本质上是一个嵌套字典，图表里面的数据也需要在这时指定，这些数据可以用提前定义好的变量代替

```
var week=['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
var weekData=[820, 932, 901, 934, 1290, 1330, 1320]
option = {
    xAxis: {
        type: 'category',
        data: week
    },
    yAxis: {
        type: 'value'
    },
    series: [{
        data: weekData,
        type: 'line'
    }]
};
```

最后调用echarts对象的`setOption`方法进行绘图

```
if (option && typeof option === "object") {
	myChart.setOption(option, true);
}
```

