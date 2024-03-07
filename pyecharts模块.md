# 	pyecharts模块

### 导入pyecharts

```python
from pyecharts.charts import Bar #导入要绘画的图像
from pyecharts import options as opts  #设置配置项
from pyecharts.faker import Faker #自带的随机数据
from pyecharts.globals import ThemeType,RenderType #主题类型
```

------

```python
图名.overlap(图名)  #把overlap中的图与前面的图合并
```

------

`Faker.choose()`：随机生成七个同类型的例子

`Faker.values()`：随机生成一组数

`Faker.week`：星期

`Faker.cars`：七个车名称	

`Faker.country`：七个国家

`Faker.visual_color`：十一个颜色

`Faker.days_attrs`：天

`Faker.clock`：时钟

------

### 设置配置项

#### 初始配置项：

#### `init_opts = opts.InitOpts()`

```python
Bar(
	init_opts = opts.InitOpts(
		width = 'numpx',    #画布的宽
		height = 'numpx',	#画布的高
		page_title = '网页标题',
		renderer = RenderType.CANVAS,	#渲染风格，可选canvas,svg
		theme = ThemeType.WALDEN,	#主题 LIGHT
		bg_color = '颜色'		#背景颜色
	)
)
```

#### 全局配置型：`set_global_opts()`

##### 标题配置项：

##### `title_opts = opts.TitleOpts()`

```python
Bar()
.set_global_opts(
	title_opts = opts.Titleopts(
		title = '主标题',		#主标题
		title_link='URL',	#主标题点击跳转链接
		title_target = 'blank'		#blank为跳转链接至新窗口打开,self为当前窗口打开
        
        subtitle = '副标题',
        subtitle_link = 'URl' 	#副标题点击跳转链接
        subtitle_target= 'blank'	   #blank为跳转链接至新窗口打开,self为当前窗口打开
        
        #位置
        pos_left = 'numpx'或'百分比',	#主副标题与左边框的距离
        pos_right = 'numpx'或'百分比',	#主副标题与右边框的距离
        pos_top = 'numpx'或'百分比',	#主副标题与上边框的距离
		pos_buttom = 'numpx'或'百分比'	#主副标题与下边框的距离	
        padding = num,		#内边距
        item_gap = num,		#主标题与副标题之间的距离
    )
)
```

##### 区域缩放配置器：

##### `datazoom_opts = opts.DataZoomOpts()`

```python
Bar()
.set_global_opts(
	datazoom_opts = opts.DataZoomOpts(
    	is_show = True,		#是否显示组件
        is_realtime = True,	#拖动窗口是否实时更新图表
        is_zoom_lock = False, #是否锁定选择区域
        type_='slider',		#组件的类型：slider：滑动块,inside:滚轮
        range_start = num,	#数据窗口的起始百分比
        range_end = num,	#数据窗口的结尾百分比
        orient = 'horizontal', 	#组件方向'horizontal':横向 或 'vertical'：竖向
    )
)
```

##### 图例配置项：

##### `legend_opts = opts.LegndOpts()`

```python
Bar()
.set_global_opts(
	legend_opts = opts.LegndOpts(
		is_show=True,	#是否显示图例
        type_='plain',	#图例的类型：plain：普通图例,scroll：滚动图例
        orient='horizontal',	#组件方向'horizontal':横向 或 'vertical'：竖向
        padding=10,		#图例与边框的距离
        align='left',	#图例和文字的位置
        
        pos_left = 'numpx'或'百分比',	#图例与左边框的距离
        pos_right = 'numpx'或'百分比',	#图例与右边框的距离
        pos_top = 'numpx'或'百分比',	#图例与上边框的距离
		pos_buttom = 'numpx'或'百分比'	#图例与下边框的距离
            
        #图例选择模式:
        #True:开启图例
        #False:关闭图例选择
        #single:单选
        #multiple:多选
        selected_mode=True,
        inactive_color='',	#图例全部不选展示的颜色
        
        item_gap=num, 	#图例之间的距离
        item_height=num,	#图例的高度
        item_width=num,	#图例的宽度
            
        #Pyecharts中常见的图标: circle,roundRect,triangle,diamond
        legend_icon='triangle',
	)
)
```

##### 视觉映射配置项：

##### `visualmap_opts = opts.VisualMapOpts()`

```python
Bar()
.set_global_opts(
	visualmap_opts = opts.VisualMapOpts(
    	is_show=True,
        is_piecewise=False,     #是否为分段形
        is_inverse=False,   #是否反转
        
        type='color',    #视觉映射的类型：color,size
        min_=50,		#最小值
        max_=100,	#最大值
        range_opacity=0.7,   #图文透明度
        range_text=['max','min'],	#两端的文本说明
        range_color=['',''],	#过度颜色
        orient='horizontal',	#组件方向'horizontal':横向 或 'vertical'：竖向
            
        pos_left = 'numpx'或'百分比',	#映射图例与左边框的距离
        pos_right = 'numpx'或'百分比',	#映射图例与右边框的距离
        pos_top = 'numpx'或'百分比',	#映射图例与上边框的距离
		pos_buttom = 'numpx'或'百分比'	#映射图例与下边框的距离
    )
)
```

##### 提示框配置项：

##### `tooltip_opts=opts.TooltipOpts()`

```python
Bar()
.set_global_opts(
	tooltip_opts=opts.TooltipOpts(
    	is_show=True,
            
        #触发类型：
        #item：数据项，一般用于：散点图，柱状图，饼图
        #axis：坐标轴，一般用于：折线图，条形图等
        trigger='item',
            
        #触发条件：mousemove:鼠标移动，click:点击
        trigger_on='mousemove',
            
        #标签内容的格式
        #{a}:系列名
        #{b}:数据名
        #{c}:值
        formatter='{a}:{b} {c}',
    )
)
```

# 坐标轴配置项：

##### `xaxis_opts = opts.AxisOpts`

##### `yaxis_opts = opts.AxisOpts`

```python
Line()
.set_global_opts(
	xaxis_opts = opts.AxisOpts(
    	is_show=True,	#是否显示x轴
        
        #坐标轴类型
        #   value：数值轴，用于连续数据
        #   category：类目轴，适用于离散数据
        #   time：时间轴，适用于连续的时间数据
        type_='category',
        axisline_opts=opts.AxisLineOpts(is_show=True),	#是否显示轴
        axistick_opts=opts.AxisTickOpts(is_show=False), #是否显示刻度
        axislabel_opts=opts.LabelOpts(rotate=-15)	#x轴标签角度
        splitline_opts=opts.SplitLineOpts(is_show=False)   #是否显示网格线
        
        boundary_gap=False	#让图与y轴之间没有间距
    ),
    yaxis_opts = opts.AxisOpts(
    	is_show=True,	#是否显示y轴
        axisline_opts=opts.AxisLineOpts(is_show=True), #是否显示轴
        axistick_opts=opts.AxisTickOpts(is_show=False)  #是否显示刻度
        splitline_opts=opts.SplitLineOpts(is_show=False)   #是否显示网格线
        
    )
)
```

### 系列配置项：`set_series_opts()`

#### 图元样式配置型：

#### `itemstyle_opts=opts.ItemStyleOpts()`

```python
Line()
.set_series_opts(
	itemstyle_opts=opts.ItemStyleOpts(
    	#图的颜色
        #可以用纯色
        #可以用RGB色：rgb(num,num,num) 或 可以改透明度：rgba(num,num,num,0.7)
        #十六进制：#ccc
        color='blue',
        opacity=0.7,     #透明度            
        border_color='yellow',    #边框颜色
        border_width=5,    #边框宽度'
    )
)
```

#### 线样式配置项：

#### `linestyle_opts=opts.LineStyleOpts()`

```python
Line()
.set_series_opts(
	linestyle_opts=opts.LineStyleOpts(
    	is_show=True,
        color='blue',   #线颜色
        width=2,    #线宽
        type_='dashed',     #线的类型：solid:实线,dashed:虚线,dotted:点线
        curve=num		#弯曲度
    )
)
```

#### 标签配置型：

#### `label_opts=opts.LabelOpts()`

```python
Line()
.set_series_opts(
	label_opts=opts.LabelOpts(
    	is_show=True,
        
        #标签位置
        #   left,right,top,buttom
        #   inside,insideLeft,insideRight,insideTop,insideButtom
        #   等
        position='top',     #位置
        
        color='blue',
        font_size=20,   #文字大小
        font_family='Arial',    #文字字体
        font_style='italic',      #是否斜体normal：正常的,ltalic：斜体
        font_weight='normal',     #是否加粗,normal：正常的,bold：加粗
        
        #标签旋转：-90~90
        rotate=40,
    )
)
```

#### 标记点配置项：

#### `markpoint_opts=opts.MarkPointOpts()`

```python,
Line()
.set_series_opts(
	`markpoint_opts=opts.MarkPointOpts(
		data=[
		 #type_：max,min,average
         #symbol：标记点图像
         #symbol_size：标记点大小
         opts.MarkPointItem(type_='max')
		]
	)`
)
```

#### 标记线配置项：

#### `markline_opts=opts.MarkLineOpts()`

```python
Line()
.set_series_opts(
	markline_opts=opts.MarkLineOpts(
    	data=[
            #type_：max,min,average
            opts.MarkLineItem(type_='max')
        ]
    )
)
```



## 柱状图

```python
from pyecharts.charts import Bar

bar = (
    Bar()
    .add_xaxis(x)
    .add_yaxis('系列名',y)
)
bar.render('基础柱状图.html')
```



## 堆叠柱状图

```python
from pyecharts.charts import Bar

bar = (
    Bar()
    .add_xaxis(x)
    .add_yaxis('系列名1',y,stack='name')
    .add_yaxis('系列名2',y,stack='name')
)
bar.render('基础柱状图.html')
```



## 条形图

```python
from pyecharts.charts import Bar

bar = (
    Bar()
    .add_xaxis(x)
    .add_yaxis('系列名',y)
    .reversal_axis()
)
bar.render('条形图.html')
```



## 直方图

```python
from pyecharts.charts import Bar

bar = (
    Bar()
    .add_xaxis(x)
    .add_yaxis('系列名',y,category_gap='0%') #与底边框的占比
)

bar.render('直方图.html')

#调节不同系列柱子之间的距离
bar = (
    Bar()
    .add_xaxis(x)
    .add_yaxis('系列名1',y,gap='0%')
    .add_yaxis('系列名1',y,gap='0%')
)

bar.render('直方图.html')
```



## 饼图

```python
from pyecharts.charts import Pie
from pyecharts.faker import Faker

xy = [list(i) for i in zip(Faker.choose(),Faker.values())]
pie = (
    Pie()
    .add('',xy)
)
pie.render('基础饼图.html')
```



## 玫瑰图

```python
from pyecharts.charts import Pie
from pyecharts.faker import Faker

xy = [list(i) for i in zip(Faker.choose(),Faker.values())]

pie = (
    Pie()
    .add('',xy,
        radius=['60%','70%'],   #半径大小百分比 分别代表 空白园大小 和 突出大小
        center=['50%','50%'],   #位置关系百分比 分别代表 横向百分比大小 和 竖向百分比大小
        rosetype='radius'   #或 area:小一点
    )
)
pie.render('基础玫瑰图.html')
```



## 雷达图

```python
from pyecharts.charts import Radar
from pyecharts import options as opts

v1 = [[90,130,150,120,60]]
radar = (
    Radar()
    .add_schema(
        schema=[
            opts.RadarIndicatorItem(name = '语文',max_=150),
            opts.RadarIndicatorItem(name = '数学',max_=150),
            opts.RadarIndicatorItem(name = '英语',max_=150),
            opts.RadarIndicatorItem(name = '政治',max_=150),
            opts.RadarIndicatorItem(name = '科学',max_=150),
        ]
    )
    .add('成绩',v1)
)
radar.render('基础雷达图.html')
```



## 折线图

```python
from pyecharts.charts import Line

line = (
    Line()
    .add_xaxis(x)
    .add_yaxis('系列名',y,symbol='triangle',symbol_size=num)
     #symbol：点图像：triangle三角形
     #symbol_size：点的大小
)
line.render('基础折线图.html')
```

 

## 面积图

```python
from pyecharts.charts import Line

line = (
	Line()
    .add_xaxis(x)
    .add_yaxis('系列名',y,areastyle_opts=opts.AreaStyleOpts(opacity=num))
)

#堆叠面积图
line = (
	Line()
    .add_xaxis(x)
    .add_yaxis('系列名',y,areastyle_opts=opts.AreaStyleOpts(opacity=num),stack='name')
    .add_yaxis('系列名',y,areastyle_opts=opts.AreaStyleOpts(opacity=num),stack='name')
)
```



## 散点图

```python
from pyecharts.charts import Scatter

data = [
    [2.0,5.6],
    [3.5,1.8],
    [4.8,7.5],
    [3.6,8.1],
    [2.8,4.1]
]
data.sort(key=lambda x:x[0])
scatter = (
    Scatter()
    .add_xaxis([i[0] for i in data])
    .add_yaxis('',[i[1] for i in data])
    .set_global_opts(
        tooltip_opts=opts.TooltipOpts(trigger='axis')
    )
)
```



## 涟漪散点图

```python
from pyecharts.charts import EffectScatter

effectscatter = (
    EffectScatter()
    .add_xaxis(x)
    .add_yaxis(
        '',
        [10,2,70,50,40,60,70],
        effect_opts=opts.EffectOpts(
            scale=10,   #涟漪范围
            period=2    #涟漪速度
        )
    )
)
```



## 热力图

```python
from pyecharts.charts import HeatMap

value = [[i,j,random.randint(0,50)] for i in range(24) for j in range(7)]
heatmap = (
    HeatMap()
    .add_xaxis(Faker.clock)
    .add_yaxis('',Faker.week,value)
)
```



## 日历图

```python
from pyecharts.charts import Calendar
```



## 箱型图

```python
from pyecharts.charts import Boxplot

boxplot = (
    Boxplot()
    .add_xaxis(['demo1','demo2'])
    .add_yaxis('A',data)
)
```



## 词云图

```python
from pyecharts.charts import WordCloud

wordcloud = (
    WordCloud()
    .add('',data)
)
```



## 漏斗图

```python
from pyecharts.charts import Funnel

funnel = (
    Funnel()
    .add('商品',[list(i) for i in zip(x,y)])
)
```



## 极坐标图

```python
polar = (
    Polar()
    .add('极坐标',y,type_='scatter')
)

# 圆柱状图
polar = (
    Polar()
    .add_schema(
        radiusaxis_opts=opts.RadiusAxisOpts(        #改x轴
            data=Faker.week
        ),
        angleaxis_opts=opts.AngleAxisOpts(is_clockwise=True)    #角度
    )
    .add('商品',y,type_='bar')
)

# 圆心散发的柱状图
polar = (
    Polar()
    .add_schema(
        angleaxis_opts=opts.AngleAxisOpts(
            data=Faker.week
        )
    )
    .add('商品a',y,type_='bar')
)	
```



## 水球图

```python
from pyecharts.charts import Liquid

liquid = (
    Liquid()
    .add(
        '',
        [num,num],
    	is_outline_show=False, 	#是否显示外边框
        shape=SymbolType.RECT 	#形状,RECT:正方形
    )
)
```



## 旭日图

```python
from pyecharts.charts import Sunburst

data = [
    {'name':'father','children':[
        {'name':1,'value':10},
        {'name':2,'value':20},
        ]
    }
]
sun = (
    Sunburst()
    .add('',data)
)
```



## 仪表盘

```python
from pyecharts.charts import Gauge

gauge = (
    Gauge()
    .add('油箱',[('','num')])
)
```



## 树图

```python
from pyecharts.charts import Tree

data = [
    {
        'name':'爸爸','children':[{'name':'我'},{'name':'姐姐'}]
    }
]
tree = (
    Tree()
    .add('家庭',data)
)
```



## 矩形树图

```python
from pyecharts.charts import TreeMap

data = [
    {
        'value':80,'name':'爸爸','children':[{'name':'我','value':70},{'name':'姐姐','value':10}]
    },
    {
        'value': 80, 'name': '叔叔', 'children': [{'name': '表哥', 'value': 70}, {'name': '表姐', 'value': 10}]
    }
]
treemap = (
    TreeMap()
    .add('家庭',data)
)
```



## k线图

```python
from pyecharts.charts import Kline

kline = (
    Kline()
    .add_xaxis(x)
    .add_yaxis('k线图',y)
)
```



## 地图

```python
from pyecharts.charts import Map

map = (
	Map()
    .add('',[('城市名字',value),('城市名字',value),...],'china')
)
```



## 地理坐标图

```python
from pyecharts.charts import Geo

gen = (
    Geo()
    .add_schema(maptype='china')
    .add(
        '',
        [('杭州',30),('宁波',20),('北京市',40)],
        type_=ChartType.EFFECT_SCATTER
    )
)
```



## 多图布局

```python
from pyecharts.charts import Grid
# 把多张图放到一个画布里
grid = (
    Grid()
    .add(图1)
    .add(图2)
)
```



## 时间轴

```python
from pyecharts.charts import Timeline,Bar

tl = Timeline()
for i in range(2019,2022):
    bar = (
        Bar()
        .add_xaxis(x)
        .add_yaxis('a',y)
        .add_yaxis('b',y)
    )
    tl.add(bar,f'{i}年')

#每个时间轴节点对应不同图
from pyecharts.charts import Line,Timeline,Bar,Pie
tl = Timeline()
pie = (
    Pie()
    .add('',[list(i) for i in zip(Faker.choose(),Faker.values())])
)
tl.add(pie,'2019年')
bar = (
    Bar()
    .add_xaxis(Faker.choose())
    .add_yaxis('',Faker.values())
)
tl.add(bar,'2020年')
line = (
    Line()
    .add_xaxis(Faker.choose())
    .add_yaxis('',Faker.values())
)
tl.add(line,'2020年')
```

