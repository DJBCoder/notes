@[toc](CSS背景及应用)

&emsp;&emsp;CSS可以添加背景颜色和背景图片，以及来进行图片设置。

background-color | 背景颜色
-|-
background-image | 背景图片地址
background-repeat | 是否平铺
background-position | 背景位置
background-attachment | 背景固定还是滚动
背景的合写（复合属性）|background:背景颜色 背景图片地址 背景平铺 背景滚动 背景位置

# 背景图片(image)
&emsp;&emsp;语法： 

```css
background-image : none | url (url)
```

+ none：无背景图（默认的）
+ url：使用绝对或相对地址指定背景图像

&emsp;&emsp;background-image属性允许指定一个图片展示在背景中（只有CSS3才可以多背景），可以和 background-color连用。如果图片不重复地话，图片覆盖不到地地方都会被背景色填充；如果有背景图片平铺，则会覆盖背景颜色。

> 提倡背景图片后面的地址url不要加引号

# 背景平铺（repeat）

&emsp;&emsp;语法：

```css
background-repeat : repeat | no-repeat | repeat-x | repeat-y
``` 

+ repeat：背景图像在纵向和横向上平铺（默认的）
+ no-repeat：背景图像不平铺
+ repeat-x：背景图像在横向上平铺
+ repeat-y：背景图像在纵向平铺

# 背景位置(position)
&emsp;&emsp;语法：

```css
background-position : length || length
background-position : position || position
```

+ length：百分数 | 由浮点数字和单位标识符组成的长度值。
+ position：top | center | bottom | left | center | right

&emsp;&emsp;说明：

+ 设置或检索对象的背景图像位置必须先指定background-image属性
+ 默认值为：(0% 0%) 及 （left, top）
+ 如果只指定了一个值，该值将用于横坐标，纵坐标将默认为50%
+ 第二个值将用于纵坐标。
+ 如果使用postion只传入一个值，第二个值则默认为center，如：background-position: left; 等价于 background-position:left center;

&emsp;&emsp;总结：

1. position后面是x坐标和y坐标，可以使用方位名词或者精确单位。
2. 如果和精确单位和方位名字混合使用，则必须是x坐标在前，y坐标后面。比如 background-position: 15px top; 则15px一定是x坐标，top是y坐标。

# 背景附着
&emsp;&emsp;语法：

```css
background-attachment : scroll | fixed 
```

+ scroll：背景图像是随对象内容滚动(默认的)
+ fixed：背景图像固定

# 背景简写
&emsp;&emsp;background属性的值的书写顺序官方并没有强制标准的。为了可读性，建议大家如下写：

```css
background:背景颜色 背景图片地址 背景平铺 背景滚动 背景位置
```

&emsp;&emsp;如：

```css
background: transparent url(image.jpg) repeat-y  scroll 50% 0 ;
```

# 背景透明(CSS3)
&emsp;&emsp;CSS3支持背景半透明的写法语法格式是:

```css
background: rgba(0,0,0,0.3);
```

&emsp;&emsp;最后一个参数是alpha透明度，取值范围 0~1之间

> *__注意：__* 背景半透明是指盒子背景半透明，盒子里面的内容不收影响

# 背景缩放(CSS3)
&emsp;&emsp;通过background-size设置背景图片的尺寸，就像我们设置img的尺寸一样，在移动Web开发中做屏幕适配应用非常广泛。其参数设置如下：

+ 可以设置长度单位(px)或百分比（设置百分比时，参照盒子的宽高）
+ 设置为cover时，会自动调整缩放比例(等比例缩放)，保证图片始终填充满背景区域，如有溢出部分则会被隐藏
+ 设置为contain会自动调整缩放比例，保证图片始终完整显示在背景区域(图片是完整的，高度和宽度有一个和盒子一样大，就不会在进行缩放，会有部分裸露)

```css
background-image: url('images/gyt.jpg');
background-size: 300px 100px;
/* background-size: contain; */
/* background-size: cover; */
```

# 多背景(CSS3)
&emsp;&emsp;以逗号分隔可以设置多背景，可用于自适应布局，做法就是用逗号隔开就好了。

+ 一个元素可以设置多重背景图像 
+ 每组属性间使用逗号分隔
+ 如果设置的多重背景图之间存在着交集（即存在着重叠关系），前面的背景图会覆盖在后面的背景图之上。
+ 为了避免背景色将图像盖住，背景色通常都定义在最后一组上，

```css
background:url(test1.jpg) no-repeat scroll 10px 20px/50px 60px  ,
url(test1.jpg) no-repeat scroll 10px 20px/70px 90px ,
url(test1.jpg) no-repeat scroll 10px 20px/110px

# 凹凸文字

```css
<head>
    <meta charset="utf-8">
    <style>
    body {
        background-color: #ccc;
    }
    div {
        color: #ccc;
        font: 700 80px "微软雅黑";
    }
    div:first-child {
        /* text-shadow: 水平位置  垂直位置  模糊距离 阴影颜色; */
        text-shadow: 1px 1px 1px #000, -1px -1px 1px #fff;
    }
    div:last-child {
        /* text-shadow: 水平位置  垂直位置  模糊距离 阴影颜色; */
        text-shadow: -1px -1px 1px #000, 1px 1px 1px #fff;
    }

    </style>
</head>
<body>
<div>我是凸起的文字</div>
<div>我是凹下的文字</div>
</body>
```

# 导航栏案例
## 文本的装饰
&emsp;&emsp;text-decoration通常我们用于给链接修改装饰效果：

值 | 描述
- | -
none| 默认。定义标准的文本
underline | 定义文本下的一条线(下划线也是我们链接自带的)
overline | 定义文本上的一条线
line-through | 定义穿过文本下的一条线

> **使用技巧**：在一行内的盒子内，我们设定行高等于盒子的高度，就可以使文字垂直居中。(盒子只有一行文本有效，多了就不行了)

```html
<head>
        <meta charset="utf-8">
        <style>
		body {
			background-color: #000;
		}
		a {
			width: 200px;
			height: 50px;
			/* background-color: orange; */
			display: inline-block;  /* 把a 行内元素转换为行内块元素 */
			text-align: center;  /* 文字水平居中 */
			line-height: 50px;  /* 我们设定行高等于盒子的高度，就可以使文字垂直居中 */
			color: #fff;
			font-size: 22px;
			text-decoration: none;  /* 取消下划线 文本装饰 */
		}
		a:hover {  /* 鼠标经过 给我们的链接添加背景图片*/
			background: url(images/h.png) no-repeat; 
		}
        </style>
    </head>
    <body>
    <a href="#">专区说明</a>
    <a href="#">申请资格</a>
    <a href="#">兑换奖励</a>
    <a href="#">下载游戏</a>
    </body>
```
