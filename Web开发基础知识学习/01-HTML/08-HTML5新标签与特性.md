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
  <header> 语义 :定义页面的头部  页眉</header>
  <nav>  语义 :定义导航栏 </nav> 
  <footer> 语义: 定义 页面底部 页脚</footer>
  <article> 语义:  定义文章</article>
  <section> 语义： 定义区域</section>
  <aside> 语义： 定义其所处内容之外的内容 侧边</aside>
```

- datalist：标签定义选项列表。请与 input 元素配合使用该元素

```html
  <input type="text" value="输入明星" list="star"/> <!--  input里面用 list -->
  <datalist id="star">   <!-- datalist 里面用 id  来实现和 input 链接 -->  
      		<option>刘德华</option>
      		<option>刘若英</option>
      		<option>刘晓庆</option>
      		<option>郭富城</option>
      		<option>张学友</option>
      		<option>郭郭</option>
  </datalist>
```

- fieldset：该元素可将表单内的相关元素分组，打包，与legend搭配使用

```html
  <fieldset>
      		<legend>用户登录</legend>  标题
      		用户名: <input type="text"><br /><br />
      		密　码: <input type="password">
  </fieldset>
```

# 新增的input type属性值

 类型       | 使用示例            | 含义 
-| - | - | - 
 email    | <input type="email">    | 输入邮箱格式     
 tel      | <input type="tel">      | 输入手机号码格式   
 url      | <input type="url">      | 输入url格式    
 number   | <input type="number">   | 输入数字格式     
 search   | <input type="search">   | 搜索框（体现语义化） 
 range    | <input type="range">    | 自由拖动滑块     
 time     | <input type="time">     | 小时分钟       
 date     | <input type="date">     | 年月日        
 datetime | <input type="datetime"> | 时间         
 month    | <input type="month">    | 月年         
 week     | <input type="week">     | 星期 年       


# 常用新属性

 属性           | 用法 | 含义 
 - | - | - 
placeholder  | <input type="text" placeholder="请输入用户名"> |占位符当用户输入的时候 里面的文字消失 删除所有文字，自动返回       
autofocus    | <input type="text" autofocus>            | 规定当页面加载时 input 元素应该自动获得焦点                
multiple     | <input type="file" multiple>             | 多文件上传                                    
autocomplete | <input type="text" autocomplete="off">   | 规定表单是否应该启用自动完成功能  有2个值，一个是on 一个是off      on 代表记录已经输入的值  1.autocomplete 首先需要提交按钮 <br/>2.这个表单您必须给他名字 
required     | <input type="text" required>             | 必填项  内容不能为空                              
accesskey    | <input type="text" accesskey="s">        | 规定激活（使元素获得焦点）元素的快捷键   采用 alt + s的形式      

# 多媒体标签

- embed：标签定义嵌入的内容

- audio：播放音频

- video：播放视频


## 多媒体embed
&emsp;&emsp;embed可以用来插入各种多媒体，格式可以是 Midi、Wav、AIFF、AU、MP3等等。url为音频或视频文件及其路径，可以是相对路径或绝对路径。

&emsp;&emsp;因为兼容性问题，我们这里只讲解 插入网络视频， 后面H5会讲解 audio 和video 视频多媒体。 

```html
<embed src="http://player.youku.com/player.php/sid/XMTI4MzM2MDIwOA==/v.swf" allowFullScreen="true" quality="high" width="480" height="400" align="middle" allowScriptAccess="always" type="application/x-shockwave-flash"></embed>
```

## 多媒体 audio

HTML5通过&lt;audio&gt;标签来解决音频播放的问题。使用相当简单，如下所示:

```html
<audio src="路径">
```