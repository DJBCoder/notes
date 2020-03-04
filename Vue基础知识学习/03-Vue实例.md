# 创建一个Vue实例
&emsp;&emsp;每个Vue应用都是通过用Vue函数创建一个新的Vue实例开始的：

```javascript
let vm = new Vue({
    // 选项
})
```

&emsp;&emsp;当创建一个Vue实例的时候，你可以传入一个选项对象，一个Vue应由一个通过new Vue创建的根Vue实例，以及可选的嵌套的、可复用的组件树组成。

# 基础选项
## el选项
&emsp;&emsp;该选项提供了一个页面上已经存在的DOM元素作为Vue实例的挂载目标，可以是CSS选择器，也可以是一个HTML Element实例，在实例挂载之后，元素可以用vm.$el来访问。

```html
<!-- 01-el选项的使用 -->
<body>
    <div id="app">

    </div>
    <script src="./node_modules/vue/dist/vue.js"></script>
    <script>
        let vm = new Vue({
            el: '#app',// 这里使用的是选择器
            // 也可以使用下面的方法
            // el: document.getElementById('app')
        })
    </script>
</body>
```

> *__注意：__*
> 1. 提供的元素只能作为挂载点，所有的挂载元素会被Vue生成的DOM替换，因此不能挂载root实例到html标签或者body标签
> 2. 如果render函数和template属性都不存在，挂载DOM元素的HTML会被提取出来用作模板，此时必须使用Runtime + Compiler构建的Vue库
> 3. 只在用new创建实例时生效

&emsp;&emsp;如果在实例化的时候存在这个选项，实例将立即进入编译过程，否则需要显式调用vm.$mount()手动开启编译。

```html
<!-- 02-使用mount挂载 -->
<body>
    <div id="app"></div>
    <script src="./node_modules/vue/dist/vue.js"></script>
    <script>
        new Vue({

        }).$mount('#app') // 使用该方法就不需要指定el选项
    </script>
</body>
```

## template选项
&emsp;&emsp;使用一个字符串模板作为Vue实例的标识使用，模板将会替换挂载的元素，挂载元素的内容都将被忽略，除非模板的内容有分发插槽。

```html
<body>
  <div id="app">
    <!-- 这里的内容将会被模板中的内容替换
      （除非模板中使用了插槽） -->
    <h1>这是模板外的内容</h1>
  </div>
  <script src="./node_modules/vue/dist/vue.min.js"></script>
  <script>
    new Vue({
      template: 
      `
        <div><h2>这是模板里面的内容</h2></div>
      `
    }).$mount('#app')
  </script>
</body>
```

&emsp;&emsp;如果值以 # 开始，则它将被用作选择符，并使用匹配元素的innerHTML作为模板，常用的技巧是用"&lt;script type='x-template'&gt;"包含模板。

```html
<body>
  <div id="app">
    <!-- 这里的内容将会被模板中的内容替换
      （除非模板中使用了插槽） -->
    <h1>这是模板外的内容</h1>
  </div>
  <!-- 定义模板，并指定id -->
  <script type="x-template" id="t">
    <div>
      <h2>这是模板里面的内容</h2>
    </div>
  </script>
  <script src="./node_modules/vue/dist/vue.min.js"></script>
  <script>
    new Vue({
      // 通过选择器指定模板对象
      template: '#t'
    }).$mount('#app')
  </script>
</body>
```

> *__注意：__*
> 1. 出于安全考虑，你应该使用你信任的Vue模板，避免使用其他人生成的内容作为你的模板
> 2. 如果Vue选项中包含渲染函数，该模板将会被忽略

## render选项
&emsp;&emsp;render选项作为字符串模板的替代方案，允许你发挥JavaScript最大的编程能力，该渲染函数接收一个createElement方法作为第一个参数用来创建VNode。

&emsp;&emsp;如果组件是一个函数组件，渲染函数还会接收一个额外的context参数，为没有实例的函数组件提供上下文信息。

```html
<!-- 04-render选项 -->
<body>
    <div id="app"></div>
    <script src="./node_modules/vue/dist/vue.js"></script>
    <script>
        const renderObject = {
            template: `
                <div>
                    <h1>这是模板中的内容</h1>
                </div>
            `
        }
        new Vue({
            render: h => h(renderObject)
        }).$mount('#app')
    </script>
</body>
```

> *__注意：__* Vue选项中的render函数若存在，则Vue构造函数不会从template选项或者通过el选项指定的挂载元素中提取出的HTML模板编译渲染函数。

## renderError选项
&emsp;&emsp;当render函数遭遇错误的时候，提供了另外一种渲染输出，其错误将作为第二个参数传递到renderError，这个功能配合hot-reload非常实用。

```html
<!-- 05-render选项 -->
<body>
    <div id="app"></div>
    <script src="./node_modules/vue/dist/vue.js"></script>
    <script>
        new Vue({
            render: h => {
                throw new Error('渲染错误')
            },
            renderError(h, err) {
                return h(
                    'pre',
                    {
                        style: {color: 'red'}
                    },
                    err.stack
                )
            },
        }).$mount('#app')
    </script>
</body>
```

> *__注意：__* 只在开发者环境下工作

## data选项
&emsp;&emsp;当一个Vue实例被创建的时候，它将data对象中的所有的属性加入到Vue的响应式系统中，当这些属性的值发生改变的时候，视图将会产生响应，即匹配更新的值。

```html
<!-- 06-data选项1 -->
<body>
    <div id="app">
        number = {{ number }}
    </div>
    <script src="./node_modules/vue/dist/vue.js"></script>
    <script>
        let data = {
            number : 1
        }
        let app = new Vue({
            data    
        }).$mount('#app')

        console.log(app.number === data.number) // true

        app.number = 2
        console.log(data.number)// 2 此时界面也是2

        data.number = 3
        console.log(app.number)// 3 此时界面也是3
    </script>
</body>
```

&emsp;&emsp;当这些数据改变时，视图会进行重新渲染，值得注意的是只有当实例被创建时就已经存在于data中的属性才是响应式的，也就是后面新添加的属性不是，如：

```html
<!-- 07-data选项2 -->
<body>
    <div id="app">
        a = {{ a }}
        b = {{ b }}
    </div>
    <script src="./node_modules/vue/dist/vue.js"></script>
    <script>
        let data = {
            a : 1
        }
        let app = new Vue({
            data
        }).$mount('#app')

        app.b = 2   //  界面不会显示b =2 依然是b = 
    </script>
</body>
```

&emsp;&emsp;如果你知道你会在晚些时候需要一个属性，但是一开始它为空或者不存在，那么你仅需要设置一些初始值，如：

```javascript
data : {
    stringDefault: '',
    numberDefault: 0,
    booleanDefault: false,
    arrayDefault: [],
    objectDefault: null
}
```

&emsp;&emsp;这里的唯一的例外是使用Object.freeze()，这会阻止修改现有的属性，也意味着响应系统无法再追踪变化。

```javascript
let obj = {
    foo: 'bar'
}

Object.freeze(obj)

new Vue({
    data: obj
}).$mount('#app')
```

&emsp;&emsp;除了数据属性，Vue实例还暴露了一些有用的实例属性与方法，它们都有前缀"$"，以便与用户定义的属性区分开来，例如：

```html
<!-- 08-实例属性与方法 -->
<body>
    <div id="app">
        number = {{ number }}
    </div>
    <script src="./node_modules/vue/dist/vue.js"></script>
    <script>
        let data = {
            number : 1
        }
        let app = new Vue({
            data
        }).$mount('#app')  

        console.log(app.$data === data)// true
        console.log(app.$el === document.getElementById('app')) // true

        // 实例方法$watch 检测数据的变化
        app.$watch('number', (newValue, oldValue) => {
            console.log(newValue, oldValue)
        })

        app.number = 2 // 2 1
    </script>
</body>
```

