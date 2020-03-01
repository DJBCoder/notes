@[toc](HTML5新标签与特性)

# 文档类型设定

```htlm
<!DOCTYPE html>
```

# 字符设定

```html
<!-- HTML与XHTML中建议这样去写 -->
<meta http-equiv="charset" content="utf-8">

<!-- HTML5的标签中建议这样去写 -->
<meta charset="utf-8">
```

# 常用新标签

- header：定义文档的页眉 头部
- nav：定义导航链接的部分
- footer：定义文档或节的页脚 底部
- article：定义文章。
- section：定义文档中的节（section、区段）
- aside：定义其所处内容之外的内容 侧边

```html
<!-- 01-常用标签 -->
<body>
    <header>语义：定义页面的头部、页眉</header>
    <nav>语义：定义导航栏</nav>
    <footer>语义：定义页面底部、页脚</footer>
    <article>语义：定义文章</article>
    <section>语义：定义区域（文章中的节）</section>
    <aside>语义：侧边（定义其所处内容之外的内容）</aside>
</body>
```

- datalist：标签定义选项列表。请与 input 元素配合使用该元素

```html
<!-- 02-datalist -->
<body>
    <input type="text" value="选择你喜欢的运动"
    list="sports">
    <datalist id="sports">
        <option>篮球</option>
        <option>足球</option>
    </datalist>
</body>
```

- fieldset：该元素可将表单内的相关元素分组，打包，与legend搭配使用

```html
<!-- 03-fieldset -->
<body>
    <fieldset>
        <legend>用户登陆</legend>
        用户名：<input type="text"><br>
        密&nbsp;码：<input type="password">
    </fieldset>
</body>
```

# 新增的input type属性值

 类型       | 使用示例            | 含义 
-| - | - | - 
 email    | &lt;input type="email"&gt;| 输入邮箱格式     
 tel      | &lt;input type="tel"&gt;| 输入手机号码格式   
 url      | &lt;input type="url"&gt;| 输入url格式    
 number   | &lt;input type="number"&gt;| 输入数字格式     
 search   | &lt;input type="search"&gt;| 搜索框（体现语义化） 
 range    | &lt;input type="range"&gt;7| 自由拖动滑块     
 time     | &lt;input type="time"&gt;| 小时分钟       
 date     | &lt;input type="date"&gt;| 年月日        
 datetime | &lt;input type="datetime"&gt;| 时间         
 month    | &lt;input type="month"&gt;| 月年         
 week     | &lt;input type="week"&gt;| 星期 年   
color     | &lt;input type="color"&gt;| 选择颜色 

```html
<!-- 04-新增type属性类型 -->
<body>
    <fieldset>
        <legend>HTML5新增type类型</legend>
        <form action="#">
            email：<input type="email"><br>
            tel：<input type="tel"><br>
            url：<input type="url"><br>
            number：<input type="number"><br>
            search：<input type="search"><br>
            range：<input type="range"><br>
            time：<input type="time"><br>
            datetime：<input type="datetime"><br>
            date：<input type="date"><br>
            month：<input type="month"><br>
            week：<input type="week"><br>
            color：<input type="color"><br>
            <input type="submit" value="提交">
        </form>
    </fieldset>
</body>
```

> 在手机端的显示效果更为明显，比如：type为number的时候，手机上会弹出数字键盘

# 常用新属性

 属性 | 用法 | 含义 
 -|-|- 
placeholder  | &lt;input type="text" placeholder="请输入用户名"&gt;|占位符当用户输入的时候里面的文字消失，删除所有文字自动返回提示信息
autofocus    | &lt;input type="text" autofocus&gt;| 规定当页面加载时input元素应该自动获得焦点
multiple     |&lt;input type="file" multiple&gt;| 多文件上传
autocomplete|&lt;input type="text" autocomplete="off"&gt;| 规定表单是否应该启用自动完成功能，有2个值：on、off。on代表记录已经输入的值 <br> 1.autocomplete 首先需要提交按钮 <br/>2.这个表单必须给他名字（name属性）
required     | &lt;input type="text" required&gt; | 必填项内容不能为空
accesskey    | &lt;input type="text" accesskey="s"&gt; | 规定激活（使元素获得焦点）元素的快捷键   采用 alt + s的形式

```html
<!-- 05-新增属性 -->
<body>
    <form action="#">
        <!-- placeholder 占位符 -->
        <!-- autofocus 自动获取焦点 -->
        <!-- autocomplete自动完成 -->
        <!-- required 必须填 -->
        用户名：<input type="text" 
        placeholder="请输入你的用户名"
        autofocus
        autocomplete="on"
        required name="username"> <br>

        <!-- 快捷键获取焦点  alt + s-->
        姓名：<input type="text" accesskey="s"><br>

        <!-- 多文件上传 -->
        文件上传：<input type="file" multiple><br>
        <input type="submit" value="提交">
    </form>
</body>
```

# 多媒体标签

- embed：标签定义嵌入的内容
- audio：播放音频
- video：播放视频

## 多媒体embed
&emsp;&emsp;embed可以用来插入各种多媒体，格式可以是 Midi、Wav、AIFF、AU、MP3等等。url为音频或视频文件及其路径，可以是相对路径或绝对路径。

> *__注意：__* 因为兼容性问题，这里只演示插入网络视频，后面H5会用 audio 和video 视频多媒体。 

1. 将视频上传到优酷、土豆等网页，或者直接找一个视频
2. 打开视频，点击分享，然后复制html的分享
3. 粘贴到自己的网页中

```html
<!-- 06-embend -->
<body>
    <embed src="//player.video.iqiyi.com/0a428688c3d38aed4630240961646a29/0/0/v_19rxjk5zus.swf-albumId=13397439400-tvId=13397439400-isPurchase=0-cnId=undefined" 
    allowFullScreen="true" 
    quality="high" 
    width="480" 
    height="350" 
    align="middle" 
    allowScriptAccess="always" 
    type="application/x-shockwave-flash">
    </embed>
</body>
```

## 多媒体 audio
&emsp;&emsp;HTML5通过&lt;audio&gt;标签来解决音频播放的问题。使用相当简单，如下所示:

```html
<audio src="路径"></audio>
```

&emsp;&emsp;并且可以通过附加属性可以更友好控制音频的播放，如：

+ autoplay：自动播放
+ controls：是否显不默认播放控件
+ loop：循环播放，"loop = 2" 就是循环2次，"loop" 或者"loop = -1"是无限循环

&emsp;&emsp;由于版权等原因，不同的浏览器可支持播放的格式是不一样的，多浏览器支持的方案如下：

```html
<!-- 07-audio -->
<body>
    <audio controls autoplay loop="-1">
        <source src="./assets/bgsound.mp3">
        <source src="./assets/music.ogg">
        您的浏览器不支持HTML音频播放功能
      </audio>
</body>
```

&emsp;&emsp;浏览器会依次读取source的文件，直到浏览器支持为止，如果都不支持，则显示最下面的提示文字。

## 多媒体 video

&emsp;&emsp;HTML5通过&lt;audio&gt;标签来解决音频播放的问题。同音频播放一样，&lt;video&gt;使用也相当简单，如下:

```html
<video src="./movie.mp4" controls="controls"></video>
```

&emsp;&emsp;同样，通过附加属性可以更友好的控制视频的播放：

+ autoplay：自动播放
+ controls：是否显示默认播放控件
+ loop：循环播放
+ width：设置播放窗口宽度
+ height：设置播放窗口的高度

&emsp;&emsp;由于版权等原因，不同的浏览器可支持播放的格式是不一样的，多浏览器支持的方案，如下：

```html
<video>
<source src="./movie.ogg">
<source src="./movie.mp4">
您的浏览器不支持HTML视频的播放
</video>
```
