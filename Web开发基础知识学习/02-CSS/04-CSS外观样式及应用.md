@[toc](CSS外观样式及应用)

# color:文本颜色
&emsp;&emsp;color属性用于定义文本的颜色，其取值方式有如下3种：

1. 预定义的颜色值，如：red，green，blue等

2. 十六进制，如：#FF0000，#FF6600，#29D794等，实际工作中，十六进制是最常用的定义颜色的方式

3. RGB代码，如：红色可以表示为rgb(255,0,0)或rgb(100%,0%,0%)。（ *__需要注意的是，如果使用RGB代码的百分比颜色值，取值为0时也不能省略百分号，必须写为0%__* ）

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>文本颜色</title>
    <style>
        /* 使用预定义颜色 */
        .red {
            color: red;
        }

        /* 使用十六进制 */
        .green {
            color: #00ff00;
        }

        /* 使用rgb */
        .blue {
            color: rgb(0,0,255);
        }
    </style>
</head>
<!-- 01-文本颜色 -->
<body>
    <span class="red">red</span>
    <span class="green">green</span>
    <span class="blue">blue</span>
</body>
</html>
```

## 颜色半透明(css3)
&emsp;&emsp;文字颜色到了CSS3我们可以采取半透明的格式了语法格式如下：

```css
color: rgba(r,g,b,a);  
/*
1. a是alpha，透明的意思  
2. 取值范围 0~1之间
3. 如：color: rgba(0,0,0,0.3)  
*/
```

```html
<!-- 06-半透明颜色 -->
<body>
    <h1 style="color: rgba(255,0,0,0.5);">这里有一段文本</h1>
</body>
```

#  line-height:行间距
&emsp;&emsp;line-height属性用于设置行间距，就是行与行之间的距离，即字符的垂直间距，一般称为行高。line-height常用的属性值单位有三种，分别为像素px，相对值em和百分比%，实际工作中使用最多的是像素px。一般情况下，行距比字号大7.8像素左右就可以了。

```html
<!-- 02-行间距 -->
<body>
    <p style="line-height: 25px;">
        阿斯顿阿斯顿爱上多少啊的阿斯顿阿斯顿爱上打算d爱上d
        奥迪阿斯顿阿斯顿阿斯顿阿斯顿阿斯顿阿斯顿阿斯顿撒的阿斯顿撒的阿斯顿
        阿斯顿阿斯顿阿斯顿阿斯顿撒的阿斯顿阿斯顿阿斯顿阿斯顿
        阿斯顿撒的阿斯顿阿斯顿阿斯顿撒打算d阿斯顿asd阿斯顿。
    </p>
</body>
```

# text-align:水平对齐方式
&emsp;&emsp;text-align属性用于设置文本内容的水平对齐，相当于html中的align对齐属性。其可用属性值如下：

+ left：左对齐（默认值）
+ right：右对齐
+ center：居中对齐

```html
<!-- 03-水平对齐方式 -->
<body>
    <p style="text-align: center;">center对齐</p>
    <p style="text-align: left;">左对齐</p>
    <p style="text-align: right;">右对齐</p>
</body>
```

# text-indent:首行缩进
&emsp;&emsp;text-indent属性用于设置首行文本的缩进，其属性值可为不同单位的数值、em字符宽度的倍数、或相对于浏览器窗口宽度的百分比%，允许使用负值。建议使用em作为设置单位。1em就是一个字的宽度，如果是汉字的段落，1em就是一个汉字的宽度。

```html
<!-- 04-首行缩进 -->
<body>
    <p style="text-indent: 2em;">阿斯顿奥迪撒的奥迪阿斯顿阿斯顿爱上打算打算的阿斯顿
        阿斯顿阿斯顿阿斯顿阿斯顿阿斯顿阿斯顿撒的
        阿斯顿阿斯顿爱上大声点阿斯顿阿斯顿阿斯顿阿斯顿阿斯顿阿斯顿
        阿斯顿撒的阿斯顿阿斯顿撒打算打算打算打算d阿斯顿
        阿斯顿撒的阿斯顿撒的阿斯顿阿斯顿阿斯顿
        撒打算打算的
    </p>
</body>
```

# 字间距和单词间距
## letter-spacing:字间距
&emsp;&emsp;letter-spacing属性用于定义字间距，所谓字间距就是字符与字符之间的空白。其属性值可为不同单位的数值，允许使用负值，默认为normal。

```html
<!-- 05-字间距和单词间间距 -->
<body>
    <p style="letter-spacing: 3em;">Hello World</p>
    <p style="letter-spacing: 3em;">我是DJBCoder</p>
</body>
```

# word-spacing:单词间距
&emsp;&emsp;word-spacing属性用于定义英文单词之间的间距，对中文字符无效。和letter-spacing一样，其属性值可为不同单位的数值，允许使用负值，默认为normal。

```html
<!-- 05-字间距和单词间间距 -->
<body>
    <p style="word-spacing: 3em;">Hello World</p>
    <!-- 有中文，所以无效 -->
    <p style="word-spacing: 3em;">我是DJBCoder</p>
</body>
```

> *__注意：__* word-spacing和letter-spacing均可对英文进行设置。不同的是letter-spacing定义的为字母之间的间距，而word-spacing定义的为英文单词之间的间距。

# 文字阴影效果
&emsp;&emsp;我们可以给文字添加阴影(Shadow)效果：

```css
text-shadow:水平位置 垂直位置 模糊距离 阴影颜色;
```

值 | 描述
- | -
h-shadow | 必须，水平阴影的位置，允许负值
v-shadow | 必须，垂直阴影的位置，允许负值
blur | 可选，模糊的距离
color | 可选，阴影的颜色

```html
<!-- 07-阴影效果 -->
<body>
    <h1 
    style="text-shadow: 2px 2px 3px rgba(0,0,0,0.4);"
    >这里是标题</h1>
</body>
```