## Vue

### SpringMVC

#### js

- 函数: 闭包()()
- Dom
	- id, name, tag
	- create, remove
- Bom
	- window
	- document

#### Java全栈工程师

- 后端开发: 主打
- 前端: html、css、js、JQuery;
- 运维: 项目发布; 服务器如何运行一个项目? Linux;

### Vue: 前端体系、前后端分离

#### 概述

Vue是一套用于构建用户页面的渐进式框架, 被设计为可以自底向上逐层应用. Vue的核心库只关注视图层, 不仅易于上手, 还便于与第三方库(如;vue-router: 跳转, vue-resource: 通信, vuex: 管理)或既有项目整合.

网络通信: axios

页面跳转: vue-router  

页面管理: vuex

Vue-UI: ICE

飞冰: 基于React的渐进式研发框架(https://ice.work/docs/guide/start/)

官网: https://cn.vuejs.org/v2/guide/

#### 前端知识体系

想要成为真正的“互联网Java全栈工程师”还有很长的一段路要走, 其中“我大前端”是绕不开的一门必修课. 本阶段课程的主要目的就是带领我Java后台程序猿认识前端、了解前端、掌握前端, 为实现成为“互联网Java全栈工程师”再向前迈进一步

##### 前端三要素

- HTML(结构): 超文本标记语言, 决定网页的结构和内容
- CSS(表现): 层叠样式表, 设计网页的表现样式
- Javascript(行为): 是一种弱类型脚本语言, 其源代码不需要经过编译, 而是由浏览器解释运行, 用于控制网页的行为

##### 结构层(HTML)

##### 表现层(CSS)

CSS层叠样式表是一门标记语言, 并不是编程语言, 因此不可以自定义变量, 不可以引用等, 换句话说就是不具备任何语法支持, 它主要缺陷如下:

- 语法不够强大, 比如无法嵌套书写, 导致模块化开发中需要书写很多重复的选择器
- 没有变量和合理的样式复用机制, 使得逻辑上相关的属性值必须以字面量的形式重复输出, 导致难以维护

这就导致我们在工作中无端增加了许多工作量. 为了解决这个问题, 前端开发人员会使用一种称为 **CSS预处理器** 工具, 提供CSS缺失的样式层复用机制, 减少冗余代码, 提高样式代码的可维护性, 大大提高了前端在样式上的开发效率

##### 什么是CSS预处理器

CSS预处理器定义了一种新的语言, 其基本思想是: 用一种专门的编程语言, 为CSS增加了一些编程的特性, 将CSS作为目标生成文件, 然后开发者就只要使用这种语言进行CSS的编码工作. 转化成通俗易懂的话来说:“用一种专门的编程语言, 进行Web页面样式设计, 再通过编译器转化为正常的CSS文件, 以供项目使用

- SASS: 基于Ruby, 通过服务端处理, 功能强大. 解析效率高. (https://www.sass.hk/)
- LESS: 基于NodeJS, 通过客户端处理, 使用简单.(https://less.bootcss.com/)

##### 行为层

Javascript一门弱类型脚本语言, 其源代码在发往客户端运行之前不需要经过编译, 而是将文本格式的字符代码发送给浏览器由浏览器解释运行

###### Native原生JS开发

原生JS开发, 也就是让我们按照[ECMAScript]标准的开发方式, 简称ES, 特点是所有浏览器都支持.

- ES3
- ES4(内部, 未正式发布)
- ES5(全浏览器支持)
- ES6(常用, 当前主流阶段: webpack打包成为ES5支持)
- ES7
- ES8
- ES9(草案阶段)

##### JavaScript框架

- JQuery: 简化了DOM操作, 缺点就是DOM操作太频繁, 影响前端性能, 在前端眼里就是为了兼容IE6、7、8
- Angular: Google收购的前端框架, 由一群Java程序员开发, 其特点是将后台的MVC模式搬到了前端并增加了模块化开发的理念, 与微软合作, 采用Typescript语法开发, 对后台程序猿友好, 对前端程序员不太友好.
- React: Facebook出品, 高性能JS前端框架, 特点是提出了新概念[虚拟DOM]用于减少真实DOM操作, 在内容中模拟DOM操作, 有效的提升了前端渲染效率. 缺点是使用复杂, 因为需要额外学习[JSX]语言
- Vue: 一款渐进式javascript框架, 所谓渐进式就是逐步实现新特性的意思, 比如实现模块化开发、路由、状态管理等新特性. 综合了Angular(模块化)和React(虚拟Dom)的优点
- Axios: 前端通信框架, 因为Vue的边界很明确, 就是为了处理DOM, 所以并不具备通信能力, 此时就需要额外使用一个通信框架与服务器交互, 当然也可以直接使用JQuery提供的AJAX通行功能

##### UI框架

- Ant-Design: 基于React的UI框架
- ElementUI: 基于Vue的UI框架
- Bootstrap: 前端开发开源工具包
- AmazeUI: HTML5跨屏前端框架

##### JavaScript构建工具

- Babel: JS编译工具, 主要用于浏览器不支持的ES新特性, 比如用于编译TypeScript
- WebPack: 模块打包器, 主要作用是打包、压缩、合并及按序加载

#### 三端统一

##### 混合开发(Hybrid App)

主要目的是实现一套代码三端统一(PC、Android: .apk、IOS: .ipa)并能够调用到设备底层硬件(如: 传感器、GPS、摄像头等), 打包方式主要有以下两种:

- 云打包: HBuild -> HBuildX. DCloud出品、API Cloud
- 本地打包: Cordova(前身是PhoneGap)

#### 微信小程序

#### 后端技术

前端为了方便开发也需要掌握一定的后端技术, 但我们Java后端人员也知道后台知识体系极其庞大复杂, 所以出现了NodeJS

NodeJS框架及项目管理工具(下一代为Deno)

- Express: NodeJS框架
- Koa: Express简化版
- NPM: 项目综合管理工具, 类似于Maven
- YARN: NPM的替代方案, 类似于Maven和Gradle的关系

#### 主流前端框架

Vue.js

##### iView

iview是一个强大的基于Vue的UI库, 有很多实用的基础组件比elementui的组件更丰富, 主要服务于PC界面的中后台产品. 使用单文件的Vue组件化开发模式, 基于npm+webpack+babel开发, 支持ES2015高质量, 功能丰富友好的API, 自由灵活的使用空间

- 官网地址(http://v1.iviewui.com/)
- Github
- iview-admin

##### ElementUI

ElementUI是饿了么前端开源维护的VueUI组件库, 组件齐全, 基本涵盖后台所需的所有组件, 文档讲解详细, 主要用于开发Pc端的页面, 是一个质量比较高的VueUI组件库

- 官网地址(https://element.eleme.cn/#/zh-CN)
- Github
- vue-element-admin

##### ICE

- 官网地址(https://ice.work/docs/guide/start/)
- Github

##### VantUI

VantUI是有赞前端团队基于有赞统一的规范实现的Vu额组件库, 提供了一整套UI基础组件和业务组件. 通过Vant, 可以快速搭建出风格一致的页面, 提升开发效率

- 官网地址
- GitHub(https://gitee.com/vant-contrib/vant)

##### AtUI

At-ui是一款基于Vue2.x的前端UI组件库, 主要用于快速开发PC网站产品, 它提供了一套npm+webpack+babel前端开发工作流程, CSS样式独立, 即使采用不同的框架实现都可以保持统一的UI风格

- 官网地址
- Github

##### CubeUI

cube-ui是滴滴团队开发的基于Vue.js实现的精致移动端组件库. 支持按需引入和后编译, 轻量灵活; 扩展性强, 可以方便的基于现有组件实现二次开发

- 官网地址
- Github

##### Flutter

Flutter 是谷歌的移动端UI框架, 可在极短的时间内构建Android和iOS上高质量的原生级应用, Flutter 可与现有代码一起工作, 他被世界各地的开发者和组织使用, 并且Flutter是免费和开源的

- 官网地址
- GitHub

##### lonic

lonic既是一个CSS框架也是一个JavaScriptUI库, lonic是目前最有潜力的一款HTML5手机应用开发框架. 通过SASS构建应用程序, 它提供了很多UI组件来帮助开发者开发强大的应用. 提供数据的双向绑定, 使用它成为Web和移动开发者的共同选择

- 官网地址
- Github
- 官网文档

##### mpvue

mpvue是美团开发的一个使用Vue.js开发小程序的前端框架, 目前支持微信小程序、百度智能小程序、头条小程序和支付宝小程序.框架基于Vue.js, 修改了的运行时框架runtime和代码编译器compiler实现, 使其可运行在小程序环境中, 从而为小程序开发引入了Vue.js开发体验

- 官方地址
- Github

##### WeUI

是一套同微信原生视觉体验一致的基础样式库, 有微信官方设计团队为微信内网页和微信小程序量身设计, 令用户的使用感知更加统一. 包含`button`、`cell`、`dialog`、`toast`、`article`、`icon`等各式元素

- 官方地址
- `GitHub`

#### 前端为主的MV*时代

- `MVC`(同步通信为主): `Model、View、Controller`
- `MVP`(异步通信为主): `Model、View、Presenter`
- `MVVM`(异步通信为主): `Model、View、ViewModel`

### 第一个Vue程序

#### IDE

- `VSCode`
- `HBuilderX`
- `Sublime`
- `WebStorm`
- `IDEA Intellij`

#### Vue常用7个属性

- `el`属性: 用来指示`vue`编译器从什么地方开始解析`vue`的语法, 可以说是一个占位符
- `data`属性: 用来组织从`view`中抽象出来的属性, 可以说将视图的数据抽象出来存放在`data`中
- `template`属性: 用来设置模版, 会替换页面元素,  包括占位符
- `methods`属性: 放置页面中的业务逻辑, `js`方法一般都放置在`methods`中
- `render`属性: 创建真正的`Virtual Dom`
- `computed`属性: 用来计算
- `watch`属性
	- `watch:function(new, old){}`
	- 监听`data`中数据的变化
	- 两个参数, 一个返回新值, 一个返回旧值

#### 下载地址

- 开发版本
	- 包含完整的警告和调试模式: https://vuejs.org/js/vue.js
	- 删除了警告: https://vuejs.org/js/vue.min.js
- CDN
	- `<script src="https://cdn.jsdeliver.net/npm/vue@2.5.21/dist/vue.js"></script>`
	- `<script src="https://cdn.jsdeliver.net/npm/vue@2.5.21/dist/vue.min.js"></script>`

#### MVVM

`MVVM`(`Model-View-ViewModel`)是一种软件架构设计模式, 由微软WPF(用于替代`WinForm`, 以前就是用这个技术开发桌面应用程序的)和`Silverlight`(类似于`Java Applet`, 简单点说就是在浏览器上运行的`WPF`)的架构师`Ken Cooper`和`Ted Peters`开发, 是一种简化用户界面的用户驱动编程方式.

`MVVM`源自于经典的`MVC`模式. 核心是`ViewModel`层, 负责转换`Model`中的数据对象来让数据变得更容易管理和使用

- 该层向上与视图层进行双向数据绑定
- 向下与`Model`层通过接口请求进行数据交互

##### 为什么使用MVVM

`MVVM`模式和`MVC`模式一样, 主要目的是分离视图(`View`)和模型(`Model`), 特点

- 低耦合: 视图(`view`)可以独立于`Model`变化和修改, 一个`ViewModel`可以绑定到不同的`View`上, 当`View`变化的时候`Model`可以不变, 当`Model`变化时`View`也可以不变
- 可复用: 你可以把一些视图逻辑放在一个`ViewModel`里面,让很多`View`重用这段视图逻辑
- 独立开发: 开发人员可以专注于业务逻辑和数据的开发(`ViewModel`), 设计人员可以专注于页面设计
- 可测试: 界面素来是比较难于测试的, 而现在测试可以针对`ViewModel`来写

#### 注意事项

- `Vue`不支持`IE8`及以下版本, 因为`Vue`使用了`IE8`无法模拟的`ECMAScript5`特性. 但他支持所有兼容`ECMAScript5`的浏览器

###  Vue基础语法

#### v-bind

- **缩写**：`:`

- **预期**：`any (with argument) | Object (without argument)`

- **参数**：`attrOrProp (optional)`

- **修饰符**：

	- `.prop` - 作为一个 DOM property 绑定而不是作为 attribute 绑定。([差别在哪里？](https://stackoverflow.com/questions/6003819/properties-and-attributes-in-html#answer-6004028))
	- `.camel` - (2.1.0+) 将 kebab-case attribute 名转换为 camelCase。(从 2.1.0 开始支持)
	- `.sync` (2.3.0+) 语法糖，会扩展成一个更新父组件绑定值的 `v-on` 侦听器。

- **用法**：

	动态地绑定一个或多个 `attribute`，或一个组件 prop `到`表达式。

	在绑定 `class` 或 `style` `attribute` 时，支持其它类型的值，如数组或对象。可以通过下面的教程链接查看详情。

	在绑定 `prop` 时，`prop` 必须在子组件中声明。可以用修饰符指定不同的绑定类型。

	没有参数时，可以绑定到一个包含键值对的对象。注意此时 `class` 和 `style` 绑定不支持数组和对象。

- 示例

	```html
	<!-- 绑定一个 attribute -->
	<img v-bind:src="imageSrc">
	
	<!-- 动态 attribute 名 (2.6.0+) -->
	<button v-bind:[key]="value"></button>
	
	<!-- 缩写 -->
	<img :src="imageSrc">
	
	<!-- 动态 attribute 名缩写 (2.6.0+) -->
	<button :[key]="value"></button>
	
	<!-- 内联字符串拼接 -->
	<img :src="'/path/to/images/' + fileName">
	
	<!-- class 绑定 -->
	<div :class="{ red: isRed }"></div>
	<div :class="[classA, classB]"></div>
	<div :class="[classA, { classB: isB, classC: isC }]">
	
	<!-- style 绑定 -->
	<div :style="{ fontSize: size + 'px' }"></div>
	<div :style="[styleObjectA, styleObjectB]"></div>
	
	<!-- 绑定一个全是 attribute 的对象 -->
	<div v-bind="{ id: someProp, 'other-attr': otherProp }"></div>
	
	<!-- 通过 prop 修饰符绑定 DOM attribute -->
	<div v-bind:text-content.prop="text"></div>
	
	<!-- prop 绑定。“prop”必须在 my-component 中声明。-->
	<my-component :prop="someThing"></my-component>
	
	<!-- 通过 $props 将父组件的 props 一起传给子组件 -->
	<child-component v-bind="$props"></child-component>
	
	<!-- XLink -->
	<svg><a :xlink:special="foo"></a></svg>
	```

	`.camel` 修饰符允许在使用 `DOM` 模板时将 `v-bind` `property` 名称驼峰化，例如 SVG 的 `viewBox` `property`：

	```
	<svg :view-box.camel="viewBox"></svg>
	```

	在使用字符串模板或通过 `vue-loader`/`vueify` 编译时，无需使用 `.camel`。

#### v-if, v-else

什么是条件判断语句, 其有以下两个属性

- `v-if`
- `v-else`

**示例**

```html
<!DOCTYPE html>
<html lang="en" xmlns:v-bind="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="UTF-8">
    <title>Index</title>
</head>
<body>

<!-- view层 ${} -->
<div id="app">
    <h1 v-if="type==='A'">A</h1>
    <h1 v-else-if="type==='B'">B</h1>
    <h1 v-else-if="type==='D'">D</h1>
    <h1 v-else>C</h1>
</div>

<!-- 导入Vue.js -->
<script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
<script>
    var vm = new Vue({
        el: "#app",
        data: {
            ok: false,
            type: 'A'
        }
    });
</script>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en" xmlns:v-bind="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="UTF-8">
    <title>Index</title>
</head>
<body>

<!-- view层 ${} -->
<div id="app">
    <li v-for="(item, index) in items">{{item.message}}--{{index}}</li>
</div>

<!-- 导入Vue.js -->
<script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
<script>
    var vm = new Vue({
        el: "#app",
        data: {
            items: [
                {message: "Vue"},
                {message: 'Java'},
                {message: 'Linux'}
            ]
        }
    });
</script>
</body>
</html>
```

#### v-on 

```html
<!DOCTYPE html>
<html lang="en" xmlns:v-on="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="UTF-8">
    <title>Index</title>
</head>
<body>

<!-- view层 ${} -->
<div id="app">
    <button v-on:click="sayHi">Click Me</button>
</div>

<!-- 导入Vue.js -->
<script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
<script>
    var vm = new Vue({
        el: "#app",
        data: {
            message: "Hello, Vue"
        },
        methods: {
            // 方法必须定义在Vue的methods对象中
            sayHi: function () {
                alert(this.message);
            }
        }
    });
</script>
</body>
</html>
```

### Vue: 表单双绑、组件

#### 什么是双向数据绑定

`Vue.js`是一个`MVVM`框架, 即数据双向绑定, 即当数据发生变化的时候, 视图也就发生变化, 当视图发生变化的时候, 数据也会跟着同步变化. 这也算是`Vue`的精髓之处了

目前所说的数据双向绑定, 一定是对于`UI控件`来说的,` 非UI控件`不会涉及到数据双向绑定. 单向数据绑定是使用状态管理工具的前提. 如果我们使用`vuex`, 那么数据流也是单向的, 这时就会和双向数据绑定有冲突

**实现数据的双向绑定,** 对于我们处理表单, `Vue,js`的双向数据绑定用起来就特别舒服, 即两者并不互斥, 在全局性数据流使用单项, 方便跟踪; 局部性数据流使用双向, 简单易操作

#### 在表单中使用双向数据绑定

可以使用`v-model`指令在表单`<input>`、`<textarea>`及`<select>`元素上创建双向数据绑定. 它会根据空间类型自动选取正确的方法来更新元素. 负责监听用户的输入时间以更新数据, 并对一些极端场景进行一些特殊处理

```html
<!DOCTYPE html>
<html lang="en" xmlns:v-on="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="UTF-8">
    <title>Index</title>
</head>
<body>

<!-- view层 ${} -->
<div id="app">

    输入的文本：<input type="text" v-model="message"/>{{message}}

    <br>------------------------------<br>

    性别：
    <input type="radio" name="sex" value="male" v-model="sex">male
    <input type="radio" name="sex" value="female" v-model="sex">female

    <p>
        select：{{sex}}
    </p>

    <br>------------------------------<br>

    下拉框
    <select name="" id="" v-model="selected">
        <option value="" disabled>---请选择---</option>
        <option>A</option>
        <option>B</option>
        <option>C</option>
    </select>

    <p>
        value: {{selected}}
    </p>
  
</div>

<!-- 导入Vue.js -->
<script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
<script>
    var vm = new Vue({
        el: "#app",
        data: {
            message: "123",
            sex: "",
            selected: ""
        },
        methods: {

        }
    });
</script>
</body>
</html>
```

**注意**: 

- `v-model`会忽略所有表单元素的`value`、`checked`、`selected`特性的初始值而总是将`Vue`实例的数据作为数据来源. 
- 如果`v-model  `表达式的初始值未能匹配任何选项, `<select>`元素将被渲染为“未选中”状态. 在`IOS`中,这会使用户无法选择第一个选项. 因为这样的情况下, `IOS`不会触发`change`事件. 因此, 更推荐像上面这样提供一个值为空的禁用选项

#### 什么是组件

组件是可复用的`Vue`实例, 说白了就是一组可以重复使用的模版, 跟`JSTL`的自定义标签、`Thymeleaf`的`th:fragment`等框架有异曲同工之妙. 

### 第一个Vue组件

```html
<!DOCTYPE html>
<html lang="en" xmlns:v-on="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="UTF-8">
    <title>Index</title>
</head>
<body>

<!-- view层 ${} -->
<div id="app">
    <lummer v-for="item in items" v-bind:li="item"></lummer>

</div>

<!-- 导入Vue.js -->
<script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
<script>

    // 定义的一个Vue组件Component
    Vue.component("lummer",{
        props: ['li'],
        template: "<li>{{li}}</li>"
    });

    var vm = new Vue({
        el: "#app",
        data: {
            items: ["java", 'linux', 'vue']
        },
        methods: {
        }
    });

</script>
</body>
</html>
```

说明

- `Vue.component()`: 注册组件
- `my-component-li`: 自定义组件的名字
- `template`: 组件的模版

#### 使用props属性传递参数

注意: 默认规则下`props`属性里的值不能为大写

```html
<script>

    // 定义的一个Vue组件Component
    Vue.component("lummer",{
        props: ['li'],
        template: "<li>{{li}}</li>"
    });

    var vm = new Vue({
        el: "#app",
        data: {
            items: ["java", 'linux', 'vue']
        },
        methods: {
        }
    });

</script>
```

说明

- `v-for=“item in items”`: 遍历`vue`实例中定义的名为`items`的数组, 并创建同等数量的组件
- `v-bind:item=“item”`: 将遍历的`item`项绑定到组件中`props`定义的名为`item`属性上; `= `号左边为`props`定义的属性名, 右边的为`item in items` 中遍历的`item`项的值

### Axios异步通信

#### 什么是Axios

`Axios`是一个开源的可以在浏览器端和`NodeJS`的异步通信框架, 它的主要作用就是实现`AJAX`异步通信, 其功能特点

- 从浏览器中创建`XMLHttp`
- 从 `node.js` 创建 `http` 请求
- 支持` Promise API` [JS中链式编程]
- 拦截请求和响应
- 转换请求数据和响应数据
- 取消请求
- 自动转换`JSON`数据
- 客户端支持防御`XSRF`(跨站请求伪造)

GIthub: https://github.com/axios/axios

中文文档: http://www.axios-js.com/

#### 为什么使用Axios

由于`Vue.js`是一个视图层框架, 所以`Vue.js`并不包含`AJAX`的通信功能, 为了解决通信功能, 作者单独开发了一个名为`vue-resource`的插件, 不过在进入`2.0`版本以后停止了对该插件的维护并推荐了`Axios`框架.

#### 第一个Axios应用程序

开发的接口大部分都是采用`JSON`格式, 可以先在项目中模拟一段`JSON`数据, 数据内容如下: 创建一个名为`data.json`的文件并填入以下内容, 放在项目的根目录下

```json
{  "name": "java",  "url": "https://www.baidu.com",  "page": 1,  "isNonProfit": true,  "address": {    "street": "光华门",    "city": "陕西西安",    "country": "中国"  },  "links": [    {      "name": "bilibili",      "url": "https://space.bilibili.com/95256449"    },    {      "name": "java",      "url": "https://www.kuangstudy.com"    },    {      "name": "baidu",      "url": "https://www.baidu.com"    }  ]}
```

```html
<!DOCTYPE html><html lang="en" xmlns:v-bind="http://www.w3.org/1999/xhtml"><head>    <meta charset="UTF-8">    <title>Title</title>    <!-- v-clock解决闪烁问题 -->    <style>        [v-clock]{            display: none;        }    </style></head><body><div id="vue" v-clock>    <div>        {{info.name}}    </div>    <div>        {{info.address}}    </div>    <a v-bind:href="info.url">Click Me </a></div><script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script><script src="https://unpkg.com/axios/dist/axios.min.js"></script><script type="text/javascript">    var vm = new Vue({        el: "#vue",        // data 属性        // data() 方法        data() {            return {                //  请求的返回参数合适， 必须和json字符串一样                info: {                    name: null,                    address: {                        street: null,                        city: null,                        country: null                    },                    url: null                }            }        },        mounted() { // 钩子函数 链式编程 ES6新特性            axios.get('../data.json').then(response=>(this.info=response.data));        }    });</script></body></html>
```

### Vue计算属性

#### 什么是计算属性

计算属性的重点突出在`属性`两个字上(属性是名词), 首先他是个属性, 其次这个属性有计算的能力(计算是动词), 这里的`计算`是个函数. 简单来说, 他就是一个能够将计算结果缓存起来的属性(将行为转化为静态的属性), 仅此而已, 可以想象为缓存

简单概括: 计算属性 = 计算出来的结果, 保存在属性中

**说明**

- `methods`: 定义方法, 调用方法使用 `currentTime1()`, 需要带括号
- `computed`: 定义计算属性, 抵用属性使用 `currentTime2`, 不需要带括号; `this.message` 是为了能够让 `currentTime2` 观察到数据变化而变化
- 如何在方法中的值发生了变化, 则缓存就会刷新! 可以在控制台中使用 `vm.message=“lummer”`, 改变下数据的值, 再次测试观察效果

**结论**

调用方法时, 每次都需要进行计算, 既然有计算过程必定产生系统开销, 那如果结果不是经常变化的, 此时就可以考虑将这个结果缓存起来, 采用计算属性可以很方便做到这一点, **计算属性的主要特性就是为将不经常变化的计算结果进行缓存, 以节约我们的系统开销**

```html
<!DOCTYPE html><html lang="en" xmlns:v-bind="http://www.w3.org/1999/xhtml"><head>    <meta charset="UTF-8">    <title>Title</title></head><body><div id="vue" v-clock>    <p>currentTime1: {{currentTime1()}}</p>    <p>currentTime2: {{currentTime2}}</p></div><script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script><script src="https://unpkg.com/axios/dist/axios.min.js"></script><script type="text/javascript">    var vm = new Vue({        el: "#vue",        data: {            message: "hello, vue"        },        methods: {            currentTime1: function () {                return Date.now();  // 返回当前时间 - 时间戳            }        },        computed: { // 计算属性： methods 与 computed 方法名不能重名，重名之后，只会调用 methods 中的方法            currentTime2: function () {                return Date.now();  // 返回当前时间 - 时间戳            }        }    });</script></body></html>dedemodemo
```

#### 内容分发

在 `Vue.js` 中我们使用 `<slot>` 元素作为承载分发内容的出口, 作者称之为**插槽**, 可以应用在组合组件的场景中

比如准备制作一个待办事项组件`(todo)`, 该组件有待办标题`(todo-title)`和待办内容`(todo-items)`, 但是这三个组件之间又是相互独立的, 那应该怎么实现呢

```html
<!DOCTYPE html><html lang="en"><head>    <meta charset="UTF-8">    <title>Title</title></head><body><div id="app">    <todo>        <todo-title slot="todo-title" :title="title"></todo-title>        <todo-items slot="todo-items" v-for="item in todoItems" :item="item"></todo-items>    </todo></div><script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script><script>    // slot: 插槽    Vue.component("todo",{        template: '<div>\            <slot name="todo-title"></slot>\                <ul>\                    <slot name="todo-items"></slot>\                </ul>\            </div>'    });    Vue.component("todo-title", {        props: ['title'],        template: '<div>{{title}}</div>'    });    Vue.component("todo-items", {        props: ['item'],        template: '<li>{{item}}</li>'    });    var vm = new Vue({        el: "#app",        data: {            title: '列表书籍',            todoItems: ['Java', 'Linux', 'Python', 'Golang']        }    });</script></body></html>
```

### Vue入门小结

**核心**

- 数据驱动
- 组件化

**优点**

- 借鉴了`AngulaJS`的模块化开发和React的虚拟`Dom`, 虚拟`Dom`就是把`Dom`操作放到内存中执行

**常用的属性**

- `v-if`
- `v-else-if`
- `v-else`
- `v-for`
- `v-on `绑定事件, 简写`@`
- `v-model `数据双向绑定
- `v-bind` 给组件绑定参数, 简写`:`

**组件化**

- 组合组件`slot`插槽
- 组件内部绑定事件需要使用到`this.$emit(“事件名”, 参数);`
- 计算属性的特色, 缓存计算数据

**说明**

`Vue`的开发都是要基于`NodeJS`, 实际开发采用 `vue-cli` 脚手架开发, `vue-router` 路由, `vuex` 做状态管理; `Vue UI`, 界面我们一般使用 `ElementUI`(饿了么出品) 或者 `ICE`(阿里巴巴出品) 来快速搭建前端项目

官网

- https://element.eleme.cn/#/zh-CN
- https://ice.work/

### 第一个vue-cli项目

#### 什么是vue-cli

`vue-cli`官方提供的一个脚手架, 用于快速生成一个`vue`的项目模版

预先定义好的目录结构及基础代码, 就好比咱们在创建`Maven`项目时可以选择创建一个骨架项目, 这个骨架项目就是脚手架, 使得我们的开发更加快速

**主要的功能**

- 统一的目录结构
- 本地调试
- 热部署
- 单元测试
- 集成打包上线

#### 环境配置

- `Node.js`: http://nodejs.cn/download
- `Git`: https://git-scm.com/downloads
	- 镜像: https://npm.taobao.org/mirrors/git-for-windows/

**确认nodejs安装成功**

- `terminal` 下输入 `node -v`, 查看是否能够正确打印出版本号即可
- `terminal` 下输入 `npm -v`, 查看是否能够正确打印出版本号即可

`npm`: 就是一个软件包管理工具, 和`Linux`下的`apt`软件安装差不多

安装 Node.js 淘宝镜像加速器(cnpm)

```shell
# -g 就是全局安装npm install cnpm -g# 或使用如下语句解决 npm 速度慢的问题npm install --registry=https://registry.npm.taobao.org# cnpm 尽量少用, 可能在打包时会出现问题
```

**安装 vue-cli**

```shell
cnpm install vue-cli -g# 测试是否安装成功# 查看可以基于哪些模版创建 vue 应用程序, 通常我们选择 webpackvue list
```

#### 第一个 vue-cli 应用程序

1. 创建一个 Vue 项目, 我们随便建立一个空的文件夹在电脑上

2. 创建一个基于 webpack 模版的 vue 应用程序

	```shell
	# 这里的 myvue 是项目名称, 可以根据自己的需求命名vue init webpack myvue# 一路选择 no 即可
	```

**说明**

- Project name: 项目名称, 默认 回车 即可

- Project description: 项目描述, 默认 回车 即可

- Author: 项目作者, 默认 回车 即可

- Install vue-router: 是否安装 vue-router, 选择 n 不安装(后期需要在手动添加)

- Use ESLint to lint your code: 是否使用 ESLint 做代码检查, 选择 n 不安装(后期需要在手动添加)

- Set up unit tests: 单元测试相关, 选择 n 不安装(后期需要在手动添加)

- Setup e2e tests with Nightwatch: 单元测试相关, 选择 n 不相关(后期需要在手动添加)

- Should we run npm install for you after the project has been created: 创建完成后直接初始化, 选择 n, 我们手动执行, 运行结果

	![image-20210708230342336](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210710225647.png)

##### 初始化并运行

```shell
cd myvuenpm installnpm run dev# 执行完成后, 目录多了很多依赖
```

### Webpack

#### 什么是webpack

本质上, webpack是一个现代JavaScript应用程序的静态模块打包器(module bundler). 当webpack处理应用程序时, 他会递归的构建一个依赖关系图(dependency graph), 其中包含应用程序需要的每个模块, 然后将所有模块打包成一个或多个bundle

Webpack是当下最热门的前端资源模块化管理和打包工具, 他可以将许多松散耦合的模块按照依赖和规则打包成符合生产环境部署的前端资源. 还可以将按需加载的模块进行代码分离, 等到时机需要时再进行异步加载. 通过loader转换, 任何形式的资源都可以当作模块, 比如CommonsJS、AMD、ES6、CSS、JSON、CoffeeScript、LESS等

伴随着移动互联网的大潮, 当今越来越多的网站已经从网页模式进化到了WebApp模式. 他们运行在现代浏览器中, 使用HTML5、CSS3、ES6等新的技术来开发丰富的功能, 网页已经不仅仅是完成浏览器的基本需求. WebApp通常是一个SPA(单页面应用), 每一个视图通过异步的方式加载, 这导致页面初始化和使用过程中会加载越来越多的JS代码, 这给前端的开发流程和资源组织带来了巨大挑战

前端开发和其他开发工作的主要区别, 首先是前端基于多语言、多层次的编码和组织工作, 其次前端产品的交付是基于浏览器的, 这些资源是通过增量加载的方式运行到浏览器端, 如何在开发环境组织好这些碎片化的代码和资源, 并且保证他们在浏览器端快速、优雅的加载和更新, 就需要一个模块化系统, 这个理想的模块化系统是前端工程师多年来探索的难题

#### 模块化的演进

##### Script标签

```js
<script src="module1.js"></script><script src="module2.js"></script><script src="module3.js"></script><script src="module4.js"></script>
```

这是最原始的JavaScript文件加载方式, 如果把每一个文件看作是一个模块, 那么他们的接口通常是暴露在全局作用域下, 也就是定义在window对象中, 不同模块的调用都是一个作用域

这种原始的加载方式暴露了一些显而易见的弊端

- 全局作用域下容易造成变量冲突
- 文件只能按照<script>的书写顺序进行加载
- 开发人员必须主观解决模块和代码库的依赖关系
- 在大型项目中各种资源难以管理, 长期积累的问题导致代码库混乱不堪

##### CommonsJS

服务端的NodeJS遵循CommonsJS规范, 规范核心思想是允许模块通过require方法来同步加载所需依赖的其他模块, 然后通过exports或者module.exports来导出需要暴露的接口

```js
require("module");require("../module.js");export.doStuff = function(){};module.exports = someValue;
```

**优点**

- 服务器端模块便于重用
- NPM中已经有超过45万个可以使用的模块包
- 简单易用

**缺点**

- 同步的模块加载方式不适合在浏览器环境中, 同步意味着阻塞加载, 浏览器资源是异步加载的
- 不能非阻塞的并行加载多个模块

**实现**

- 服务端的NodeJS
- Browserify, 浏览器端的CommonsJS实现, 可以使用NPM模块, 但是编译打包后的文件体积比较大
- modules-webmake、类似Browserify, 但不如Browserify灵活
- wreq, Browserify的前身

##### AMD

他在声明模块的时候指定所有的依赖dependencies, 并且还要当作形参传到factory中, 对于依赖的模块提前执行

```js
define("module", ["dep1", "dep2"], function(d1, d2){  return someExportedValue;});require(["module", "../file.js"], function(module, file){});
```

**优点**

- 适合在浏览器环境中异步加载模块
- 可以并行加载多个模块

**缺点**

- 提高了开发成本, 代码的阅读和书写比较困难, 模块定义方式的语义不畅
- 不符合通用的模块化思维方式, 是一种妥协到的实现

**实现**

- RequireJS
- curl

##### CMD

Commons Module Definition 规范和 AMD 很相似, 尽量保持简单, 并与 CommonsJS 和 NodeJS 的 Modules 规范保持了很大的兼容性

```js
define(function(require, exports, module){  var $ = require("jquery");  var Spinning = require("./spinning");  exports.doSomething = ...;  module.exports = ...;});
```

**优点**

- 依赖就近, 延迟执行
- 可以很容易在 NodeJS中运行

**缺点**

- 依赖SPM打包, 模块的加载逻辑片中

**实现**

- Sea.js
- coolie

##### ES6 模块

EcmaScript6标准增加了JavaScript语言层面的模块体系定义, ES6模块的设计思想, 是尽量静态化, 使编译时就可以确定模块的依赖关系, 以及输入和输出的变量. CommonsJS 和 AMD 模块, 都只能在运行时确定这些东西

```js
import "jquery";export function doStuff(){}module "localModule"{}
```

**优点**

- 容易进行静态分析
- 面向未来的 EcmaScript 标准

**缺点**

- 原生浏览器端还没有实现该标准
- 全新的命令, 新版的 NodeJS 才支持

**实现**

- Babel

#### 安装Webpack

Webpack是一款模块加载器兼打包工具, 他可以把各种资源, 如JS、JSX、ES6、SASS、LESS、图片等都作为模块来处理和使用

##### 安装

```shell
npm install webpack -gnpm install webpack-cli -g
```

##### 测试安装成功

- webpack -v
- webpack-cli -v

##### 配置

创建webpack.config.js配置文件

- entry: 入口文件, 指定 WebPack 用哪个文件作为项目的入口
- output: 输出, 指定 WebPack 把处理完成的文件放置到指定路径
- module: 模块, 用于处理各种类型的文件
- plugins: 插件, 如: 热更新、代码重用等
- resolve: 设置路径指向
- watch: 监听, 用于设置文件改动后直接打包

```js
module.exports = {  entry: "",  output: {    path: "",    filename: ""  },  module: {    loaders: [      {test: /\.js$/, loader: ""}    ]  },  plugins: {},  resolve: {},  watch: true};
```



直接运行webpack命令打包即可

##### 使用webpack

1. 创建项目

2. 创建一个名为modules的目录, 用于放置JS模块等资源文件

3. 在modules下创建模块文件, 如hello.js, 用于编写JS模块相关代码

	```js
	// 暴露一个方法: sayHiexports.sayHi = function(){  document.write("<div>Hello WebPack</div>");};
	```

4. 在modules下创建一个名为main.js的入口文件, 用于打包时设置extry属性

	```js
	// require 导入一个模块, 就可以调用这个模块中的方法var hello = require("./hello");hello.sayHi();
	```

5. 在项目目录下创建 webpack.config.js配置文件, 使用webpack命令打包

	```js
	module.exports = {  entry: "./modules/main.js",  output: {    filename: "./js/bundle.js"  }};
	```

6. 在项目目录下创建index.html文件, 引入bundle.js文件

7. 在控制台直接执行webpack, 如果失败的话, 就是用管理员权限运行即可

8. 运行HTML看效果

**说明**

```shell
# 参数 --watch 用于监听变化webpack --watch
```

### vue-router 路由

#### 说明

Vue Router 是 Vue.js 官方的路由管理器. 它和 Vue.js 的核心深度集成, 让构建单页面应用变得易如反掌.

功能

- 嵌套的路由/视图表
- 模块化的、基于组件的路由配置
- 路由参数、查询、通配符
- 基于Vue.js过度系统的视图过渡效果
- 细粒度的导航控制
- 带有自动激活的CSS class的链接
- HTML5历史模式或hash模式, 在IE9中自动降级
- 自定义的滚动条行为

#### 安装

基于第一个vue-cli进行测试学习, 先查看node_modules中是否存在vue-router

vue-router是一个插件包, 所以我们还是需要用npm/cnpm进行安装. 打开terminal, 进入项目目录, 输入下列命令

```shell
npm install vue-router --save-dev
```

如果在一个模块化工程中使用它, 必须通过Vue.use()明确的安装路由功能

```shell
import Vue from 'vue'import VueRouter from 'vue-router'Vue.use(VueRouter);
```

#### 测试

1. 删除没有的东西

2. components目录下存放我们编写的组件

3. 定义一个Content.vue的组件

	```js
	<template>  <h1>Java - Linux - Vue - SSM</h1></template><script>    export default {        name: "Content"    }</script><style scoped></style>
	```

4. 安装路由, 在src目录下, 新建一个文件夹: router, 专门存放路由

	```js
	import Vue from 'vue'import VueRouter from "vue-router"import Content from "../components/Content";import Main from "../components/Main";// 安装路由Vue.use(VueRouter);// 配置导出路由export default new VueRouter({  routes:[    {      // 路由路径      path: '/content',      name: 'content',      // 跳转的组件      component: Content    },    {      // 路由路径      path: '/main',      name: 'main',      // 跳转的组件      component: Main    }  ]});
	```

5. 在main.js中配置路由

	```js
	// The Vue build version to load with the `import` command// (runtime-only or standalone) has been set in webpack.base.conf with an alias.import Vue from 'vue'import App from './App'import router from './router' // 自动扫描里面的路由配置文件Vue.config.productionTip = false;/* eslint-disable no-new */new Vue({  el: '#app',  // 配置路由  router,  components: { App },  template: '<App/>'})
	```

6. 在App.vue中使用路由

	```js
	<template>  <div id="app">    <h1>Vue-Router</h1>    <router-link to="/main">首页</router-link>    <router-link to="/content">内容</router-link>    <router-view></router-view>  </div></template><script>  import Content from './components/Content'export default {  name: 'App',    components: {      Content    }}</script><style>#app {  font-family: 'Avenir', Helvetica, Arial, sans-serif;  -webkit-font-smoothing: antialiased;  -moz-osx-font-smoothing: grayscale;  text-align: center;  color: #2c3e50;  margin-top: 60px;}</style>
	```



### Vue+elementUI实战

#### 创建工程

**注意:** 命令行都要使用管理员模式运行

1. 创建一个名为hello-vue的工程vue init webpack hello-vue

2. 安装依赖, 我们需要安装 vue-router、element-ui、sass-loader和node-sass四个插件

	```shell
	# 进入工程目录cd hello-vue# 安装 vue-routernpm install vue-router --save-dev# 安装 element-uinpm i element-ui -S# 安装依赖npm install# 安装 SASS 加载器cnpm install sass-loader node-sass --save-dev# 启动测试npm run dev
	```

3. npm命令解释

	- npm install moduleName: 安装模块到项目目录下
	- npm install -g moduleName: -g的意思是将模块安装到全局, 具体安装到磁盘哪个位置, 要看 npm config profix的位置
	- npm install -save moduleName: —save的意思是将模块安装到项目目录下, 并在package文件的dependencies节点写入依赖, -S为该命令的缩写
	- npm install -save-dev moduleName: —save-dev 的意思是将模块安装到项目目录下, 并在package文件的devDependencies节点写入依赖, -D为该命令的缩写

4. 代码详情请翻资料

#### 路由嵌套

路由嵌套又称子路由, 在实际应用中, 通常由多层嵌套的组件组合而成. 同样的, URL中各段动态路径也按某种结构对应嵌套的各层组件, 例如

```shell
/user/foo/profile																	/user/foo/posts+---------------------+														+---------------------+|	User								|														|	User							 	||	+---------------+		|														|	+---------------+		||	| Profile				|		|			+--------------->			|	| Posts					|		|	|	|								|		|														|	|								|		|	|	+---------------+		|														|	+---------------+		|+---------------------+														+---------------------+
```

```js
import Vue from 'vue'import VueRouter from "vue-router";import Main from '../views/Main'import Login from '../views/Login'import Profile from "../views/user/Profile";import List from "../views/user/List";import fa from "element-ui/src/locale/lang/fa";Vue.use(VueRouter);export default new VueRouter({  routes: [    {      path: '/main',      component: Main,   // 嵌套路由      children: [        {          path: '/user/profile/:id',          component: Profile,        },        {          path: '/user/list',          component: List        }      ]    },    {      path: '/login',      component: Login    }});
```

#### 参数传递

```vue
<el-menu-item-group>  <el-menu-item index="5-1">    <!-- name: 地址  params: 传递参数 -->    <router-link :to="{name: 'Profile', params: {id: 1}}">个人信息</router-link>  </el-menu-item>  <el-menu-item index="5-2">    <router-link to="/user/list">用户列表</router-link>  </el-menu-item>  <el-menu-item index="5-3">    <router-link to="/goHome">回到首页</router-link>  </el-menu-item></el-menu-item-group>
```

```js
import Vue from 'vue'import VueRouter from "vue-router";import Main from '../views/Main'import Login from '../views/Login'import Profile from "../views/user/Profile";import List from "../views/user/List";import fa from "element-ui/src/locale/lang/fa";Vue.use(VueRouter);export default new VueRouter({  routes: [    {      path: '/main',      component: Main,   // 嵌套路由      children: [        {          // 参数传递          path: '/user/profile/:id',          name: 'Profile',          component: Profile,          // 两种方式传递参数          props: true        },        {          path: '/user/list',          component: List        }      ]    },    {      path: '/login',      component: Login    },    {      path: '/goHome',      redirect: '/main'    }  ]});
```

```vue
<template><!--  所有的元素必须在标签内-->    <div>      <h1>个人信息</h1>      {{id}}    </div></template><script>    export default {      	// 参数传递        props: ['id', 'user', 'pwd'],        name: "Profile"    }</script><style scoped></style>
```

#### 重定向

```js
import Vue from 'vue'import VueRouter from "vue-router";import Main from '../views/Main'import Login from '../views/Login'import Profile from "../views/user/Profile";import List from "../views/user/List";import fa from "element-ui/src/locale/lang/fa";Vue.use(VueRouter);export default new VueRouter({  routes: [    {      path: '/main',      component: Main,   // 嵌套路由      children: [        {          path: '/user/profile/:id',          name: 'Profile',          component: Profile,          // 两种方式传递参数          props: true        },        {          path: '/user/list',          component: List        }      ]    },    {      path: '/login',      component: Login    },    {      // 重定向      path: '/goHome',      redirect: '/main'    }  ]});
```

### 路由模式与404

路由模式有两种

- hash: 路径带#符号, 如https://localhost/#/login
- history: 路径不带#符号, 如https://localhost/login

修改路由配置, 代码如下

```js
export default new Router({  mode: 'history',  routes: []});
```

处理404创建一个名为NotFound.vue的视图组件, 代码如下

```vue
<template>	<div>  	页面不存在, 请重试  </div></template><script>	export default{    name: 'NotFound'  }</script><style></style>
```

修改路由配置, 代码如下

```ja
import NotFound form '../views/NotFound'{	path: '*',	component: NotFound}
```

#### 路由钩子与异步请求

beforeRouteEnter: 在进入路由前执行

beforeRouteLeave: 在离开路由前执行

```js
export default{	props: ['id'],	name: "Profile",	beforeRouteEntry: (to, from, next) => {		console.log("准备进入个人信息页");    next();	}  beforeRouteLeave: (to, from, next) => {    console.log("准备离开个人信息页");    next();  }}
```

**参数说明**

- to: 路由将要跳转的路径信息
- from: 路径跳转前的路径信息
- next: 路由的控制参数
	- next()跳入下一个页面
	- next(‘/path’)改变路由的跳转方向, 使其跳转到另外一个路由
	- next(false)返回原来的页面
	- next((vm)=>{})仅在beforeRouteEnter中可以用, vm是组件实例

**在钩子函数中使用异步请求**

1. 安装 Axios cnpm install axios -s

2. main.js引用Axios

	```js
	import axios from 'axios'Vue.prototype.axios = axios;
	```

3. 准备数据: 只有我们的static目录下的文件是可以被访问到的, 所以我们把静态文件放入该目录下

	```shell
	// 静态数据存放的位置static/mock/data.json
	```

4. 在beforeRouteEnter中进行异步请求

