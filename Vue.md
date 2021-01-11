# Vue篇

Vue是一套用于构建用户界面的渐进式（javaScript）框架。Vue的核心库只关注视图层



## 前端三要素

- HTML（结构）：超文本标记语言（Hyper Text Markup Language），决定网页的结构和内容
- CSS（表现）：层叠样式表（Cascading Style Sheets），设定网页的表现样式
- JavaScript（行为）：是一种弱类型脚本语言，其源代码不需经过编译，而是由浏览器解释运行，用于控制网页的行为

CSS预处理器？？一种语言

SASS

LESS：基于Node.js

## Native原生JS开发

按照【ECMAScript】标准的开发方式，简称是ES，特点是所有浏览器都支持。

- ES3
- ES4（内部，未正式发布）
- ES5（全浏览器支持）
- ES6（常用，当前主流版本：webpack打包成为ES5支持！）
- ES7
- ES8
- ES9（草案阶段）



## TypeScript微软的标准

JS的一个超集，本质上向这个语言添加了可选的静态类型和基于类的面向对象编程。

TS特点除了具备ES的特性之外还纳入了许多不在便准范围内的新特性，所以会导致一些浏览器不能直接支持TS语法，需要编译后（编译成JS）才能被浏览器正确执行



## JavaScript框架

- jQuery：熟知的JavaScript框架，优点是简化了DOM操作，缺点是DOM操作太频繁，影响前端性能；在前端眼里使用它仅仅是为了兼容IE6、7、8
- Angular：Google收购的前端框架，一群Java程序员开发的。特点是将后台的MVC模式搬到了前端并增加了模块化开发的理念；与微软合作，采用TypeScript语言开发
- React：FaceBook出品，一款高性能的JS前端框架，特点是提出了新概念【虚拟DOM】用于减少真实DOM操作，在内存中模拟DOM操作，有效提升了前端渲染效率；缺点是使用复杂，因为需要额外学习一门【JSX】语言
- ==Vue==：一款渐进式JavaScript框架，所谓渐进式就是逐步实现新特性的意思，如实现模块化开发、路由、状态管理等新特性。其特点是综合了Angular（模块化）和React（虚拟DOM）的优点
- ==Axios==：前端通信框架；因为Vue的边界很明确，就是为了处理DOM，所以并不具备通信能力，此时就需要额外使用一个通信框架与服务器交互；当然也可以直接选择使用jQuery提供的AJAX通信功能。

## UI框架

- Ant-Design：阿里巴巴出品，基于React的UI框架
- ElementUI、iview、ice：饿了么出品，基于Vue的UI框架
- Bootstrap：Twitter推出的一个用于前端开发的开源工具包
- AmazeUI：又叫”妹子UI“，一款HTML5跨屏前端框架

## JavaScript构建工具

- Babel：JS编译工具，主要用于浏览器不支持的ES新特性，比如用于编译TypeScript
- WebPack：模块打包器，主要作用是打包、压缩、合并及按序加载



## Node.js后台技术

既然是后台技术，肯定也需要框架和项目管理工具。NodeJS框架及项目管理工具如下：

- Express：NodeJS框架
- Koa：Express简化版
- NPM：项目综合管理工具，类似于Maven
- YARN：NPM的替代方案，类似于Maven和Gradle的关系



## 前端为主的MV*时代

- MVC（同步通信为主）：Model、View、Controller
- MVP（异步通信为主）：Model、View、Presenter
- MVVM（异步通信为主）：Model、View、ViewModel



View   ViewModel Model  数据双向绑定

## MVVM模式的实现者

- Model：模型层，在这里表示JavaScript对象

- View：视图层，在这里表示DOM（HTML操作的元素）
- ==ViewModel==：连接视图和数据的中间件，Vue.js就是MVVM中的ViewModel层的实现者

在MVVM架构中，是不允许 数据 和视图 直接通信的，只能通过ViewModel来通信，而ViewModel就是定义了一个Observer观察者

- ViewModel能够观察到数据的变化，并对视图对应的内容进行更新
- ViewModel能够监听到视图的变化，并能够通知数据发生改变

至此，我们就明白了，Vue.js就是一个MVVM的实现者，它的核心就是实现了DOM==监听与数据绑定==



工具：IDEA下载Vue插件

vue在线cdn

```xml
 <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.js"></script>
 <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
```

v-on:click="方法名"——点击事件



## 双向数据绑定

### v-model 双向数据绑定

在表单中可以使用v-model进行双向数据绑定

### Vue组件























