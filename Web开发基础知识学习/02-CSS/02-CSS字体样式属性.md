@[toc](CSS字体样式属性)

# 字号和字体设置
## font-size:字号大小
&emsp;&emsp;font-size属性用于设置字号，该属性的值可以使用相对长度单位，也可以使用绝对长度单位。其中，相对长度单位比较常用，推荐使用像素单位px，绝对长度单位使用较少。具体如下：

<table>
    <tr>
        <td>类型</td>
        <td>单位</td>
        <td>说明</td>
    </tr>
    <tr>
        <td rowspan="2">相对长度单位</td>
        <td>em</td>
        <td>相对于当前对象内文本的字体尺寸</td>
    </tr>
    <tr>
        <td>px</td>
        <td>像素，最常用</td>
    </tr>
    <tr>
        <td rowspan="4">绝对长度单位</td>
        <td>in</td>
        <td>英寸</td>
    </tr>
    <tr>
        <td>cm</td>
        <td>厘米</td>
    </tr>
    <tr>
        <td>mm</td>
        <td>毫米</td>
    </tr>
    <tr>
        <td>pt</td>
        <td>点</td>
    </tr>
</table>

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>字号大小</title>
    <style>
        h2 {
            font-size: 30px;
        }
        h4 {
            font-size: 14px;
        }
        p {
            font-size: 12px;
        }
    </style>
</head>
<!-- 01-字号大小 -->
<body>
    <h2>企业简介</h2>
    <h4>公司由来</h4>
    <p>阿斯顿阿斯顿爱上打算大实打实的奥迪阿斯顿奥
    迪阿斯顿奥迪爱上多少啊打算大声点阿斯顿爱上的</p>
    <h4>公司发展</h4>
    <p>阿斯顿阿斯顿爱上打算大实打实的奥迪阿斯顿奥
    迪阿斯顿奥迪爱上多少啊打算大声点阿斯顿爱上的</p>
    <h4>课程安排</h4>
    <p>阿斯顿阿斯顿爱上打算大实打实的奥迪阿斯顿奥
    迪阿斯顿奥迪爱上多少啊打算大声点阿斯顿爱上的</p>
</body>
</html>
```

## font-family:字体
&emsp;&emsp;font-family属性用于设置字体。网页中常用的字体有宋体、微软雅黑、黑体等，例如将网页中所有段落文本的字体设置为微软雅黑，可以使用如下方法：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>字体样式</title>
    <style>
        p {
            font-family: "微软雅黑";
        }
    </style>
</head>
<!-- 02-字体样式 -->
<body>
    <p>这里有一段文本</p>
</body>
</html>
```

&emsp;&emsp;可以同时指定多个字体，中间以逗号隔开，表示如果浏览器不支持第一个字体，则会尝试下一个，直到找到合适的字体：

```css
p {
    font-family: "微软雅黑", "宋体";
}
```

## 使用技巧

1. 现在网页中普遍使用14px+。
2. 尽量使用偶数的数字字号，ie6等老式浏览器支持奇数会有bug。
3. 各种字体之间必须使用英文状态下的逗号隔开。
4. 中文字体需要加英文状态下的引号，英文字体一般不需要加引号。当需要设置英文字体时，英文字体名必须位于中文字体名之前。
5. 如果字体名中包含空格、#、$等符号，则该字体必须加英文状态下的单引号或双引号，例如 *__font-family: "Times New Roman";__*
6. 尽量使用系统默认字体，保证在任何用户的浏览器中都能正确显示。

## CSS Unicode字体
&emsp;&emsp;在CSS中设置字体名称，直接写中文是可以的。但是在文件编码（GB2312、UTF-8 等）不匹配时会产生乱码的错误，并且xp系统不支持类似"微软雅黑"的中文。有下面两种方法来解决：

+ 你可以使用英文来替代，比如：*__font-family:"Microsoft Yahei"__*

+ 在CSS直接使用Unicode编码来写字体名称可以避免这些错误。使用Unicode写中文字体名称，浏览器是可以正确的解析的。*__font-family: "\5FAE\8F6F\96C5\9ED1"__* ，表示设置字体为“微软雅黑”。

&emsp;&emsp;常用的字体编码：

字体名称 | 英文名称 | Unicode 编码
- | - | -
宋体 | SimSun| \5B8B\4F53
新宋体 | NSimSun |\65B0\5B8B\4F53
黑体 |SimHei | \9ED1\4F53
微软雅黑 | Microsoft YaHei | \5FAE\8F6F\96C5\9ED1
楷体_GB2312 | KaiTi_GB2312| \6977\4F53_GB2312
隶书 | LiSu | \96B6\4E66
幼园 | YouYuan| \5E7C\5706
华文细黑 | STXihei | \534E\6587\7EC6\9ED1
细明体  | MingLiU  | \7EC6\660E\4F53
新细明体| PMingLiU | \65B0\7EC6\660E\4F53

> *__注意：__* 为了照顾不同电脑的字体安装问题，我们尽量只使用宋体和微软雅黑中文字体。

# font-weight（字体粗细）
&emsp;&emsp;字体加粗除了用b和strong标签之外，还可以使用CSS来实现，但是CSS是没有语义的。

&emsp;&emsp;font-weight属性用于定义字体的粗细，其可用属性值：normal、bold、bolder、lighter、100~900（100的整数倍）。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>字体粗细</title>
    <style>
        p {
            font-weight: blod;
        }
        span {
            font-weight: 100;
        }
    </style>
</head>
<!-- 03-字体粗细 -->
<body>
    <p>这里是一段文本</p>
    <span>这里是span中的内容</span>
</body>
</html>
```

> *__小技巧：__*数字 400 等价于 normal，而 700 等价于 bold，但是我们更喜欢用数字来表示。

# font-style（字体风格）
&emsp;&emsp;字体倾斜除了用i和em标签之外，可以使用CSS来实现，但是CSS是没有语义的。

&emsp;&emsp;font-style属性用于定义字体风格，如设置斜体、倾斜或正常字体，其可用属性值如下：

+ normal：默认值，浏览器会显示标准的字体样式。

+ italic：浏览器会显示斜体的字体样式。

+ oblique：浏览器会显示倾斜的字体样式。

```html
<!-- 04-字体风格 -->
<body>
    <p style="font-style: italic;">斜体</p>
    <p style="font-style: normal;">正常</p>
    <p style="font-style: oblique;">倾斜</p>
</body>
```

> *__小技巧：__* 平时我们很少给文字加斜体，反而喜欢给斜体标签（em，i）改为普通模式。

# font综合设置字体样式
&esmp;&esmp;font属性用于对字体样式进行综合设置，其基本语法格式如下：

```css
选择器 {font: font-style  font-weight  font-size/line-height  font-family; }
```

> *__注意：__* 
> 1. 使用font属性时，必须按上面语法格式中的顺序书写，不能更换顺序
> 2. 各个属性以空格隔开
> 3. 其中不需要设置的属性可以省略（取默认值），但必须保留font-size和font-family属性，否则font属性将不起作用。

```html
<!-- 05-字体综合设置 -->
<body>
    <!-- 完整版本 -->
    <p 
    style="font: italic 400 10px '微软雅黑';">
    完整的字体综合样式</p>

    <!-- 省略版本 -->
    <p
    style="font: 20px '微软雅黑';">
    省略版本
    </p>
</body>
```