@[toc](CSS基本选择器)

&emsp;&emsp;要想将CSS样式应用于特定的HTML元素，首先需要找到该目标元素。在CSS中，执行这一任务的样式规则部分被称为选择器（选择符）。

# 标签选择器（元素选择器）
&emsp;&emsp;标签选择器是指用HTML标签名称作为选择器，按标签名称分类，为页面中某一类标签指定统一的CSS样式。其基本语法格式如下：

```css
标签名 {属性1:属性值1; 属性2:属性值2; 属性3:属性值3; }

/* 或者 */

元素名{属性1:属性值1; 属性2:属性值2; 属性3:属性值3; }
```

> 标签选择器最大的优点是能快速为页面中同类型的标签统一样式，同时这也是他的缺点，不能设计差异化样式。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>标签选择器</title>
    <style>
        /* 所有的p标签添加 */
        p {
            font-size: 20px;
        }

        /* 为所有的span标签提供样式 */
        span {
            font-style: italic;
        }
    </style>
</head>
<!-- 01-标签选择器 -->
<body>
    <p>这里是一段p标签的内容</p>
    <span>这里是span中的内容</span>
    <p>这里是一段p标签的内容</p>
</body>
</html>
```

# 类选择器
&emsp;&emsp;类选择器使用“.”（英文点号）进行标识，后面紧跟类名，其基本语法格式如下：

```css
.类名 {属性1:属性值1; 属性2:属性值2; 属性3:属性值3; }
```

&emsp;&emsp;标签调用的时候用 *__class=“类名”__*  即可，如：

```html
<p class="类名">...</p>
```

&emsp;&emsp;类选择器最大的优势是可以为元素对象定义单独或相同的样式。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>类选择器</title>
    <style>
        span {
            font-size: 100px;
            font-weight: 200;
        }
        .blue {
            color: blue;
        }
        .red {
            color: red;
        }
        .orange {
            color: orange;
        }
        .green {
            color: green;
        }
    </style>
</head>
<!-- 02-类选择器 -->
<body>
    <span class="blue">G</span>
    <span class="red">o</span>
    <span class="orange">o</span>
    <span class="blue">g</span>
    <span class="green">l</span>
    <span class="red">e</span>
</body>
</html>
```

## 命名规范

1. 长名称或词组可以使用中横线来为选择器命名
2. 不建议使用“_”下划线来命名CSS选择器
3. 不要纯数字、中文等命名，尽量使用英文字母来表示

## 多类名选择器
&emsp;&emsp;我们可以给标签指定多个类名，从而达到更多的选择目的。语法格式如下：

```html
<标签名 class="类名1 类名2 ..."></标签名>
```

1. 样式显示效果跟HTML元素中的类名先后顺序没有关系,受CSS样式书写的上下顺序有关
2. 各个类名中间用空格隔开

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>多类名选择器</title>
    <style>
        .red {
            color: red;
        }
        .blue {
            color: blue;
        }
        .b-font {
            font-size: 16px;
        }
        .s-font {
            font-size: 14px;
        }
    </style>
</head>
<!-- 03-多类名选择器 -->
<body>
    <div class="s-font red">字体大小14px，红色</div>
    <div class="s-font blue">字体大小14px，蓝色</div>
    <div class="b-font red">字体大小16px，红色</div>
</body>
</html>
```

# id选择器
&emsp;&emsp;id选择器使用“#”进行标识，后面紧跟id名，其基本语法格式如下：

```css
#id名{属性1:属性值1; 属性2:属性值2; 属性3:属性值3; }
```

&emsp;&emsp;该语法中，id名即为HTML元素的id属性值，大多数HTML元素都可以定义id属性，元素的id值是唯一的，只能对应于文档中某一个具体的元素。

&emsp;&emsp;id选择器的用法基本和类选择器相同：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>id选择器</title>
    <style>
        #id-select {
            color: red;
            font-size: 20px;
        }
    </style>
</head>
<!-- 04-id选择器 -->
<body>
    <p id="id-select">这是id选择器</p>
</body>
</html>
```

## id选择器和类选择器区别

+ W3C标准规定，在同一个页面内，不允许有相同名字的id对象出现，但是允许相同名字的class
+ 类选择器好比人的名字，是可以多次重复使用的
+ id选择器好比人的身份证号码，不得重复，只能使用一次
+ id选择器和类选择器最大的不同在于使用次数上

# 通配符选择器
&emsp;&emsp;通配符选择器用“*”号表示，他是所有选择器中作用范围最广的，能匹配页面中所有的元素。其基本语法格式如下：

```css
* { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; }
```

&emsp;&emsp;例如下面的代码，使用通配符选择器定义CSS样式，清除所有HTML标记的默认边距。

```css
* {
  margin: 0;                    /* 定义外边距*/
  padding: 0;                   /* 定义内边距*/
}
```

# 伪类选择器
&emsp;&emsp;伪类选择器用于向某些选择器添加特殊的效果，比如给链接添加特殊效果，可以选择第1个、第n个元素。

&emsp;&emsp;类选择器是一个点，比如：*__.demo {}__* 。而伪类用冒号，比如： *__:link{}__*

## 链接伪类选择器

+ :link ： 未访问的链接
+ :visited ：已访问的链接
+ :hover ：鼠标移动到链接上
+ :active ：选定的链接

> *__注意__* 写的时候它们的顺序尽量不要颠倒，按照lvha的顺序。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>伪类选择器</title>
    <style>
        .lk:link{
            font-size: 14px;
            color: gray;
            font-weight: 700;
        }
        .lk:visited {
            font-size: 16px;
            color: orange;
            font-weight: 700;
        }
        .lk:hover {
            font-size: 16px;
            color: red;
            font-weight: 700;
        }
        .lk:active {
            font-size: 16px;
            color: green;
            font-weight: 700;
        }
    </style>
</head>
<!-- 05-伪类选择器 -->
<body>
    <a href="#" class="lk">链接标签</a>
</body>
</html>
```

## 结构(位置)伪类选择器（CSS3)

+ :first-child：选取属于其父元素的首个子元素的指定选择器
+ :last-child：选取属于其父元素的最后一个子元素的指定选择器
+ :nth-child(n)：匹配属于其父元素的第 N 个子元素，不论元素的类型
+ :nth-last-child(n)：选择器匹配属于其元素的第 N 个子元素的每个元素，不论元素的类型，从最后一个子元素开始计数。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>结构伪类选择器</title>
    <style>
        /* 第一个成红色 */
        li:first-child {
            color: red;
        }
        /* 最后一个绿色 */
        li:last-child {
            color: blue;
        }
        /* 第3个变成黄色 */
        li:nth-child(3) {
            color: orange;
        }
        /* 倒数第3个 */
        li:nth-last-child(3){
            color: orchid;
        }
    </style>
</head>
<!-- 05-结构伪类选择器 -->
<body>
    <ul>
        <li>第一行</li>
        <li>第二行</li>
        <li>第三行</li>
        <li>第四行</li>
        <li>第五行</li>
        <li>第六行</li>
    </ul>
</body>
</html>
```

&emsp;&emsp;对于 *__:nth-child(n)__* 和 *__:nth-last-child(n)__* 传递的参数n可以是数字、关键词或公式，下面通过传递关键字和公式的方式实现隔行换色：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>07-结构伪类选择器-隔行</title>
    <style>
        /* 奇数 */
        li:nth-child(odd){
            color: red;
        }
        /* 偶数 */
        li:nth-child(even){
            color: orange;
        }

        /* 也可以使用下面的 */
        /* 奇数 */
        /* li:nth-child(2n+1){
            color: orchid;
        } */
        /* 偶数 */
        /* li:nth-child(2n){
            color: peru;
        } */
    </style>
</head>
<!-- 07-结构伪类选择器-隔行 -->
<body>
    <ul>
        <li>第一行</li>
        <li>第二行</li>
        <li>第三行</li>
        <li>第四行</li>
        <li>第五行</li>
        <li>第六行</li>
    </ul>
</body>
</html>
```

## 目标伪类选择器(CSS3)
&emsp;&emsp;:target目标伪类选择器，该选择器可用于选取当前活动的目标元素。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>目标伪类选择器</title>
    <style>
        :target {
            color: red;
        }
    </style>
</head>
<!-- 08-目标伪类选择器 -->
<body>
    <h2>目录</h2>
    <hr />
    <a href="#1">1 早年经历</a> <br />
    <a href="#2">2 演艺经历</a> <br />
    <a href="#3">3 个人生活</2> <br />
    <a href="#4">4 主要作品</a> <br />
    
    
    <h3 id="1">早年经历</h3>
    <hr />
    刘德华出生于香港新界，在家中排行老四，幼时随家人搬到了九龙钻石山的木屋区居住，并和姐弟一起帮助家里打理卖稀饭的生意[17]  。1973年，刘德华随家人搬入香港蓝田邨第15座14楼[18]  。刘德华从黄大仙天主教小学毕业后升读可立中学[19]  。在可立中学读书期间，刘德华积极参加校内学校剧社的表演，在老师杜国威的指导下学习戏剧方面的知识。此外，他还参与包括编剧在内的幕后制作。刘德华在中五会考获得1B3D2E（中文读本A）的成绩。中六上学期后，他到香港电视广播有限公司的艺员训练班受训，从而开始了演艺之路[20]  。
    
    
    <h3 id="2">演艺经历</h3>
    <hr />
    
    1981年，刘德华考进第10期无线电视艺员训练班[21]  ；同年，出演个人首部电视剧《江湖再见》，在剧中饰演以贩卖妇女为生的小混混阿龙[22]  ；该剧获得美国电视节电视剧特别奖[23]  。
    1982年，刘德华以甲级成绩从艺员训练班毕业后正式签约TVB[24]  ；同年在
    刘德华早期照片
    刘德华早期照片(2张)
     喜剧《花艇小英雄》中饰演败家仔钱日添；12月，与叶德娴搭档主演时装警匪剧《猎鹰》，凭借卧底警察江大伟一角获得关注[25]  。
    1983年，主演金庸武侠剧《神雕侠侣》，在剧中饰演外貌俊俏、倜傥不羁的杨过[26]  ；该剧在香港播出后取得62点的收视纪录；同年，与黄日华、梁朝伟、苗侨伟、汤镇业组成“无线五虎将”[27]  。
    1984年，与赵雅芝合作主演古装武侠剧《魔域桃源》，在剧中饰演资质出众、武功高强的傅青云[28]  ；同年，与梁朝伟共同主演金庸武侠剧《鹿鼎记》，在剧中饰演英明果断的康熙[29]  。
    1985年，在古装武侠剧《杨家将》中饰演饶勇善战的杨六郎[30]  ；同年，TVB向刘德华提出加签五年的合约，刘德华因拒绝而被TVB雪藏400天[31-32]  。1986年，在邵逸夫的调解下，刘德华与TVB和解并签下合约；同年，主演古装剧《真命天子》。1988年，在出演了武侠剧《天狼劫》后，刘德华将演艺事业的重心转向影坛[32]  。
    刘德华
    刘德华
    电影时代
    1981年，刘德华出演电影处女作《彩云曲》，在片中扮演一个音乐班
    刘德华电视剧剧照
    刘德华电视剧剧照(9张)
     的学员[33]  。1982年，在剧情片《投奔怒海》中饰演美军翻译官祖名，并凭借该片获得第2届香港电影金像奖最佳新演员提名[33]  。
    1983年，与张曼玉搭档主演剧情片《家在香港》，在片中饰演急功近利的青年人亚伦[34]  ；同年，主演动作片《毁灭号地车》，在片中与一个越南少女演绎了一段爱情故事[35]  。1984年，在爱情片《停不了的爱》中饰演富家公子Eric[36]  。
    1985年，在与叶德娴共同主演的剧情片《法外情》中饰演少年得志的青年律师刘志鹏[37]  。1986年，主演科幻冒险片《魔翡翠》，在片中饰演冒险专家猎鹰一号，这也是他首度出演科幻题材的电影[38]  ；同年，出演喜剧片《最佳福星》，在片中饰演身手矫健的特警组警员蓝保[39]  。1987年，主演警匪片《肝胆相照》，在片中饰演亦正亦邪的犯罪集团成员阿定[40]  。
    1988年，主演王家卫执导的黑帮片《旺角卡门》，在片中饰演重情重义的江湖混混华仔，并凭借该片获得第8届香港电影金像奖最佳男主角奖提名[41]  ；同年，主演警匪片《猎鹰计划》，在片中饰演具有正义感的警员国华[42]  ；此外，他还再度与叶德娴合作，在剧情片《法内情》中与叶德娴饰演绎了一段母子情[43]  。
    1989年，在动作片《至尊无上》中饰演有“亚洲第一快手”之称的
    刘德华写真
    刘德华写真(4张)
     陈亚蟹[44]  ；同年，主演剧情片《神行太保》，在片中饰演一名公正、能干、勇敢的太保；此外，他还主演了动作片《人海孤鸿》，在片中饰演没有接受过良好教育的古惑仔沙士[45]  ；12月，与周润发共同主演动作片《赌神》，在片中饰演赌神高进的徒弟刀仔[46]  。
    1990年，主演爱情片《天若有情之追梦人》，在片中饰演善良热情、讲义气的黑社会混混华Dee[47]  ；同年，主演剧情片《至尊计状元才》；12月，与周星驰合作主演赌片《赌侠》，在片中饰演身怀绝技的陈刀仔[48]  。
    1991年，刘德华开始改变银幕形象，主演了传记题材的系列电影《五亿探长雷洛传》，并在片中首次诠释年龄跨度较大的人物，该系列中的两部作品《五亿探长雷洛传I雷老虎》、《五亿探长雷洛传2:父子情仇》在香港的累积票房达到5300万[49]  ；6月，主演犯罪题材的电影《至尊无上Ⅱ之永霸天下》；此外，他还主演了动作片《九一神雕侠侣》，该片是刘德华投资出品的首部电影作品[50]  。
    1992年，凭借传记片《五亿探长雷洛传》获得第11届香港电影金像奖最佳男主角提名[51]  ；8月，与王祖贤、叶德娴合作出演剧情片《庙街十二少》；11月，与林青霞、叶德娴共同主演古装片《绝代双骄》，在片中饰演聪明绝顶的小鱼儿[52]  ；同年，主演爱情片《九二神雕侠侣之痴心情长剑》，在片中饰演痴情大侠情仁[53]  。
    1993年，在古装片《战神传说》中扮演一个武功超群的渔民[54]  ；同年，主
    
    
    <h3 id="3">个人生活</h3>
    <hr />
    
    刘德华的父亲刘礼在启德机场做过消防员的工作。20世纪60年代，刘礼开了一间小吃杂货店以赚钱维持家用。刘德华在家中还有三位姐姐，一位妹妹以及一位弟弟（刘德盛）[158]  。
    感情
    1986年，刘德华随香港明星足球队赴吉隆坡时，结识了朱丽倩。2008年6月23日，刘德华与朱丽倩在美国拉斯维加斯注册结婚[159]  。2012年5月9日，刘德华的妻子朱丽倩生下一个女儿。[160-161]  2016年3月，刘德华的妻子朱丽倩怀上第2胎。[162] 
    
    
    <h3 id="4">主要作品</h3>
    <hr />
    参演电影
     
    侠盗联盟2017-07
    导演冯德伦 主演让-雷诺, 舒淇
     
    拆弹专家2017
    饰演拆弹专家 导演邱礼涛 主演姜武, 小宋佳,
    黄宗泽
     
    长城2016-12-18
    饰演宋朝将军 导演张艺谋 主演马特·达蒙, 景甜, 张涵予
    
</body>
</html>
```