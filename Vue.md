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



## Vue：表单双绑、组件

### 什么是双向数据绑定

Vue.js是一个MVVM框架，即数据双向绑定，即当数据发生变化的时候，视图也就发生变化，当视图发生变化的时候，数据也会跟着同步变化。这也算是Vue.js的精髓之处了。

值得注意的是，我们所说的数据双向绑定，一定是对于UI控件来说的，非UI控件不会涉及到数据双向绑定。



### 在表单中使用双向数据绑定

在表单中可以使用v-model进行双向数据绑定，在<input>、<textarea>、<select>等元素上创建双向数据绑定。

### Vue组件

```js
// 定义一个组件【就是一个模板】
Vue.component("uncle", {
    props: ['item'],//如果不用props，就取不到外面的item值
    template: '<li>{{item}}</li>'
});
```



## Vue：Axios异步通信

### 什么是Axios

Axios是一个开源的可以用在浏览器端和NodeJS的异步通信框架，它的主要作用就是实现AJAX异步通信，其功能特点如下：

- 从浏览器中创建`XMLHttpRequests`
- 从node.js创建http请求
- 支持Promise API 【JS中链式编程】
- 拦截请求和响应
- 转换请求数据和响应数据
- 取消请求
- 自动转换JSON数据
- 客户端支持防御XSRF（跨站请求伪造）

GitHub：https://github.com/axios/axios

中文文档：http://www.axios-js.com/

### 为什么要使用Axios

由于Vue.js是一个视图层框架并且作者（尤雨溪）严格准守SoC(关注度分离原则)，所以Vue.js并不包含AJAX的通信功能，为了解决通信问题，作者单独开发了一个名为vue-resource的插件，不过在进入2.0版本以后停止了对该插件的维护并推荐了Axios框架。少用jQuery,因为它操作Dom太频繁！

在线cdn

~~~html
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
~~~



## 计算属性

计算出来的结果，保存在属性中。

计算就是个函数，简单点说，它就是一个能够将计算结果缓存起来的属性（将行为转化成了静态的属性），仅此而已；可以想象为==缓存==



## slot插槽



## vue-cli

vue-cli是官方提供的一个脚手架，用于快速生成一个vue的项目模板

### 需要环境

Node.js：http://nodejs.cn/download/

电脑安装-下一步 安装在自己的环境目录下

node -v

npm -v

这个npm，就是一个软件包管理工具，就和linux下的apt软件安装差不多

安装Node.js淘宝镜像加速器（cnpm）

这样子的话，下载会快很多

~~~bash
# -g 就是全局安装
npm install cnpm -g

# 或使用如下语句解决 npm 速度慢的问题
npm install --registry=https://registry.npm.taobao.org
~~~

安装过程可能有点慢~耐心等待。虽然安装了cnpm 但是尽量少用



最好启用cmd管理员

安装vue-cli

~~~bash
cnpm install vue-cli -g

# 测试是否安装成功
# 查看可以基于哪些模板创建vue 应用程序 ，通常我们选择webpack
vue list
~~~

安装webpack

~~~bash
# 这两个同事都要安装，webpack的客户端cli
npm install webpack -g
npm install webpack-cli -g

#测试成功
webpack -v
webpack-cli -v
~~~







### 第一个vue-cli应用程序

1、创建一个Vue项目，我们随便建立一个空的文件夹在电脑上，比如在D盘下新建一个目录

`D:\Project\vue-study`

2、创建一个基于webpack模板的vue应用程序

~~~bash
# 这里的 myvue 是项目名称，可以根据自己的需求起名
vue init webpack myvue

F:\UncleRayslove\MyGitHub\my_vue_study>vue init webpack myvue

? Project name myvue
? Project description A Vue.js project
? Author leipei <leipei@ebupt.com>
? Vue build standalone
? Install vue-router? No
? Use ESLint to lint your code? No
? Set up unit tests No
? Setup e2e tests with Nightwatch? No
? Should we run `npm install` for you after the project has been created? (recommended) no

   vue-cli · Generated "myvue".

# Project initialization finished!
# ========================

To get started:

  cd myvue
  npm install (or if using yarn: yarn)
  npm run dev

Documentation can be found at https://vuejs-templates.github.io/webpack
~~~

一路都选择no即可；原因是可以自己手动去设置一些东西【熟悉过程和结构】

**初始化并运行**

~~~bash
cd myvue

npm install
# install之后，提示可能需要修复，按提示输入命令修复即可
added 1268 packages from 675 contributors and audited 1275 packages in 256.849s

42 packages are looking for funding
  run `npm fund` for details

found 17 vulnerabilities (3 low, 8 moderate, 6 high)
  run `npm audit fix` to fix them, or `npm audit` for details
  
# 启动测试
npm run dev
~~~



说明：



## 创建工程-结合element-ui

~~~bash
# 这里的 myvue 是项目名称，可以根据自己的需求起名
vue init webpack myvue
一路都选择no即可；原因是可以自己手动去设置一些东西【熟悉过程和结构】

#进入到工程目录
cd myvue

# 安装 vue-router
npm install vue-router --save-dev

#安装 element-ui
npm i element-ui -S

#安装依赖
npm install

# 安装SASS加载器
cnpm install sass-loader node-sass --sava-dev

# 启动测试
npm run dev
~~~

