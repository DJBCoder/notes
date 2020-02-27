@[toc](02-Html基础知识)

# Html初识
&emsp;&emsp;HTML（英文Hyper Text Markup Language的缩写）中文译为“超文本标签语言”，主要是通过HTML标签对网页中的文本、图片、声音等内容进行描述。

## HTML基本框架

```html
<html>
<head>
  <title></title>
</head>
<body>

</body>
</html>
```

1. html标签：所有HTML中标签的一个根节点。
2. head标签：用于存放title、meta、base、style、script、link标签。（*__注意：在head标签中我们必须要设置的标签是title__*）
3. title标签：让页面拥有一个属于自己的标题。
4. body标签：页面在的主体部分，用于存放所有的HTML标签。

# HTML标签
## HTML标签分类
&emsp;&emsp;在HTML页面中，带有"< >"符号的元素被称为HTML标签，如上面提到的&lt;html&gt;、&lt;head&gt;、&lt;body&gt;都是HTML标签。所谓标签就是放在"< >"标签符中表示某个功能的编码命令，也称为HTML标签或HTML元素。

1. 双标签

```html
<标签名> 内容 </标签名>
```

&emsp;&emsp;该语法中"<标签名>"表示该标签的作用开始，一般称为"开始标签（start tag）"，"</标签名>"表示该标签的作用结束，一般称为"结束标签（end tag）"，和开始标签相比，结束标签只是在前面加了一个关闭符"/"。比如：

```html
<p>我是文字</p>
```

2. 单标签

```html
<标签名 />
```

&emsp;&emsp;单标签也称空标签，是指用一个标签符号即可完整地描述某个功能的标签。比如：

```html
<br />
```

## HTML标签关系
&emsp;&emsp;标签的相互关系就分为两种：

1. 嵌套关系

```html
<head>
  <title> </title>  
</head>
```


2. 并列关系

```html
<head></head>
<body></body>
```

> *__如果两个标签之间的关系是嵌套关系，子元素最好缩进一个tab键的身位。如果是并列关系，最好上下对齐。__*

## HTML标签的语义化

&emsp;&emsp;所谓标签语义化，就是指标签的含义。

### 为什么要有语义化标签

1. 方便代码的阅读和维护
2. 同时让浏览器或是网络爬虫可以很好地解析，从而更好分析其中的内容 
3. 使用语义化标签会具有更好地搜索引擎优化 

# 文档类型<!DOCTYPE>

```html
<!DOCTYPE html>
```

&emsp;&emsp;这句话就是告诉我们使用的是 *HTML5* 的版本，html有很多版本，那我们应该告诉用户和浏览器我们使用的版本号。

&emsp;&emsp; *__&lt;!DOCTYPE&gt;__* 标签位于文档的最前面，用于向浏览器说明当前文档使用哪种HTML或XHTML标准规范，必需在开头处使用 *__&lt;!DOCTYPE&gt;__* 标签为所有的XHTML文档指定XHTML版本和类型，只有这样浏览器才能按指定的文档类型进行解析。

# 字符集

```html
<meta charset="UTF-8">
```

&emsp;&emsp;utf-8是目前最常用的字符集编码方式，常用的字符集编码方式还有gbk和gb2312：

+ gb2312：简单中文，包括6763个汉字
+ BIG5：繁体中文，港澳台等用
+ GBK：包含全部中文字符，是GB2312的扩展，加入对繁体字的支持，兼容GB2312
+ UTF-8：包含全世界所有国家需要用到的字符

> *__以后我们统统使用UTF-8字符集, 这样就避免出现字符集不统一而引起乱码的情况了。__*

