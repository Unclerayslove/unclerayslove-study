# 编辑器篇`Intellij IDEA`

## 酸爽！ Intellij IDEA 神器居然还藏着这些实用小技巧 ！

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/ow6przZuPIENb0m5iawutIf90N2Ub3dcPuP2KXHJvaR1Fv2FnicTuOy3KcHuIEJbd9lUyOibeXqW8tEhoJGL98qOw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/knmrNHnmCLFB8R9CjZg2crOT56ZkubQ9PyjQBDDZ3pKRWZJ83Fe8zSzCtvWdbnvW5fFA3cqOxMfoSeebuwkZMA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

作者：Sam哥哥

blog.csdn.net/linsongbin1/article/details/80211919

### 概述

`Intellij IDEA`真是越用越觉得它强大，它总是在我们写代码的时候，不时给我们来个小惊喜。出于对`Intellij IDEA`的喜爱，我决定写一个与其相关的专栏或者系列，把一些好用的`Intellij IDEA`技巧分享给大家。本文是这个系列的第一篇，主要介绍一些你可能不知道的但是又实用的小技巧。

### 我最爱的【演出模式】

我们可以使用【Presentation Mode】，将`IDEA`弄到最大，可以让你只关注一个类里面的代码，进行毫无干扰的`coding`。

可以使用`Alt+V`快捷键，弹出`View`视图，然后选择`Enter Presentation Mode`。效果如下：![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/knmrNHnmCLFB8R9CjZg2crOT56ZkubQ9Tx4vRvcnrAlLic2Ckn9macer6nkMyYoYf4XELJEdDN4yl1p8BoZHMTw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

这个模式的好处就是，可以让你更加专注，因为你只能看到特定某个类的代码。可能读者会问，进入这个模式后，我想看其他类的代码怎么办？这个时候，就要考验你快捷键的熟练程度了。你可以使用`CTRL+E`弹出最近使用的文件。又或者使用`CTRL+N`和`CTRL+SHIFT+N`定位文件。

如何退出这个模式呢？很简单，使用`ALT+V`弹出view视图，然后选择`Exit Presentation Mode` 即可。但是我强烈建议你不要这么做，因为你是可以在`Enter Presentation Mode`模式下在`IDEA`里面做任何事情的。当然前提是，你对`IDEA`足够熟练。

### 神奇的Inject language

如果你使用`IDEA`在编写`JSON`字符串的时候，然后要一个一个`\`去转义双引号的话，就实在太不应该了，又烦又容易出错。在`IDEA`可以使用`Inject language`帮我们自动转义双引号。![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/knmrNHnmCLFB8R9CjZg2crOT56ZkubQ9PKIU0PHwp9BDoJUhBZxRnialictcmqIB1FPmkjYmibicbegpnPOWpsFveA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

先将焦点定位到双引号里面，使用`alt+enter`快捷键弹出`inject language`视图，并选中`Inject language or reference`。![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/knmrNHnmCLFB8R9CjZg2crOT56ZkubQ9v4tBW0Me0uqdIuF83zvicXOlbkEtoXyyiatVdAqV2sibWvWv9rTGYu0lQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

选择后,切记，要直接按下`enter`回车键，才能弹出`inject language`列表。在列表中选择 `json`组件。![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/knmrNHnmCLFB8R9CjZg2crOT56ZkubQ9ibfeF4ia8JrK6Xj9vibtGbewFwyMAwKmbLesyjxuL0IvVErHCYE4lqhKg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

选择完后。鼠标焦点自动会定位在双引号里面，这个时候你再次使用`alt+enter`就可以看到![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/knmrNHnmCLFB8R9CjZg2crOT56ZkubQ9dRp6Yzibr9ibwt1k8picibEDJA0HT3DIqBWk8dGzCicRlxkNB1ia1MMTPUJQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

选中`Edit JSON Fragment`并回车，就可以看到编辑`JSON`文件的视图了。![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/knmrNHnmCLFB8R9CjZg2crOT56ZkubQ9J1KicxcWsBDzRDe5cgjzXJ1KMEo7msLfRq0O7YQ0PG5wfApRmiavzSQQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

可以看到`IDEA`确实帮我们自动转义双引号了。如果要退出编辑`JSON`信息的视图，只需要使用`ctrl+F4`快捷键即可。

`Inject language`可以支持的语言和操作多到你难以想象，读者可以自行研究。

### 使用快捷键移动分割线

假设有下面的场景，某个类的名字在`project`视图里被挡住了某一部分。![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/knmrNHnmCLFB8R9CjZg2crOT56ZkubQ9E7jEDkV1Bw9PPHMuP0kMP6jf6pWaLo0J51cqocbviaiabXaDg9tuY6GA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

你想完整的看到类的名字，该怎么做。一般都是使用鼠标来移动分割线，但是这样子效率太低了。可以使用`alt+1`把鼠标焦点定位到`project`视图里，然后直接使用`ctrl+shift+左右箭头`来移动分割线。

### ctrl+shift+enter不只是用来行尾加分号的

`ctrl+shift+enter`其实是表示`为您收尾`的意思，不只是用来给代码加分号的。比如说：![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

这段代码，我们还需要为if语句加上大括号才能编译通过，这个时候你直接输入`ctrl+shift+enter`，`IDEA`会自动帮你收尾，加上大括号的。

### 不要动不动就使用IDEA的重构功能

`IDEA`的重构功能非常强大，但是也有时候，在单个类里面，如果只是想批量修改某个文本，大可不必使用到重构的功能。比如说：![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

上面的代码中，有5个地方用到了rabbitTemplate文本，如何批量修改呢？首先是使用`ctrl+w`选中`rabbitTemplate`这个文本,然后依次使用5次`alt+j`快捷键，逐个选中，这样五个文本就都被选中并且高亮起来了，这个时候就可以直接批量修改了。![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

### 去掉导航栏

去掉导航栏，因为平时用的不多。![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

可以把红色的导航栏去掉，让`IDEA`显得更加干净整洁一些。使用`alt+v`，然后去掉`Navigation bar`即可。去掉这个导航栏后，如果你偶尔还是要用的，直接用`alt+home`就可以临时把导航栏显示出来。![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

如果想让这个临时的导航栏消失的话，直接使用`esc`快捷键即可。

### 把鼠标定位到project视图里

当工程里的包和类非常多的时候，有时候我们想知道当前类在project视图里是处在哪个位置。![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

上面图中的`DemoIDEA`里，你如何知道它是在`spring-cloud-config`工程里的哪个位置呢？可以先使用`alt+F1`，弹出`Select in`视图，然后选择`Project View`中的`Project`，回车，就可以立刻定位到类的位置了。

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)这里写图片描述

那如何从`project`跳回代码里呢？可以直接使用`esc`退出`project`视图，或者直接使用`F4`,跳到代码里。

### 强大的symbol

如果你依稀记得某个方法名字几个字母，想在`IDEA`里面找出来，可以怎么做呢？直接使用`ctrl+shift+alt+n`，使用`symbol`来查找即可。比如说：![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

你想找到checkUser方法。直接输入`user`即可。![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

如果你记得某个业务类里面有某个方法，那也可以使用首字母找到类,然后加个`.`，再输入方法名字也是可以的。![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

### 如何找目录

使用`ctrl+shift+n`后，使用`/`，然后输入目录名字即可.![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

### 自动生成not null判断语句

自动生成not null这种if判断，在`IDEA`里有很多种办法，其中一种办法你可能没想到。![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

当我们使用rabbitTemplate. 后，直接输入`notnull`并回车，`IDEA`就好自动生成if判断了。![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

### 按照模板找内容

这个也是我非常喜欢的一个功能，可以根据模板来找到与模板匹配的代码块。比如说：

> 想在整个工程里面找到所有的try catch语句,但是catch语句里面没有做异常处理的。

catch语句里没有处理异常，是极其危险的。我们可以`IDEA`里面方便找到所有这样的代码。![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

首先使用`ctrl+shift+A`快捷键弹出action框，然后输入`Search Struct`![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/knmrNHnmCLFB8R9CjZg2crOT56ZkubQ90NXWY0ZZicVxuepYcibXDhIqkUFOricGmRGxNn6ghacZ7D61Yt1cINAgg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

选择`Search Structurally`后，回车，跳转到模板视图。![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/knmrNHnmCLFB8R9CjZg2crOT56ZkubQ9vibFJD4SDpqS5PP9EE2iaA9e3fwCh8FEtWLFYOZekl1hs0lLwrrsfw1g/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

点击`Existing Templates`按钮，选择`try`模板。为了能找出catch里面没有处理异常的代码块，我们需要配置一下`CatchStatement`的`Maximum count`的值，将其设置为1。

点击`Edit Variables`按钮，在界面修改`Maximum count`的值。![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/knmrNHnmCLFB8R9CjZg2crOT56ZkubQ91glnTuMh2mKJ1icnZjkyxHIyXcgicyShBcMLM4dE3ym77xHicCskC376Q/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

最后点击`find`按钮，就可以找出catch里面没有处理异常的代码了。![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/knmrNHnmCLFB8R9CjZg2crOT56ZkubQ9tiaI5DJkYWG1YiaIzqA5ULIo0TMHibHxT6BHDINUgGzcib3H4aJYaJko9A/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)





## 试试 IntelliJ IDEA 自带的高能神器！

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/1QxwhpDy7ia0kbfibMXwGrBKv99xx47wrBCHa5z9bicS4jMNIMRbfGOTcdFicO6HS7LPza89icRgpqLLcRLmicNrhjOg/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)作者：凯京技术团队

链接：https://my.oschina.net/keking/blog/3104972





![图片](https://mmbiz.qpic.cn/mmbiz_png/1J6IbIcPCLanG2nzjVZov1VibmPXR7lDibFjRdTvH1iaDz9ic4H3xRZCz7BM563rFFfvRukzX7uhOqXc8yDhEZqicFQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

正文

- 从postman到IDEA REST Client
- IDEA REST Client控制台
- 历史请求记录
- 构建HTTP请求脚本
- 环境区分
- 结果断言
- 结果值暂存
- 结语

### **前言**

接口调试是每个软件开发从业者必不可少的一项技能，一个项目的的完成，可能接口测试调试的时间比真正开发写代码的时间还要多，几乎是每个开发的日常工作项。

所谓工欲善其事必先利其器，在没有尝到IDEA REST真香之前，postman（chrome的一款插件）确实是一个非常不错的选择，具有完备的REST Client功能和请求历史记录功能。

但是当使用了IDEA REST之后，postman就可以丢了，因为，IDEA REST Client具有postman的所有功能，而且还有postman没有的功能，继续往下看。

### **从postman到IDEA REST Client**

真香定律的原因有如下几个：

1. 首先postman的所有功能IDEA REST Client都具备了，如REST Client控制台和历史请求记录
2. 其次如果能够在一个生产工具里完成开发和调试的事情，干嘛要切换到另一个工具呢
3. 然后IDEA REST Client还支持环境配置区分的功能，以及接口响应断言和脚本化处理的能力
4. IDEA REST Client的请求配置可以用文件配置描述，所以可以跟随项目和项目成员共享

### **IDEA REST Client控制台**

从顶层工具栏依次Tools -> HTTP Client -> Test RESTFUL Web Service 打开后，IDEA REST Client控制台的界面如下样式：

![图片](https://mmbiz.qpic.cn/mmbiz_png/CvQa8Yf8vq2oEz6dCicKG4SodNzklEzWNWkvaNciaZ3qk7zkF4R9rN1Q4hSzicYFXGEq6cMnOibS4icjnom7KXSFOUw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

可以看到，这个控制台展示的功能区和postman已经没什么差别了，包括请求方式，请求参数和请求头的填充都已经包含了，特别说明下的是，如果请求的方式是Authorization :Basic这种方式认证的话，可以点击下图所示的按钮，会弹出填充用户名和密码的窗口出来，填完后会自动补充到Authorization 的header里面去

![图片](https://mmbiz.qpic.cn/mmbiz_png/CvQa8Yf8vq2oEz6dCicKG4SodNzklEzWNlYa7zgUicVuic7U3eFc52eBT2kJO15zMuAspQemyxH2bdicQV1icqQXd0g/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### **历史请求记录**

IntelliJ IDEA自动将最近执行的50个请求保存到http-requests-log.http 文件中，该文件存储在项目的.idea / httpRequests / 目录下。

使用请求历史记录，您可以快速导航到特定响应并再次发出请求。文件内容大如下图所示，再次发出请求只要点击那个运行按钮即可。

如果从请求历史记录再次发出请求，则其执行信息和响应输出的链接将添加到请求历史记录文件的顶部。

![图片](https://mmbiz.qpic.cn/mmbiz_png/CvQa8Yf8vq2oEz6dCicKG4SodNzklEzWNhW3HWiaBTLz3HSm0Zq5IAvBpBGufhNtOhx7iapBbaicUVzqABHnvN0hyQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### **构建HTTP请求脚本** 

上面的历史记录就是一个完整的IDEA REST Client请求脚本，如果你是从控制台触发的，那么可以直接复制历史请求记录的文件放到项目里作为HTTP请求的脚本，给其他成员共享，如果不是，也可以直接新建一个.http或者.rest结尾的文件，IDEA会自动识别为HTTP请求脚本。

### **语法部分**

```
### 演示POST请求POST {{baseUrl}}}get?show_env=1Accept: application/json{   "name":"a"}### 演示GET请求GET {{baseUrl}}}/postContent-Type: application/x-www-form-urlencodedid=999&value=content
```

首先通过###三个井号键来分开每个请求体，然后请求url和header参数是紧紧挨着的，请求参数不管是POST的body传参还是GET的

parameter传参，都是要换行的

### 环境区分

细心的你可能发现了上面示例的代码，没有真实的请求地址，取而代之的，是一个{{baseUrl}}的占位符，这个就是IDEA REST Client真香的地方，支持从指定的配置文件中获取到环境相关的配置参数，不仅baseUrl可以通过占位符替换，一些请求的参数如果和接口环境相关的都可以通过配置文件来区分。

首先在.http的脚本同目录下创建一个名为http-client.private.env.json的文件，然后内容如下，一级的key值时用来区分环境的，比如，dev、uat、pro等，环境下的对象就是一次HTTP请求中能够获取到的环境变量了，你可以直接在请求的HTTP的脚本中通过{{xx}}占位符的方式获取到这里配置的参数

```
{  "uat":
      {    "baseUrl": "http://gateway.xxx.cn/",
            "username": "",    "password": ""
     },  "dev": {
          "baseUrl": "http://localhsot:8888/",
          "username": "",
          "password": ""
          }
}
```

那么在选择执行请求的时候，IDEA就会让你选执行那个环境的配置，如：

![图片](https://mmbiz.qpic.cn/mmbiz_png/CvQa8Yf8vq2oEz6dCicKG4SodNzklEzWNkvzxlXHU4CdUSnIm5bO7wez9QChPRc0xKVFqib8P78NQfwqxtUP4b0Q/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### **结果断言**

IDEA REST Client可以针对接口的响应值进行脚本化的断言处理，立马从一个接口调试工具上升到测试工具了，比如：

```
### Successful test: check response status is 200GET https://httpbin.org/status/200> {%client.test("Request executed successfully", function() {  client.assert(response.status === 200, "Response status is not 200");});%}
```

### 结果值暂存

试想下这样的场景，当一个系统需要通过认证才能访问的时候，如果用postman的时候，是不是先访问登录接口，然后获得token后，手动粘贴复制到新的调试接口的header参数里面去，这太麻烦了，IDEA REST Client还有一个真香的功能，可以完美解决这个问题，请看下面的脚本：

```
### 演示POST请求POST https://httpbin.org/postContent-Type: application/json{  "user": "admin",  "password": "123456"}> {% client.global.set("auth_token", response.body.json.token); %}### 演示GET请求GET https://httpbin.org/headersAuthorization: Bearer {{auth_token}}
```

在第一个认证的请求结束后，可以在response里拿到返回的token信息，然后我们通过脚本设置到了全局变量里，那么在接下来的接口请求中，就可以直接使用双大括号占位符的方式获取到这个token了

### **结语**

postman有口皆碑，确实是一个非常不错的必备工具，之前给比人推荐这种工具时总是安利他postman。

但是，IDEA REST Client也真的很不错，值得尝试一下，后面安利这种工具就切换到IDEA REST Client了，postman反正被我丢掉了。

和第三方做接口对接时，项目里必备一个rest-http.http接口请求文件，满足自己的同时也成方便了他人。



## 部门内 IDEA 分享，超实用技巧！

来源：https://segmentfault.com/a/1190000019977265

### 前言

> 工欲善其事
>
> 必先利其器

最近受部门的邀请，给入职新人统一培训IDEA，发现有很多新人虽然日常开发使用的是IDEA，但是还是很多好用的技巧没有用到，只是用到一些基本的功能，蛮浪费IDEA这个优秀的IDE。

同时，在这次分享之后，本人自己也学习到了一些新的使用技巧，所以借着这次机会，一起分享出来。希望可以帮到一些人。

> 基于的 IDEA 版本信息：IntelliJ IDEA 2018.2.2 (Ultimate Edition)

知识点概览：

- 高效率配置

- 日常使用 必备快捷键（★★）

- - 查找
  - 跳转切换
  - 编码相关
  - 代码阅读相关
  - 版本管理相关

- 编码效率相关（★★）

- - 文件代码模板
  - 实时代码模板
  - 其他

- 代码调试 源码阅读相关（★★★）

- - 视图模式
  - 代码调试
  - ...

- 插件方面

- - 插件的安装与使用
  - 插件推荐

- 参考



------

### 高效率配置

#### 1. 代码提示不区分大小写

```
Settings -> Editor -> General -> Code Completion
```

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMyykKtcCGeSAK6wmrq0XybibY0IT8bzz9KUP7uqpYVYBaB5of10oZmaBQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

(低版本 将 Case sensitive completion 设置为 None 就可以了)

#### 2. 自动导包功能及相关优化功能

```
Settings -> Editor -> General -> Auto Import
```

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMyKG2tbBXEDEAf3LTFbTWhqU8iaphDyeyslpZZAbywcmKykD2TqLdFtzQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

#### 3. CTRL + 滑动滚轮 调整窗口显示大小

```
Settings -> Editor -> General -> Change font size (Zoom) with Ctrl+Mouse wheel
```

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMyicmj7JYzRfHfr2RCxBp2BWaiaI8dxwwkiaQMYbYmrYvPBIBhUztOE9xsQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

选择之后，就可以通过CTRL+滑动滚轮的方式，调整编辑器窗口的字体大小

#### 4. tab 多行显示

这点因人而异，有些人喜欢直接取消所有tab，改用快捷键的方式，我屏幕比较大，所以喜欢把tab全部显示出来。

`Window -> Editor Tabs -> Tabs Placement`，取消勾选 `Show Tabs In Single Row`选项。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMyh6EMl6pnpX7Ucq1iaZDtfWG6a9YGbuHn581xGyHfhhxavTTJ9nsq7Wg/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

效果如下：

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMyyzswUiawyMOzsSMfyFzmgWyviaQJMSrK4fPVnbhtqiaj8lJmDniaD4HL7Q/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



#### 5. 代码编辑区显示行号

```
Settings -> Editor -> General -> Appearance `勾选 `Show Line Numbers
```

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMydU3icJdacSekxhzEx3Bic2CthWM625FIVXBGSFLKBAibnejU4SkeB7POg/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMyiaMPibphZ0gAogRf4ia4Y5dyhtKWoOOibxom2jKamO2doKCOnvYswD6Yfg/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

6....



### 日常使用 必备快捷键（★★）

#### 查找

| 快捷键                 | 介绍                         |
| ---------------------- | ---------------------------- |
| Ctrl + F               | 在当前文件进行文本查找       |
| Ctrl + R               | 在当前文件进行文本替换       |
| Shift + Ctrl + F       | 在项目进行文本查找           |
| Shift + Ctrl + R       | 在项目进行文本替换           |
| Shift + Shift          | 快速搜索                     |
| Ctrl + N               | 查找class                    |
| Ctrl + Shift + N       | 查找文件                     |
| Ctrl + Shift + Alt + N | 查找symbol（查找某个方法名） |

#### 跳转切换

| 快捷键           | 介绍                  |
| ---------------- | --------------------- |
| Ctrl + E         | 最近文件              |
| Ctrl + Tab       | 切换文件              |
| Ctrl + Alt + ←/→ | 跳转历史光标所在处    |
| Alt + ←/→ 方向键 | 切换子tab             |
| Ctrl + G         | go to（跳转指定行号） |

#### 编码相关

| 快捷键                      | 介绍                                                         |
| --------------------------- | ------------------------------------------------------------ |
| Ctrl + W                    | 快速选中                                                     |
| (Shift + Ctrl) + Alt + J    | 快速选中同文本                                               |
| Ctrl + C/Ctrl + X/Ctrl + D  | 快速复制或剪切                                               |
| 多行选中 Tab / Shift + Tab  | tab                                                          |
| Ctrl + Y                    | 删除整行                                                     |
| 滚轮点击变量/方法/类        | 快速进入变量/方法/类的定义处                                 |
| Shift + 点击Tab             | 快速关闭tab                                                  |
| Ctrl + Z 、Ctrl + Shift + Z | 后悔药，撤销/取消撤销                                        |
| Ctrl + Shift + enter        | 自动收尾，代码自动补全                                       |
| Alt + enter                 | IntelliJ IDEA 根据光标所在问题，提供快速修复选择，光标放在的位置不同提示的结果也不同 |
| Alt + ↑/↓                   | 方法快速跳转                                                 |
| F2                          | 跳转到下一个高亮错误 或 警告位置                             |
| Alt + Insert                | 代码自动生成，如生成对象的 set / get 方法，构造函数，toString() 等 |
| Ctrl + Shift + L            | 格式化代码                                                   |
| Shift + F6                  | 快速修改方法名、变量名、文件名、类名等                       |
| Ctrl + F6                   | 快速修改方法签名                                             |

#### 代码阅读相关

| 快捷键                     | 介绍                               |
| -------------------------- | ---------------------------------- |
| Ctrl + P                   | 方法参数提示显示                   |
| Ctrl + Shift + i           | 就可以在当前类里再弹出一个窗口出来 |
| Alt + F7                   | 可以列出变量在哪些地方被使用了     |
| 光标在子类接口名，Ctrl + u | 跳到父类接口                       |
| Alt + F1 + 1， esc         |                                    |
| (Shift) + Ctrl + +/-       | 代码块折叠                         |
| Ctrl + Shift + ←/→         | 移动窗口分割线                     |
| Ctrl + (Alt) + B           | 跳转方法定义/实现                  |
| Ctrl + H                   | 类的层级关系                       |
| Ctrl + F12                 | Show Members 类成员快速显示        |

#### 版本管理相关

| 快捷键       | 介绍             |
| ------------ | ---------------- |
| Ctrl + D     | Show Diff        |
| (Shift) + F7 | （上）下一处修改 |

> 更多快捷键请参考此文章 https://github.com/judasn/Int...
>
> **mac os** 快捷键请参考本文章 https://github.com/judasn/Int...

### 编码效率相关（★★）

#### 文件代码模板

```
Settings -> Editor -> File and Code Template
```

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMyW07KXuH00TBHUEfRaphPJgOYBCMhfFfl90VPfBu7bhYKQj65VnN6OQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

在这里可以看到IDEA所有内置的文件代码模板，当你选择某个文件生成时，就会按照这里面的模板生成指定的代码文件。

另外，你可以在这里设置文件头。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMy1xu4LdJzKq57EZd7dZh3oSfky7kbHkwHW5hFiaHBibyW6GTk3OVhO0Cg/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

设置之后，效果如下

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMybGvXAsib6ibDIszDRoxBLriboZjI9D6ibgUAmemZlyI05p3kib0iaUWh1U3Q/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

#### 实时代码模板

IDEA提供了强大的实时代码模板功能，并且原生内置了很多的模板，比如，当你输入`sout`或者`psvm`，就会快速自动生成`System.out.println();`和`public static void main(String[] args) {}`的代码块。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMy2EBBzMQssD6vRyc34Z0Ou9CzLdEeHIWjntME6y0uYRsCKbZ4YX4t7g/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMyicsxBPjK17lWJY5RjvwZibXO2jkBpCTNE11mkc40bRFVia9shQRibRGo4A/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

这些的模板可以在`Settings -> Editor -> Live Templates `看到。使用者可以按照自己的使用习惯来熟悉相关的代码模板。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMyrvWkrv3EHIsm7l6fnX0I4XJILLzrTibv5eRbu7XgTYTrwmCdic7ZS3LA/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

#### 定制代码模板

IDEA也提供自己定制实时代码模板的功能。

1. 创建自己的模板库

2. 创建定制的代码模板

   

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMy6nrTLzFbc3GTLydicicFicbnOSiaicZR4c1aaBsuVIiaia4viaFMHYBdEeTChQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

图中的`MyGroup`就存放着我自己定义的代码模板。

#### 其他

#### CRTL+ALT+T

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMyY7BXH1m8SUSK1ibnCD5IhmK14FLNRibibygnCIjYzqrKfiamoS80vshoXw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

`Ctrl + Alt + T` 提供的是代码块包裹功能 - Surround With。可以快速将选中的代码块，包裹到选择的语句块中。

#### 本地历史版本

IDEA 自带本地版本管理的功能，能够让你本地编写代码变得更加的安心和方便。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMyXFFazIVGl61xFL4KRVgG2BEZO6NNXRTh2veEM57Ybq77jPicpGSGRrg/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### 代码调试 源码阅读相关（★★★）

#### 视图模式

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMy7kqNLCiaDFJwEML0jEZ1SRoSJ5llYsb7RpuuBJq6kjxK2hwLCmHTADQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

IDEA提供两种特殊的视图模式，

1. Presentation Mode - 演示模式，专门用于Code Review这种需要展示代码的场景
2. Distraction Free Mode - 禅模式，专注于代码开发

#### 代码调试

##### 1. 条件断点

IDEA 可以设置指定条件的断点，增加我们调试的效率。[IntelliJ IDEA 调试 Java 8 Stream，](http://mp.weixin.qq.com/s?__biz=MzU2NjIzNDk5NQ==&mid=2247486106&idx=1&sn=2e9c161dee6c166293cc07ddd486a466&chksm=fcaed086cbd9599044c4bd3412a53dfcdfd785342f1bbfaa5efc704c0f08e2e59796ab472cd8&scene=21#wechat_redirect)推荐看下。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMyOibiauncia5SS2SofPBZJrxBqQZkzYjVMbAt41MRZ5z9DcfqyR5RvfIIw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

##### 2. 强制返回

IDEA 可以在打断点的方法栈处，强制返回你想要的方法返回值给调用方。非常灵活！

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMy42vDMibYt0kOicAXibQ4iagkzLpWEw0sZCEPU8ichJOquLgaibGKGpo0IzFA/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMynoZoCibEassBhvI59RI017ibCYW0hwopuyr6kaCgFCo9vxQ9XbibSwTRw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

##### 3. 模拟异常

IDEA 可以在打断点的方法栈处，强制抛出异常给调用方。这个在调试源码的时候非常有用。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMy2xtv8fgicLCCRUcYGFcSJMOYIeF7XS52lrcwEdxTkIy4x5jylDU83RA/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

##### 4. Evaluate Expression

IDEA 还可以在调试代码的时候，动态修改当前方法栈中变量的值，方便我们的调试。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMyu5bgnj4otHK1AGjxXIDbg7ZZLMFtvPuWIJdSYbQCEhe0cRHOAqwvjA/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### 插件方面

#### 插件安装

```
File -> Setting -> Plugin
```

插件安装，可以直接在IDEA的插件库中实时搜索安装。`browse plugin repository`

对于**网络不好**的用户，可以登录官方插件仓库地址：https://plugins.jetbrains.com...，下载压缩包之后，选择`install from disk`

#### 插件推荐

本人日常开发中使用的插件。

##### Alibaba Java Coding Guidelines

阿里Java编程规约插件。

##### FindBugs

代码缺陷扫描

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMy0SSK3RVKT2qEcbWTKg9QxdWuYj5gx73OmMRTD6LarR3Dmha0ENCQGA/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TC7wfaV18mQWSn3VswKolP8xYA57xDMyW8FKoXazn3gcmZos3WUCDO3eeTe8IM9LnGUr3ibMY0wkubzOJicfyQ6g/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

##### PMD

代码缺陷扫描

##### InnerBuilder

builder模式快速生成

![图片](https://mmbiz.qpic.cn/mmbiz_png/TC7wfaV18mQWSn3VswKolP8xYA57xDMyNdXhFic5JYygJHr7zaLTkO3ic149icK59JT6wKpbc6G16ETVAbrQGs0hQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

##### lombok plugin

lombok 插件

##### maven helper

maven 依赖管理助手 ，解析maven pom结构，分析冲突；

![图片](https://mmbiz.qpic.cn/mmbiz_png/TC7wfaV18mQWSn3VswKolP8xYA57xDMyp8MoppXSA0ib3aYIt4eejkkhiciaAa3zo00dr0VO4cvPYoicGQLn8iaRgFQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/TC7wfaV18mQWSn3VswKolP8xYA57xDMyUvOQfwU4m5n6wKB6Yia19sJCWdjKIoqThzYSwMUW1CrhK6R00KrCpFA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

##### Rainbow brackets

让代码中的括号更具标识性

![图片](https://mmbiz.qpic.cn/mmbiz_png/TC7wfaV18mQWSn3VswKolP8xYA57xDMy8z2DmOTRuogWQkRNiaPFLpRZddj7uryn1kaeI49DjQ8wYSdS7cbCEfg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

##### String Manipulation

String相关辅助简化，搭配 CTRL+W 、ALT+J等文本选择快捷键使用

![图片](https://mmbiz.qpic.cn/mmbiz_gif/TC7wfaV18mQWSn3VswKolP8xYA57xDMyrMOic4rj2equFR7TA5koLlicdkSXVIfeqvaOSBSxtiaPl9Haum9Onqqbw/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

##### Translation 

翻译插件，阅读源码必备

![图片](https://mmbiz.qpic.cn/mmbiz_png/TC7wfaV18mQWSn3VswKolP8xYA57xDMybtxu5G0YLJv1Iat1KAygkydI1ZKcPM4sqaH3DKCYHN2xibK93dhWyvQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/TC7wfaV18mQWSn3VswKolP8xYA57xDMyjnHuTbLzvsyh11QBb7oYAfLXQvlxN1U7HbhOACbULQgr0e3G2oKENg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

##### GenerateAllSetter

![图片](https://mmbiz.qpic.cn/mmbiz_gif/TC7wfaV18mQWSn3VswKolP8xYA57xDMyTtRpthr6ibyVLuPDgqibOvoDjRrQhy62ibMBAXN6za9PhygWjnEQictYbg/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

##### Generate SerialVersionUID 

`Alt` + `Insert` 快速生成SerialVersionUID

![图片](https://mmbiz.qpic.cn/mmbiz_gif/TC7wfaV18mQWSn3VswKolP8xYA57xDMyH6CQJo7sQ1Dh3FjUvrdIMibicAZ0k7ibf3AN5OeOzQRylUcNx4AcXOhFg/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

##### GsonFormat 

![图片](https://mmbiz.qpic.cn/mmbiz_gif/TC7wfaV18mQWSn3VswKolP8xYA57xDMy1YjTcjaYlLrJHst2LIGbvf4sc1Xbj1Kkd53b4NX5EfUxotOemicEXYA/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

##### RestfulToolkit 

1. 快速跳转到Restful Api处( use: Ctrl(Command) + or Ctrl + Alt + N )

2. 展示Resultful 接口结构

3. http 简单请求工具

   

![图片](https://mmbiz.qpic.cn/mmbiz_png/TC7wfaV18mQWSn3VswKolP8xYA57xDMy7tKGdopoEc4D4O3HSKxfdetlBXVafXuBJEAufzSyBpLmcz79UDFk4Q/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/TC7wfaV18mQWSn3VswKolP8xYA57xDMyVBiaamfpsO3qbiamHFORnBzXjDErpPfuMN0x63hiabESQ7e78CKF4icELQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

##### Material Theme UI

本人自用的主题就是这个。

![图片](https://mmbiz.qpic.cn/mmbiz_png/TC7wfaV18mQWSn3VswKolP8xYA57xDMy3XcNdXI6pZQmQWqSMu25HZLZbDvibDH8ZtGianbqiab2dLJhIEU2h0sBg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

##### MyBatis Log Plugin 

把 Mybatis 输出的sql日志还原成完整的sql语句，看起来更直观。

![图片](https://mmbiz.qpic.cn/mmbiz_png/TC7wfaV18mQWSn3VswKolP8xYA57xDMy5IYUx3uhJmE8ticicicoxicCfEOGGkqGsibffgf4l9b5SzPoWEau8siaVYZg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

##### Free Mybatis

MyBatis 免费的插件

#### 参考

https://github.com/judasn/IntelliJ-IDEA-Tutorial

(By the way, 更多IDEA使用请参考此延伸文档以及官方文档



## Intellij IDEA就这样配置，快到飞起！

*作者：琦彦*

blog.csdn.net/fly910905/article/details/77868300

### 目录

1.设置maven

2.IDEA 设置代码行宽度

3.IDEA 提示不区分大小写

4.IntelliJ强制更新Maven Dependencies

5.idea的环境配置默认保存位置

6.隐藏不想看到的文件或者文件夹（类似eclipse的filter功能）

7.修改为Eclipse快捷键

8.修改默认设置--default setting

9.修改智能提示快捷键

 10.查找快捷键冲突问题处理

11.显示行号

 12.代码智能提示，忽略大小写

13.用*标识编辑过的文件 

 14.关闭自动代码提示

15.常用快捷键

16.svn 不能同步代码问题修正

17.设置idea的SVN忽略掉*.iml文件

18.改变编辑文本字体大小

19.IDEA编码设置

 20.Live Templates

21.配置tomcat参数

22.idea安装插件的方法

23.调整idea启动时的内存配置参数

 24.导入eclipse web项目发布到Tomcat如果找不到

 25.每次打开一个新jsp或java文件时,cpu都占用很高,去掉检验即可

 26.idea增加spring/struts关联文件支持

\27. IDEA开启类修改后自动编译

 28.提示实现Serializable接口

29.演出模式

30.神奇的Inject language

31.强大的symbol

32.idea快捷键和Windows默认快捷键冲突解决（如：Ctrl+Alt+↑或Ctrl+Alt+F12）

33.格式化代码时，注释被格式化问题

\34. import导入报错，更新maven提示Unable to import maven project: See logs for details

\35. IDEA2019版显示出Run Dashboard

36.切换大小写

\37. 在IDEA中批量删除代码的注释

38.忽略css、js文件报错

39.Terminal替换成Git Bash

------

### 1.设置maven

> 1. 在File->settings->搜索maven
> 2. Mavan home directory--设置maven安装包的bin文件夹所在的位置
> 3. User settings file--设置setting文件所在的位置
> 4. Local repository--设置本地仓库的

### 2.IDEA 设置代码行宽度

> 1. 在File->settings->Editor->CodeStyle
> 2. 有人会问，如果输入的代码超出宽度界线时，如何让IDE自动将代码换行？有两种方式！
> 3. 第一种，在上述的“Right margin (columns)”的下方，有“Wrap when typing reaches right margin”选项，选中它，是什么效果呢？
> 4. 随着输入的字符的增加，当代码宽度到达界线时，IDEA会自动将代码换行。
> 5. 第一种方式是在输入代码时触发，还有第二种方式，在File->settings->CodeStyle->Java中，选中“Wrapping and Braces”选项卡，
> 6. 在“Keep when reformatting”中有一个“Ensure rigth margin is not exceeded”，选中它，是什么效果呢？
> 7. 从配置项的字面意思很容易理解，在格式化Java代码时，确保代码没有超过宽度界线。
> 8. 即输入的代码超出界线后，

### 3.IDEA 提示不区分大小写

> 1. 首先打开File----->setting
> 2. 然后，输入：sensitive
> 3. 将右侧的case sensitive completion 修改为NONE

### 4.IntelliJ强制更新Maven Dependencies

> 1.Intellj自动载入Mave依赖的功能很好用，但有时候会碰到问题，导致pom文件修改却没有触发自动重新载入的动作，此时需要手动强制更新依赖。
>
> 2.如下：
>
> 1. 手动删除ProjectSettings里面的Libraries内容；
> 2. 在MavenProject的试图里clean一下，删除之前编译过的文件；
> 3. 项目右键-》Maven-》Reimport
> 4. Ok，此时发现依赖已经建立！

### 5.idea的环境配置默认保存位置

> 1. idea的环境配置默认保存位置:C:\Users\xxxxxxxxx.IntelliJIdea14,xxxxxx代表用户目录,
> 2. 可以对该目录进行备份,一但环境出问题恢复此配置即可.
> 3. 可以在%IDEA_HOME%/bin/idea.properties中修改该配置路径.

### `6.隐藏不想看到的文件或者文件夹（类似eclipse的filter功能）`

> 1. intellij idea 隐藏不想看到的文件或者文件夹（类似eclipse的filter功能）
> 2. 打开intellij -->:>File-->>Settings-->>搜索FileTypes

### 7.修改为Eclipse快捷键

> 1. File->Settings->Keymap=>Keymaps改为Eclipse copy

### 8.修改默认设置--default setting

> 1. 修改默认设置--default setting

### 9.修改智能提示快捷键

> 1. File->Settings->Keymap->Main menu ->Code->Completion->Basic=>修改为Ctrl+Alt+Enter
> 2. 保存时把冲突的Remove掉。
> 3. File->Settings->Keymap->EditorActions->CompleteCurrentStatement=>修改为Ctrl+;

### 10.查找快捷键冲突问题处理

> 1. File->Settings->Keymap->Main menu ->Edit->Find=>修改Find...和Replace...分别改为Ctrl+F 和Ctrl+R

### 11.显示行号

> 1. File->Settings->Editor->General->Appearance=>Show line numbers选中

### 12.代码智能提示，忽略大小写

> 1. File->Settings -> Editor->CodeCompletion里把Case sensitive completion设置为None就可以了

### 13.用*标识编辑过的文件

> 1. Editor–>General–>EditorTabs
> 2. 在IDEA中，你需要做以下设置,这样被修改的文件会以*号标识出来，你可以及时保存相关的文件。
> 3. “Mark modifyied tabs with asterisk”

### 14.关闭自动代码提示

> 1. Preferences=> IDE Settings=>Editor=>CodeCompletion=>Autopopup documentation in (ms)

### 15.常用快捷键

> 1. ØTop#10切来切去：Ctrl+Tab
> 2. ØTop#9选你所想【选中上下文相关联代码】：Ctrl+W
> 3. ØTop#8代码生成：Template/Postfix+Tab
> 4. ØTop#7发号施令：Ctrl+Shift+A
> 5. ØTop#6无处藏身：Shift+Shift
> 6. ØTop#5自动完成：Ctrl+Shift+Enter
> 7. ØTop#4创造万物：Alt+Insert
>
> 使用前三名！
>
> 1. ØTop#1智能补全：Ctrl+Shift+Space
> 2. ØTop#1自我修复：Alt+Enter
> 3. ØTop#1重构一切：Ctrl+Shift+Alt+T
>
> 其他辅助
>
> 1. 以上这些神键配上一些辅助快捷键，即可让你的双手90%以上的时间摆脱鼠标，专注于键盘仿佛在进行钢琴表演。这些不起眼却是至关重要的最后一块拼图有：
> 2. Ø命令：Ctrl+Shift+A可以查找所有Intellij的命令，并且每个命令后面还有其快捷键。所以它不仅是一大神键，也是查找学习快捷键的工具。
> 3. Ø新建：Alt+Insert可以新建类、方法等任何东西。
> 4. Ø格式化代码：格式化import列表Ctrl+Alt+O，格式化代码Ctrl+Alt+L。
> 5. Ø切换窗口：Alt+Num，常用的有1-项目结构，3-搜索结果，4/5-运行调试。Ctrl+Tab切换标签页，Ctrl+E/Ctrl+Shift+E打开最近打开过的或编辑过的文件。
> 6. Ø单元测试：Ctrl+Alt+T创建单元测试用例。
> 7. Ø运行：Alt+Shift+F10运行程序，Shift+F9启动调试，Ctrl+F2停止。
> 8. Ø调试：F7/F8/F9分别对应Step into，Step over，Continue。
> 9. 此外还有些我自定义的，例如水平分屏Ctrl+|等，和一些神奇的小功能Ctrl+Shift+V粘贴很早以前拷贝过的，Alt+Shift+Insert(块选)进入到列模式进行按列选中

### 16.svn 不能同步代码问题修正

> File->Settings->Subversion->General=>Use command line client 选中
>
> 1. 使用command line方式需要指定svn.exe的路径,例如:D:\tools\TortoiseSVN\bin\svn.exe
> 2. 注意,安装TortoiseSVN时路径中不要带空格,例如:C:\Program Files\TortoiseSVN\bin\svn.exe就会报错.
> 3. 安装TortoiseSVN选择全部安装组件,否则可能没有svn.exe

### 17.设置idea的SVN忽略掉*.iml文件

> 1. Editor->FileTypes=>Ignore files and folders增加*.iml;
> 2. 在lgnore files and folesrs中输入.idea;注意要";"结尾。你就可以隐藏.idea文件夹了

### 18.改变编辑文本字体大小

> 1. File-> settings -> EDITOR COLORS & FONTS -> FONT -> SIZE

### 19.IDEA编码设置

> 1. FILE -> SETTINGS -> FILE ENCODINGS => IDE ENCODING
> 2. FILE -> SETTINGS -> FILE ENCODINGS =>ProjectEncoding
> 3. FILE -> SETTINGS -> FILE ENCODINGS =>Default encoding for properties files
> 4. FILE -> SETTINGS -> FILE ENCODINGS =>Transparentnative-to-ascii conversion

### 20.Live Templates

> System.out.println 快捷输出
>
> ```
> “abc”.sout =>System.out.println("abc");
> ```
>
> 在eclipse中使用方式为： `sysout=>System.out.println();`

> for循环
>
> ```
> List list =newArrayList();
> ```
>
> 输入: list.for即可输出
>
> ```
> for(String s:list){``}
> ```

### 21.配置tomcat参数

> 1. vm options:-Xms256m-Xmx512m-XX:PermSize=128m-XX:MaxPermSize=256m

### 22.idea安装插件的方法

> 1. 以IntelliJ IDEA 14.0.1安装findbugs插件为例：
> 2. (1)在线方式:进入File->setting->plugins->browse repositorits 搜索你要下载的插件名称，
> 3. 右侧可以找到下载地址,完成后按提示重启即可.
> 4. (2)离线安装:下载findbugs插件地址：http://plugins.jetbrains.com/plugin/3847,
> 5. 将下载的FindBugs-IDEA-0.9.994.zip,安装插件：进入File->setting->plugins=> Install plugin from disk...
> 6. 定位到到刚才下载的jar,点击ok,完成后按提示重启即可.
> 7. 插件安装的位置在C:\Users\xxxxxxxxx.IntelliJIdea14\config\plugins\插件名下.
> 8. 安装iBATIS/MyBatis min-plugin插件

### 23.调整idea启动时的内存配置参数

> 1. %IDEA_HOME%/bin/idea.exe.vmoptions

### 24.导入eclipse web项目发布到Tomcat如果找不到

> 1. 导入eclipse web项目发布到Tomcat如果找不到,可以在环境配置的Facets增加web支持,在Artifacts中增加项目部署模块名

### 25.每次打开一个新jsp或java文件时,cpu都占用很高,去掉检验即可

> 每次打开一个新jsp或java文件时,cpu都占用很高,去掉检验即可:
>
> ```
> file->settings->editor->inspections
> ```

### 26.idea增加spring/struts关联文件支持

> 1. project Settings->Modules->选中项目右键可添加

### 27. IDEA开启类修改后自动编译

> 1. File->setting->Buil,Execution,Deployment->compiler=>Make project automatically
> 2. 编译错误问题解决
> 3. Error:java:Compilation failed: internal java compiler error
> 4. set中Java complier 设置的问题，项目中有人用jdk1.6有人用jdk1.7版本不一样会一起这个错误

### 28.提示实现Serializable接口

> 1. 使用Eclipse或MyEclipse的同学可能知道，如果implementsSerializable接口时，会提示你生成 serialVersionUID。
> 2. 但Intellij IDEA 默认没启用这个功能。
> 3. Preferences->IEditor->nspections->Serialization issues->Serializableclass without ’serialVersionUID’，
> 4. 选中以上后，在你的class中：光标定位在类名前，按Alt+Enter就会提示自动创建 serialVersionUID了

### 29.演出模式

> 我们可以使用【Presentation Mode】，将IDEA弄到最大，可以让你只关注一个类里面的代码，进行毫无干扰的coding。
>
> 可以使用Alt+V快捷键，谈出View视图，然后选择Enter Presentation Mode。效果如下：

![图片](https://mmbiz.qpic.cn/mmbiz_png/eQPyBffYbueR7CSBl0cVRNuNiatHM4ofMxOn9WWBTx5WGibaVQweI05kIjQ6NemmFhviaqobDgUAuVtJITUvvCx6A/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

> 这个模式的好处就是，可以让你更加专注，因为你只能看到特定某个类的代码。可能读者会问，进入这个模式后，我想看其他类的代码怎么办？这个时候，就要考验你快捷键的熟练程度了。你可以使用CTRL+E弹出最近使用的文件。又或者使用CTRL+N和CTRL+SHIFT+N定位文件。

> 如何退出这个模式呢？很简单，使用ALT+V弹出view视图，然后选择Exit Presentation Mode 即可。
>
> 但是我强烈建议你不要这么做，因为你是可以在Enter Presentation Mode模式下在IDEA里面做任何事情的。当然前提是，你对IDEA足够熟练。

### 30.神奇的Inject language

> 如果你使用IDEA在编写JSON字符串的时候，然后要一个一个\去转义双引号的话，就实在太不应该了，又烦又容易出错。
>
> 在IDEA可以使用Inject language帮我们自动转义双引号。

- 先将焦点定位到双引号里面，使用alt+enter快捷键弹出inject language视图，并选中Inject language or reference。

![图片](https://mmbiz.qpic.cn/mmbiz_png/eQPyBffYbueR7CSBl0cVRNuNiatHM4ofMnCribaShKpTpOjEnZlJH7soqyibvL3E9oIlkhyU1nCMKH8DIGRuRibbibA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

- 选择后,切记，要直接按下enter回车键，才能弹出inject language列表。在列表中选择 json组件。

![图片](https://mmbiz.qpic.cn/mmbiz_png/eQPyBffYbueR7CSBl0cVRNuNiatHM4ofMK6wAAd90yZVWKKgh6pqr4iayG3AOGvLvJECrB6QyZYiaHg0ryCKh52HQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

- 选择完后。鼠标焦点自动会定位在双引号里面，这个时候你再次使用alt+enter就可以看到

![图片](https://mmbiz.qpic.cn/mmbiz_png/eQPyBffYbueR7CSBl0cVRNuNiatHM4ofMbeXjUibqaSQQ61y4AuM4Bjh1eQoEykF2WwmHM18xu7ysXgHMMUy5qpg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

- 选中Edit JSON Fragment并回车，就可以看到编辑JSON文件的视图了。

![图片](https://mmbiz.qpic.cn/mmbiz_png/eQPyBffYbueR7CSBl0cVRNuNiatHM4ofMu85Bib9wQP4F4YPrJU77uuzkdRuSxia94m8yXuIak14micGcVbfDlyUOQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

- 可以看到IDEA确实帮我们自动转义双引号了。如果要退出编辑JSON信息的视图，只需要使用ctrl+F4快捷键即可。
- Inject language可以支持的语言和操作多到你难以想象，读者可以自行研究。

### 31.强大的symbol

> 如果你依稀记得某个方法名字几个字母，想在IDEA里面找出来，可以怎么做呢？
>
> 直接使用ctrl+shift+alt+n，使用symbol来查找即可。

![图片](https://mmbiz.qpic.cn/mmbiz_png/eQPyBffYbueR7CSBl0cVRNuNiatHM4ofMR40qTWYjw8A7M4GSLlH51agIUHUPIv7M1oSOwO3smKmQ48DEe62Urg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### 32.idea快捷键和Windows默认快捷键冲突解决（如：Ctrl+Alt+↑或Ctrl+Alt+F12）

> 解决方式：在桌面右键 - 图形选项 - 快捷键 - 禁止 就可以了

### 33.格式化代码时，注释被格式化问题

解决方案

> 将enable javadoc formating取消掉

![图片](https://mmbiz.qpic.cn/mmbiz_png/eQPyBffYbueR7CSBl0cVRNuNiatHM4ofM6kbFPicgHNjHsvlmABQhok08PhAHD9mgcn8ktsUZ7I7l8Wiarkv6CqSg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### 34. import导入报错，更新maven提示Unable to import maven project: See logs for details

> IDEA2019和Maven3.6.2不兼容导致的，需要把Maven降级到3.6.1版本
>
> 或者使用idea自带的maven组件

![图片](https://mmbiz.qpic.cn/mmbiz_png/eQPyBffYbueR7CSBl0cVRNuNiatHM4ofMyX1FQYBGm08Q03sQjZGg6e1u1RGb3OZaDcwUJZ5jN9LmyWs0VSjNTQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### 35. IDEA2019版显示出Run Dashboard

> 1. 启动按钮，点击“Edit Configrations”
> 2. 左侧，选择Templates
> 3. 右侧，选择Configurations available in Run Dashboard
> 4. 点击“+”，选择Spring Boot

![图片](https://mmbiz.qpic.cn/mmbiz_png/eQPyBffYbueR7CSBl0cVRNuNiatHM4ofMNP2wjXDdIw8nmcXiaea62FWoV8f0q9GGaR978cDuiaj86POGYcpbqerg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### 36.切换大小写

> - idea的切换大小写的默认快捷键是ctrl+shift+u
> - 如果默认快捷键冲突，可以双击shift，输入Toggle Case

### 37. 在IDEA中批量删除代码的注释

> 先通过IDEA使用Ctrl+R(或者Ctrl+Shift+R()正则表达式替换
>
> (/\*([^*]|[\r\n]|(\*+([^*/]|[\r\n])))*\*+/|[ \t]*//.*)
>
> 或者
>
> (/\*([^*]|[\r\n]|(\*+([^*/]|[\r\n])))*\*+/)

![图片](https://mmbiz.qpic.cn/mmbiz_png/eQPyBffYbueR7CSBl0cVRNuNiatHM4ofMmkgh8FAOAgb66csAib1zHkOSicVe3wGiclpyFyf5A2eK6aibGNjgaCDOqQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

> 被替换以后格式会变乱，可以通过你自己的热键或者IDEA默认格式化（Ctrl+Alt+L）

### 38.忽略css、js文件报错

> - 选择需要处理的文件，按下快捷键：`ctrl+alt+shift+h`
> - 将高亮级别调到`None`即可
> - 不消失的话关闭重新打开文件，或重启IDEA

### 39.Terminal替换成Git Bash

> 1.IDEA Terminal替换成Git Bash
>
> 在IDEA中，打开settings，设置相应的bash路径
> `settings`–>`Tools`–>`Terminal`–>`Shell path: C:\Program Files\Git\bin\bash.exe`
>
> 2.解决git commit注释乱码的问题
>
> 在`C:\Program Files\Git\etc\bash.bashrc`末尾行追加如下内容：
>
> ```
> export LANG="zh_CN.UTF-8"
> export LC_ALL="zh_CN.UTF-8"
> ```
>
> 3.重启
>
> 重启IDEA或者关闭当前`Terminal`的`session`连接，然后`New Session`连接。

参考链接：

https://www.pianshen.com/article/61151292626/

https://blog.csdn.net/hanchao5272/article/details/79087934





# JAVA篇

## Java 8 中的方法引用，轻松减少代码量，提升可读性！

### 1. 引言

Java8中最受广大开发中喜欢的变化之一是因为引入了 lambda 表达式，因为这些表达式允许我们放弃匿名类，从而大大减少了样板代码，并提高了可读性。 **方法引用是lambda表达式的一种特殊类型**。它们通常通过引用现有方法来创建简单的lambda表达式。

方法引用包括以下四种类型：

- 静态方法
- 特定对象的实例方法
- 特定类型的任意对象的实例方法
- 构造方法

在本篇文章中，我们将探讨Java中的方法引用。

### 2. 引用静态方法

We'll begin with a very simple example, capitalizing and printing a list of *Strings*:

我们从一个非常简单的示例开始，字符串转成大写并打印：

```java
List<String> messages = Arrays.asList("hello", "baeldung", "readers!");
```

我们可以通过简单的lambda表达式直接调用 `StringUtils.capitalize()` 方法：

```java
messages.forEach(word -> StringUtils.capitalize(word));
```

或者，我们可以使用方法引用来简单地引用 `capitalize` 静态方法：

```java
messages.forEach(StringUtils::capitalize);
```

注意，方法引用应使用`::`运算符。

### 3. 引用特定对象的实例方法

为了演示这种类型的方法引用，我们新建以下这两个类：

```java
public class Bicycle {
 
    private String brand;
    private Integer frameSize;
    // standard constructor, getters and setters
}
 
public class BicycleComparator implements Comparator {
 
    @Override
    public int compare(Bicycle a, Bicycle b) {
        return a.getFrameSize().compareTo(b.getFrameSize());
    }
 
}
```

创建一个 BicycleComparator 对象来比较自行车尺寸：

```java
BicycleComparator bikeFrameSizeComparator = new BicycleComparator();
```

我们可以使用lambda表达式按尺寸大小对自行车进行排序，但需要指定两个自行车实例进行比较：

```java
createBicyclesList().stream()
  .sorted((a, b) -> bikeFrameSizeComparator.compare(a, b));
```

我们可以使用方法引用让编译器把句柄参数传递给我们：

```java
createBicyclesList().stream()
  .sorted(bikeFrameSizeComparator::compare);
```

### 4. 引用特定类型任意对象的实例方法

这种类型的方法引用与前面的示例类似，但不必创建自定义对象来执行比较。

让我们创建一个要排序的*Integer* 整数列表：

```
List<Integer> numbers = Arrays.asList(5, 3, 50, 24, 40, 2, 9, 18);
```

如果我们使用经典的 lambda 表达式，这两个参数都需要显式传递，而使用方法引用则要简单得多：

```java
numbers.stream()
  .sorted((a, b) -> a.compareTo(b));
numbers.stream()
  .sorted(Integer::compareTo);
```

尽管它仍然是一行代码，但是方法引用更容易阅读和理解。

### 5. 引用构造函数

我们可以像在第一个例子中引用静态方法一样引用构造函数。唯一区别是需要使用*new*关键字。现在我们用不同品牌的*String*列表创建一个*Bicycle*数组：

```
List<String> bikeBrands = Arrays.asList("Giant", "Scott", "Trek", "GT");
```

首先，我们将向*Bicycle*类添加一个新的构造函数：

```
public Bicycle(String brand) {
    this.brand = brand;
    this.frameSize = 0;
}
```

接下来，我们将使用方法引用中的新构造函数，并从原始的*String*列表中生成一个*Bicycle*数组：

```
bikeBrands.stream()
  .map(Bicycle::new)
  .toArray(Bicycle[]::new);
```

注意如何使用方法引用调用*Bicycle*和*Array*构造函数，从而使代码看起来更加简洁明了。

### 6. 其他示例和限制

目前为止，方法引用是一个使代码非常清晰和易读的好方法。但是，我们不能用它们来代替各种lambda表达式，因为它们有一些局限性。

它们的主要局限性是由于它们最大的优点：**前一个表达式的输出需要与引用的方法声明的输入参数匹配**。

看看这个限制的例子：

```
createBicyclesList().forEach(b -> System.out.printf(
  "Bike brand is '%s' and frame size is '%d'%n",
  b.getBrand(),
  b.getFrameSize()));
```

这个简单的例子不能用方法引用来表示，因为在我们的例子中，*printf* 方法需要3个参数，而使用*createBicyclesList().forEach()*只允许方法引用一个参数（*Bicycle*对象）。

**最后，我们研究下，如何创建一个可以从lambda表达式引用的no-operation函数。**

在本例中，我们希望使用lambda表达式而不使用其参数。

首先，创建 *doNothingAtAll* 方法：

```
private static <T> void doNothingAtAll(Object... o) {
}
```

因为这是一个varargs方法，它可执行在任意 lambda 表达式中，而不管引用的对象或参数的数量。我们看看它的作用：

```
createBicyclesList()
  .forEach((o) -> MethodReferenceExamples.doNothingAtAll(o));
```

### 7. Conclusion

在这篇文章中，我们学习了Java中的方法引用，以及如何使用它们来替换lambda表达式，从而提高了可读性并阐明编程的意图。



# Spring MVC篇

## 14 个 Spring MVC 顶级技巧，随时用随时爽，一直用一直爽

> 链接：blog.csdn.net/Summer_Lyf/article/details/102911215
>
> 

通常，在Spring MVC中，我们编写一个控制器类来处理来自客户端的请求。然后，控制器调用业务类来处理与业务相关的任务，然后将客户端重定向到逻辑视图名称，该名称由Spring的调度程序Servlet解析，以呈现结果或输出。



这样就完成了典型的请求-响应周期的往返。



今天整理了一下编写Spring MVC控制器的14个技巧，你今天get到了吗？(≧▽≦)/



### **1.使用@Controller构造型**

**
**

这是创建可以处理一个或多个请求的控制器类的最简单方法。仅通过用构造型注释一个类@Controller ，例如：

```
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
@Controller
public class HomeController {
    @RequestMapping("/")
    public String visitHome() {
      
        return "home";
    }
}
```

如你所见，visitHome()方法通过重定向到名为home的视图来处理来自应用程序上下文路径(/)的请求。

注意：@Controller原型只能在Spring的配置文件中启用注解驱动时使用:

```
<annotation-driven />
```

启用注释驱动时，Spring容器自动在以下语句指定的包下扫描类：

```
<context:component-scan base-package="net.codejava.spring" />
```

由@Controller 注释注释的类被配置为控制器。这是最可取的，因为它很简单：无需在配置文件中为控制器声明bean。

注意：通过使用@Controller 注解，您可以拥有一个多动作控制器类，该类能够处理多个不同的请求。例如：

```
@Controller
public class MultiActionController {
    @RequestMapping("/listUsers")
    public ModelAndView listUsers() {
    }
    @RequestMapping("/saveUser")
    public ModelAndView saveUser(User user) {
    }
    @RequestMapping("/deleteUser")
    public ModelAndView deleteUser(User user) {
    }
}
```

正如你可以在上面的控制器类看，有处理三种不同的请求3种处理方法 /listUsers，/saveUser，和/deleteUser分别。

### **2.实现控制器接口**

在Spring MVC中创建控制器的另一种（也许是经典的）方法是让类实现 Controller 接口。例如：

```
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import org.springframework.web.servlet.ModelAndView;
import org.springframework.web.servlet.mvc.Controller;
public class MainController implements Controller {
    @Override
    public ModelAndView handleRequest(HttpServletRequest request,
            HttpServletResponse response) throws Exception {
        System.out.println("Welcome main");
        return new ModelAndView("main");
    }
}
```

实现类必须重写该 handleRequest() 方法，当匹配请求进入时，该方法将由Spring调度程序Servlet调用。此控制器处理的请求URL模式在Spring的上下文配置文件中定义如下：

```
<bean name="/main" class="net.codejava.spring.MainController" />
```

但是，此方法的缺点是控制器类无法处理多个请求URL。

### **3.扩展AbstractController类**

如果要轻松控制受支持的HTTP方法，会话和内容缓存。扩展你的控制器 AbstractController 类是理想的选择。请考虑以下示例：

```
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import org.springframework.web.servlet.ModelAndView;
import org.springframework.web.servlet.mvc.AbstractController;
public class BigController extends AbstractController {
    @Override
    protected ModelAndView handleRequestInternal(HttpServletRequest request,
            HttpServletResponse response) throws Exception {
        System.out.println("You're big!");
        return new ModelAndView("big");
    }
}
```

这将创建具有有关受支持的方法，会话和缓存的配置的单动作控制器，然后可以在控制器的bean声明中指定这些配置。例如：

```
<bean name="/big" class="net.codejava.spring.BigController">
    <property name="supportedMethods" value="POST"/>
</bean>
```

此配置指示POST 此控制器的hander 方法仅支持该方法。

Spring MVC还提供了几种针对特定目的而设计的控制器类，包括：

- AbstractUrlViewController
- MultiActionController
- ParameterizableViewController
- ServletForwardingController
- ServletWrappingController
- UrlFilenameViewController

### **4.为处理程序方法指定URL映射**

这是编码控制器类时必须执行的强制性任务，该控制器类旨在处理一个或多个特定请求。Spring MVC提供了@RequestMapping 注释，该注解用于指定URL映射。例如：

```
@RequestMapping("/login")
```

这映射了/login 要由带注解的方法或类处理的URL模式。当在类级别使用此注解时，该类将成为单动作控制器。例如：

```
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
@Controller
@RequestMapping("/hello")
public class SingleActionController {
    @RequestMapping(method = RequestMethod.GET)
    public String sayHello() {
        return "hello";
    }
}
```

当@RequestMapping 注解在方法级别使用的，你可以有一个多动作控制器。例如：

```
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
@Controller
public class UserController {
    @RequestMapping("/listUsers")
    public String listUsers() {
        return "ListUsers";
    }
    @RequestMapping("/saveUser")
    public String saveUser() {
        return "EditUser";
    }
    @RequestMapping("/deleteUser")
    public String deleteUser() {
        return "DeleteUser";
    }
}
```

@RequestMapping注释还可以用于指定一个方法要处理的多个URL模式。例如:

```
@RequestMapping({"/hello", "/hi", "/greetings"})
```

此外，此注解还具有在某些情况下可能有用的其他属性，例如method。

### **5.为处理程序方法指定HTTP请求方法**

可以使用 注解的method 属性 指定处理程序方法支持哪种HTTP方法（GET，POST，PUT等） @RequestMapping。这是一个例子：

```
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
@Controller
public class LoginController {
    @RequestMapping(value = "/login", method = RequestMethod.GET)
    public String viewLogin() {
        return "LoginForm";
    }
    @RequestMapping(value = "/login", method = RequestMethod.POST)
    public String doLogin() {
        return "Home";
    }
}
```

此控制器有两个处理相同URL模式的方法/login，但前者用于 GET 方法，而后者用于 POST 方法。有关使用@RequestMapping 注解的更多信息，请参见 @RequestMapping注解。

### **6.将请求参数映射到处理程序方法**

Spring MVC的很酷的功能之一是，您可以使用@RequestParam 注解将请求参数作为处理程序方法的常规参数进行检索。这是将控制器HttpServletRequest 与Servlet API 的接口分离的好方法。

```
@RequestMapping(value = "/login", method = RequestMethod.POST)
public String doLogin(@RequestParam String username,
                      @RequestParam String password) {
}
```

Spring将方法参数用户名和密码绑定到具有相同名称的HTTP请求参数。这意味着您可以按以下方式调用URL（如果请求方法是GET）：

```
http：// localhost：8080 / spring / login？username = scott＆password = tiger
```

类型转换也是自动完成的。例如，如果您声明integer 如下类型的参数 ：

```
@RequestParam int securityNumber
```

然后，Spring将在处理程序方法中自动将请求参数（字符串）的值转换为指定的类型（整数）。

如果参数名称与变量名称不同，则可以如下指定参数的实际名称：

```
@RequestParam("SSN") int securityNumber
```

该@RequestParam 注解也有两个额外的属性，这可能是在某些情况下是有用的。该属性指定参数是否为必需。例如：required

```
@RequestParam(required = false) String country
```

这意味着该参数 country 是可选的；因此，它可能会从请求中丢失。在上面的示例中，country 如果请求中不存在此类参数，则变量 将为null。

另一个属性是 defaultValue，可以在请求参数为空时用作后备值。例如：

```
@RequestParam(defaultValue = "18") int age
```

Map 如果方法参数是type，Spring还允许我们将所有参数作为对象 访问 Map<String, String>。例如：

```
doLogin(@RequestParam Map<String, String> params)
```

然后，映射参数包含键-值对形式的所有请求参数。有关使用@RequestParam 注释的更多信息，请参见 @RequestParam注解。

### **7.返回模型和视图**

处理完业务逻辑后，处理程序方法应返回一个视图，然后由Spring的调度程序servlet对其进行解析。Spring允许我们ModelAndView 从handler 方法中返回String或 对象 。

在以下示例中，该 handler 方法返回一个String并表示一个名为的视图 LoginForm：

```
@RequestMapping(value = "/login", method = RequestMethod.GET)
public String viewLogin() {
    return "LoginForm";
}
```

这是返回视图名称的最简单方法。但是，如果要将其他数据发送到视图，则必须返回一个 ModelAndView 对象。考虑以下处理程序方法：

```
@RequestMapping("/listUsers")
public ModelAndView listUsers() {
    List<User> listUser = new ArrayList<>();
    // 从DAO获取用户列表…
    ModelAndView modelView = new ModelAndView("UserList");
    modelView.addObject("listUser", listUser);
    return modelView;
}
```

如您所见，此处理程序方法返回一个 ModelAndView 保存视图名称 UserList 的User 对象和一个可在视图中使用的对象集合 。Spring 面试 7 大问题，推荐看下。

Spring也非常灵活，因为您可以将ModelAndView 对象声明 为处理程序方法的参数，而不用创建一个新的对象。因此，以上示例可以重写如下：

```
@RequestMapping("/listUsers")
public ModelAndView listUsers(ModelAndView modelView) {
    List<User> listUser = new ArrayList<>();
    //从DAO获取用户列表…
    modelView.setViewName("UserList");
    modelView.addObject("listUser", listUser);
    return modelView;
}
```

了解有关该类的更多信息，请参见：ModelAndView class。

### **8.将对象放入模型**

在遵循MVC架构的应用程序中，控制器（C）应该将数据传递到模型（M）中，然后在视图（V）中使用该模型。正如我们在前面的示例中看到的那样， 该类的addObject() 方法 ModelAndView是以名称-值对的形式将对象放入模型中：

```
modelView.addObject("listUser", listUser);
modelView.addObject("siteName", new String("CodeJava.net"));
modelView.addObject("users", 1200000);
```

同样，Spring非常灵活。你可以Map 在处理程序方法中声明类型的参数 。Spring使用此映射存储模型的对象。让我们看另一个例子：

```
@RequestMapping(method = RequestMethod.GET)
public String viewStats(Map<String, Object> model) {
    model.put("siteName", "CodeJava.net");
    model.put("pageviews", 320000);
    return "Stats";
}
```

这比使用ModelAndView 对象还要简单 。根据你的喜好，可以使用Map 或 使用 ModelAndView 对象。在这里要感谢Spring的灵活性。

### **9.处理程序方法中的重定向**

如果你希望在满足条件的情况下将用户重定向到另一个URL，请redirect:/ 在URL之前追加。以下代码段给出了一个示例：

```
// 检查登录状态....
if (!isLogin) {
    return new ModelAndView("redirect:/login");
}
// 返回用户列表
```

在上面的代码中，/login 如果未登录，用户将被重定向到该 URL。

### **10.处理表格提交和表格验证**

通过提供@ModelAttribute 用于将表单字段绑定到表单支持对象的注解以及BindingResult 用于验证表单字段的界面，Spring使处理表单提交变得容易。下面的代码片段显示了一种典型的处理程序方法，该方法负责处理和验证表单数据：

```
@Controller
public class RegistrationController {
    @RequestMapping(value = "/doRegister", method = RequestMethod.POST)
    public String doRegister(
        @ModelAttribute("userForm") User user, BindingResult bindingResult) {
        if (bindingResult.hasErrors()) {
            // 表单验证错误
        } else {
            // 表单输入没问题
        }
        // 注册过程……
        return "Success";
    }
}
```

从Spring的官方文档中了解有关@ModelAttribute 注释和BindingResult 接口的更多信息：

- 在方法参数上使用@ModelAttribute
- 在方法上使用@ModelAttribute
- 接口绑定结果

### **11.处理文件上传**

通过自动将上传数据绑定到CommonsMultipartFile 对象数组，Spring还使在处理程序方法中处理文件上传变得容易。Spring使用Apache Commons FileUpload作为基础的多部分解析器。

以下代码段显示了从客户端上传文件有多么容易

```
@RequestMapping(value = "/uploadFiles", method = RequestMethod.POST)
public String handleFileUpload(
        @RequestParam CommonsMultipartFile[] fileUpload) throws Exception {
    for (CommonsMultipartFile aFile : fileUpload){
        // 存储上传的文件
        aFile.transferTo(new File(aFile.getOriginalFilename()));
    }
    return "Success";
}
```

### **12.在控制器中自动装配业务类**

控制器应将业务逻辑的处理委托给相关的业务类。为此，您可以使用@Autowired 注解让Spring自动将业务类的实际实现注入控制器。

考虑以下控制器类的代码段：

```
@Controller
public class UserController {
    @Autowired
    private UserDAO userDAO;
    public String listUser() {
        // 列出所有用户的处理方法
        userDAO.list();
    }
    public String saveUser(User user) {
        // 保存/更新用户的处理方法
        userDAO.save(user);
    }
    public String deleteUser(User user) {
        // 删除用户的处理方法
        userDAO.delete(user);
    }
    public String getUser(int userId) {
        // 获取用户的处理方法
        userDAO.get(userId);
    }
}
```

在此，与用户管理有关的所有业务逻辑都由该UserDAO 接口的实现提供 。例如：

```
interface UserDAO {
    List<User> list();
    void save(User user);
    void checkLogin(User user);
}
```

有关@Autowired 注解的更多信息，请参见 注释类型自动装配。

### **13.访问HttpServletRequest和HttpServletResponse**

在某些情况下，您需要直接 在处理程序方法中访问 HttpServletRequest 或 HttpServletResponse对象。

通过Spring的灵活性，只需在处理方法中添加相关参数即可。例如：

```
@RequestMapping("/download")
public String doDownloadFile(
        HttpServletRequest request, HttpServletResponse response) {
    // 访问请求
    // 访问响应
    return "DownloadPage";
}
```

Spring检测并自动将 HttpServletRequest 和 HttpServletResponse 对象注入方法中。然后，可以访问请求和响应如获取 InputStream， OutputStream或返回一个特定的HTTP代码。

### **14.遵循单一责任原则**

最后，在设计和编写Spring MVC控制器时，有两个很好的实践是你应该遵循的:

1）控制器类不应执行业务逻辑。相反，它应该将业务处理委托给相关的业务类别。这使控制器始终专注于其设计职责是控制应用程序的工作流程。例如：

```
@Controller
public class UserController {
    @Autowired
    private UserDAO userDAO;
    public String listUser() {
        userDAO.list();
    }
    public String saveUser(User user) {
        userDAO.save(user);
    }
    public String deleteUser(User user) {
        userDAO.delete(user);
    }
    public String getUser(int userId) {
        userDAO.get(userId);
    }
}
```

2）为每个业务域创建每个单独的控制器。例如， UserController 用于控制用户管理的OrderController 工作流程， 用于控制订单处理的工作流程等。例如：

```
@Controller
public class UserController {
}
@Controller
public class ProductController {
}
@Controller
public class OrderController {
}
@Controller
public class PaymentController {
}
```

这14个小技巧，可以帮助你正确有效地在Spring MVC中编写控制器类。如果你有其他提示或建议，请随时在评论中分享您的想法。



# Spring Boot注解篇

## 超级全面的 SpringBoot 注解介绍，每一个用途都应该清晰

*作者：riemann*

blog.csdn.net/qq_34371461/article/details/80571281

### 一、注解(annotations)列表

1、@SpringBootApplication

包含了`@ComponentScan`、`@Configuration`和`@EnableAutoConfiguration`注解。
其中`@ComponentScan`让`Spring Boot`扫描到`Configuration`类并把它加入到程序上下文。

2、@ComponentScan

组件扫描，可自动发现和装配一些`Bean`。

3、@Configuration

等同于`Spring`的`XML`配置文件；使用`Java`代码可以检查类型安全。

4、@EnableAutoConfiguration

自动配置

5、@RestController

该注解是`@Controller`和`@ResponseBody`的合集,表示这是个控制器`Bean`,并且是将函数的返回值直接填入`HTTP`响应体中,是`REST`风格的控制器。

6、@Autowired

自动导入。

7、@PathVariable

获取参数。

8、@JsonBackReference

解决嵌套外链问题。

9、@RepositoryRestResourcepublic

配合spring-boot-starter-data-rest使用。

### 二、注解(annotations)详解

1、`@SpringBootApplication`：申明让`Spring Boot`自动给程序进行必要的配置，这个配置等同于：`@Configuration` ，`@EnableAutoConfiguration` 和 `@ComponentScan` 三个配置。

```
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication // same as @Configuration @EnableAutoConfiguration @ComponentScan
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

2、`@ResponseBody`：表示该方法的返回结果直接写入`HTTP Response Body`中，一般在异步获取数据时使用，用于构建`RESTful`的`api`。

在使用`@RequestMapping`后，返回值通常解析为跳转路径，加上`@ResponseBody`后返回结果不会被解析为跳转路径，而是直接写入`HTTP Response Body`中。

比如异步获取`json`数据，加上`@ResponseBody`后，会直接返回`json`数据。

该注解一般会配合`@RequestMapping`一起使用。

示例代码：

```
@RequestMapping(“/test”)
@ResponseBody
public String test(){
    return ”ok”;
}
```

3、`@Controller`：用于定义控制器类，在`spring` 项目中由控制器负责将用户发来的`URL`请求转发到对应的服务接口（`service`层）

一般这个注解在类中，通常方法需要配合注解`@RequestMapping`。

示例代码：

```
@Controller
@RequestMapping(“/demoInfo”)
publicclass DemoController {
    @Autowired
    private DemoInfoService demoInfoService;

    @RequestMapping("/hello")
    public String hello(Map map){
        System.out.println("DemoController.hello()");
        map.put("hello","from TemplateController.helloHtml");
        // 会使用hello.html或者hello.ftl模板进行渲染显示.
        return"/hello";
    }
}
```

4、`@RestController`：用于标注控制层组件(如`struts`中的`action`)，`@ResponseBody`和`@Controller`的合集。

示例代码：

```
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping(“/demoInfo2”)
publicclass DemoController2 {

    @RequestMapping("/test")
    public String test(){
        return"ok";
    }
}
```

5、`@RequestMapping`：提供路由信息，负责`URL`到`Controller`中的具体函数的映射。

6、`@EnableAutoConfiguration`：`Spring Boot`自动配置（`auto-configuration`）：尝试根据你添加的`jar`依赖自动配置你的`Spring`应用。

例如，如果你的`classpath`下存在HSQLDB，并且你没有手动配置任何数据库连接`beans`，那么我们将自动配置一个内存型（`in-memory`）数据库”。

你可以将`@EnableAutoConfiguration`或者`@SpringBootApplication`注解添加到一个`@Configuration`类上来选择自动配置。

如果发现应用了你不想要的特定自动配置类，你可以使用`@EnableAutoConfiguration`注解的排除属性来禁用它们。



7、`@ComponentScan`：表示将该类自动发现扫描组件。

个人理解相当于，如果扫描到有`@Component`、`@Controller`、`@Service`等这些注解的类，并注册为`Bean`，可以自动收集所有的`Spring`组件，包括`@Configuration`类。

我们经常使用`@ComponentScan`注解搜索`beans`，并结合`@Autowired`注解导入。可以自动收集所有的`Spring`组件，包括`@Configuration`类。

如果没有配置的话，`Spring Boot`会扫描启动类所在包下以及子包下的使用了`@Service`、`@Repository`等注解的类。

8、`@Configuration`：相当于传统的`xml`配置文件，如果有些第三方库需要用到`xml`文件，建议仍然通过`@Configuration`类作为项目的配置主类——可以使用`@ImportResource`注解加载`xml`配置文件。

9、`@Import`：用来导入其他配置类。

10、`@ImportResource`：用来加载`xml`配置文件。

11、`@Autowired`：自动导入依赖的`bean`

12、`@Service`：一般用于修饰`service`层的组件

13、`@Repository`：使用`@Repository`注解可以确保`DAO`或者`repositories`提供异常转译，这个注解修饰的`DAO`或者`repositories`类会被`ComponetScan`发现并配置，同时也不需要为它们提供`XML`配置项。

14、`@Bean`：用`@Bean`标注方法等价于`XML`中配置的`bean`。

15、`@Value`：注入`Spring boot` `application.properties`配置的属性的值。示例代码：

```
@Value(value = “#{message}”)
private String message;
```

16、`@Inject`：等价于默认的`@Autowired`，只是没有`required`属性；

17、`@Component`：泛指组件，当组件不好归类的时候，我们可以使用这个注解进行标注。

18、`@Bean`：相当于`XML`中的,放在方法的上面，而不是类，意思是产生一个`bean`,并交给`spring`管理。

19、`@AutoWired`：自动导入依赖的`bean`。`byType`方式。把配置好的`Bean`拿来用，完成属性、方法的组装，它可以对类成员变量、方法及构造函数进行标注，完成自动装配的工作。当加上（`required=false`）时，就算找不到`bean`也不报错。

20、`@Qualifier`：当有多个同一类型的`Bean`时，可以用`@Qualifier(“name”)`来指定。与`@Autowired`配合使用。`@Qualifier`限定描述符除了能根据名字进行注入，但能进行更细粒度的控制如何选择候选者，具体使用方式如下：

```
@Autowired
@Qualifier(value = “demoInfoService”)
private DemoInfoService demoInfoService;
```

21、`@Resource(name=”name”,type=”type”)`：没有括号内内容的话，默认`byName`。与`@Autowired`干类似的事。



### 三、JPA注解

1、`@Entity`：`@Table(name=”“)`：表明这是一个实体类。一般用于`jpa`这两个注解一般一块使用，但是如果表名和实体类名相同的话，`@Table`可以省略。

2、`@MappedSuperClass`:用在确定是父类的`entity`上。父类的属性子类可以继承。

3、`@NoRepositoryBean`:一般用作父类的`repository`，有这个注解，`Spring`不会去实例化该`repository`。

4、`@Column`：如果字段名与列名相同，则可以省略。

5、`@Id`：表示该属性为主键。

6、`@GeneratedValue(strategy=GenerationType.SEQUENCE,generator= “repair_seq”)`：表示主键生成策略是`sequence`（可以为`Auto`、`IDENTITY`、`native`等，`Auto`表示可在多个数据库间切换），指定`sequence`的名字是`repair_seq`。

7、`@SequenceGeneretor(name = “repair_seq”, sequenceName = “seq_repair”, allocationSize = 1)`：`name`为`sequence`的名称，以便使用，`sequenceName`为数据库的`sequence`名称，两个名称可以一致。

8、`@Transient`：表示该属性并非一个到数据库表的字段的映射,`ORM`框架将忽略该属性。

如果一个属性并非数据库表的字段映射,就务必将其标示为`@Transient`,否则,`ORM`框架默认其注解为`@Basic`。

9、`@Basic(fetch=FetchType.LAZY)`：标记可以指定实体属性的加载方式。

10、`@JsonIgnore`：作用是`json`序列化时将`Java bean`中的一些属性忽略掉,序列化和反序列化都受影响。

11、`@JoinColumn（name=”loginId”）`:一对一：本表中指向另一个表的外键。一对多：另一个表指向本表的外键。

12、`@OneToOne、@OneToMany、@ManyToOne`：对应`hibernate`配置文件中的一对一，一对多，多对一。

### 四、SpringMVC相关注解

1、`@RequestMapping`：`@RequestMapping(“/path”)`表示该控制器处理所有“/path”的UR L请求。

`RequestMapping`是一个用来处理请求地址映射的注解，可用于类或方法上。

用于类上，表示类中的所有响应请求的方法都是以该地址作为父路径。该注解有六个属性：

- `params`:指定`request`中必须包含某些参数值是，才让该方法处理。
- `headers`:指定`request`中必须包含某些指定的`header`值，才能让该方法处理请求。
- `value`:指定请求的实际地址，指定的地址可以是`URI Template` 模式
- `method`:指定请求的method类型， `GET、POST、PUT、DELETE`等
- `consumes`:指定处理请求的提交内容类型（`Content-Type`），如`application/json,text/html`;
- `produces`:指定返回的内容类型，仅当`request`请求头中的(`Accept`)类型中包含该指定类型才返回。

2、`@RequestParam`：用在方法的参数前面。

3、`@PathVariable`:路径变量。如：

```
RequestMapping(“user/get/{macAddress}”)
public String getByMacAddress(@PathVariable String macAddress){
    //do something;
}
```

参数与大括号里的名字一样要相同。

### 五、全局异常处理

`@ControllerAdvice`：包含`@Component`。可以被扫描到。统一处理异常。

`@ExceptionHandler（Exception.class）`：用在方法上面表示遇到这个异常就执行以下方法。





# Docker篇

## 牛逼！Docker从入门到上瘾

### **容器简介**

#### **什么是 Linux 容器**

Linux容器是与系统其他部分隔离开的一系列进程，从另一个镜像运行，并由该镜像提供支持进程所需的全部文件。



容器提供的镜像包含了应用的所有依赖项，因而在从开发到测试再到生产的整个过程中，它都具有可移植性和一致性。



![图片](https://mmbiz.qpic.cn/mmbiz_png/oTKHc6F8tsiaicIibGNyuxJNbNay2XqjcyNJHb3Q3iaoePFedxGK0NdPncQfl6aotsbonTG2FicsX4Bziaw97H4FgQUw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)





更加详细地来说，请您假定您在开发一个应用。您使用的是一台笔记本电脑，而且您的开发环境具有特定的配置。其他开发人员身处的环境配置可能稍有不同。您正在开发的应用依赖于您当前的配置，还要依赖于某些特定文件。



与此同时，您的企业还拥有标准化的测试和生产环境，且具有自身的配置和一系列支持文件。



您希望尽可能多在本地模拟这些环境，而不产生重新创建服务器环境的开销。



因此，您要如何确保应用能够在这些环境中运行和通过质量检测，并且在部署过程中不出现令人头疼的问题，也无需重新编写代码和进行故障修复？答案就是使用容器。



容器可以确保您的应用拥有必需的配置和文件，使得这些应用能够在从开发到测试、再到生产的整个流程中顺利运行，而不出现任何不良问题。这样可以避免危机，做到皆大欢喜。



虽然这只是简化的示例，但在需要很高的可移植性、可配置性和隔离的情况下，我们可以利用 Linux 容器通过很多方式解决难题。



无论基础架构是在企业内部还是在云端，或者混合使用两者，容器都能满足您的需求。



#### **容器不就是虚拟化吗**

是，但也不竟然。我们用一种简单方式来思考一下：



虚拟化使得许多操作系统可同时在单个系统上运行。



容器则可共享同一个操作系统内核，将应用进程与系统其他部分隔离开。



![图片](https://mmbiz.qpic.cn/mmbiz_png/oTKHc6F8tsiaicIibGNyuxJNbNay2XqjcyNttwRxBsGRT1zsefq4qcWZO9lPmsSpiaS9VIMRSF7a20APn22Vn4lNqQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



图 - 普通虚拟化技术和Docker的对比



这意味着什么？首先，让多个操作系统在单个虚拟机监控程序上运行以实现虚拟化，并不能达成和使用容器同等的轻量级效果。



事实上，在仅拥有容量有限的有限资源时，您需要能够可以进行密集部署的轻量级应用。



Linux 容器可从单个操作系统运行，在所有容器中共享该操作系统，因此应用和服务能够保持轻量级，并行快速运行。



#### **容器发展简史** 

![图片](https://mmbiz.qpic.cn/mmbiz_png/oTKHc6F8tsiaicIibGNyuxJNbNay2XqjcyNNC2uBib5YZeRTnyY86wBNeOVicVUQDj8LKpD5TUibRBArAxd2M6tHtDrw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



我们现在称为容器技术的概念最初出现在 2000 年，当时称为 FreeBSD jail，这种技术可将 FreeBSD 系统分区为多个子系统（也称为 Jail）。



Jail 是作为安全环境而开发的，系统管理员可与企业内部或外部的多个用户共享这些 Jail。



Jail 的目的是让进程在经过修改的 chroot 环境中创建，而不会脱离和影响整个系统 — 在 chroot 环境中，对文件系统、网络和用户的访问都实现了虚拟化。



尽管 Jail 在实施方面存在局限性，但最终人们找到了脱离这种隔离环境的方法。



但这个概念非常有吸引力。



2001 年，通过 Jacques Gélinas 的 VServer 项目，隔离环境的实施进入了 Linux 领域。



正如 Gélinas 所说，这项工作的目的是“在高度独立且安全的单一环境中运行多个通用 Linux 服务器 [sic]。” 



在完成了这项针对 Linux 中多个受控制用户空间的基础性工作后，Linux 容器开始逐渐成形并最终发展成了现在的模样。



### **什么是 Docker？**

“Docker” 一词指代多种事物，包括开源社区项目、开源项目使用的工具、主导支持此类项目的公司 Docker Inc. 以及该公司官方支持的工具。技术产品和公司使用同一名称，的确让人有点困惑。



我们来简单说明一下：

🎍 IT 软件中所说的 “Docker” ，是指容器化技术，用于支持创建和使用 Linux 容器。



🎍 开源 Docker 社区致力于改进这类技术，并免费提供给所有用户，使之获益。



🎍 Docker Inc. 公司凭借 Docker 社区产品起家，它主要负责提升社区版本的安全性，并将改进后的版本与更广泛的技术社区分享。此外，它还专门对这些技术产品进行完善和安全固化，以服务于企业客户。



借助 Docker ，您可将容器当做重量轻、模块化的虚拟机使用。同时，您还将获得高度的灵活性，从而实现对容器的高效创建、部署及复制，并能将其从一个环境顺利迁移至另一个环境。



#### **Docker 如何工作？**

Docker 技术使用 Linux 内核和内核功能（例如 Cgroups 和 namespaces）来分隔进程，以便各进程相互独立运行。



这种独立性正是采用容器的目的所在；它可以独立运行多种进程、多个应用程序，更加充分地发挥基础设施的作用，同时保持各个独立系统的安全性。



容器工具（包括 Docker）可提供基于镜像的部署模式。这使得它能够轻松跨多种环境，与其依赖程序共享应用或服务组。Docker 还可在这一容器环境中自动部署应用程序（或者合并多种流程，以构建单个应用程序）。



此外，由于这些工具基于 Linux 容器构建，使得 Docker 既易于使用，又别具一格 —— 它可为用户提供前所未有的高度应用程访问权限、快速部署以及版本控制和分发能力。



#### **Docker 技术是否与传统的 Linux 容器相同？**

否。Docker 技术最初是基于 LXC 技术构建（大多数人都会将这一技术与“传统的” Linux 容器联系在一起），但后来它逐渐摆脱了对这种技术的依赖。



**就轻量级 虚拟化 这一功能来看，LXC 非常有用**，但它无法提供出色的开发人员或用户体验。除了运行容器之外，Docker 技术还具备其他多项功能，包括简化用于构建容器、传输镜像以及控制镜像版本的流程。



![图片](https://mmbiz.qpic.cn/mmbiz_png/oTKHc6F8tsiaicIibGNyuxJNbNay2XqjcyNSTduDPY6VjYcM953tjoDMvSQ7NQRIB4iadxRetGb582Fz7t2wBkJIyw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)





传统的 Linux 容器使用 init 系统来管理多种进程。这意味着，所有应用程序都作为一个整体运行。与此相反，Docker 技术鼓励应用程序各自独立运行其进程，并提供相应工具以实现这一功能。这种精细化运作模式自有其优势。



#### **docker的目标**

docker的主要目标是"Build,Ship and Run any App,Angwhere",构建，运输，处处运行

- **构建：**做一个docker镜像
- **运输：**docker pull
- **运行：**启动一个容器



每一个容器，他都有自己的文件系统rootfs.

### **安装Docker**

环境说明

```
# 需要两台几点进行安装
[root@docker01 ~]# cat /etc/redhat-release 
CentOS Linux release 7.2.1511 (Core) 
[root@docker01 ~]# uname  -r 
3.10.0-327.el7.x86_64
[root@docker01 ~]# hostname -I
10.0.0.100 172.16.1.100 
[root@docker02 ~]# hostname -I
10.0.0.101 172.16.1.101
```



在**两个节点**上都进行操作

```
wget -O /etc/yum.repos.d/docker-ce.repo https://mirrors.ustc.edu.cn/docker-ce/linux/centos/docker-ce.repo
sed -i 's#download.docker.com#mirrors.ustc.edu.cn/docker-ce#g' /etc/yum.repos.d/docker-ce.repo
yum install docker-ce -y
```



修改在docker01配置：

```
# 修改启动文件，监听远程端口
vim /usr/lib/systemd/system/docker.service
ExecStart=/usr/bin/dockerd -H unix:///var/run/docker.sock -H tcp://10.0.0.100:2375
systemctl daemon-reload
systemctl enable docker.service 
systemctl restart docker.service
# ps -ef检查进行，是否启动
```



在docker02测试

```
[root@docker02 ~]# docker -H 10.0.0.100 info
Containers: 0
 Running: 0
 Paused: 0
 Stopped: 0
Images: 0
Server Version: 17.12.0-ce
Storage Driver: devicemapper
···
```



#### **Docker基础命令操作**

查看docker相关信息

```
[root@docker01 ~]#  docker version  
Client:
 Version:    17.12.0-ce
 API version:    1.35
 Go version:    go1.9.2
 Git commit:    c97c6d6
 Built:    Wed Dec 27 20:10:14 2017
 OS/Arch:    linux/amd64
Server:
 Engine:
  Version:    17.12.0-ce
  API version:    1.35 (minimum version 1.12)
  Go version:    go1.9.2
  Git commit:    c97c6d6
  Built:    Wed Dec 27 20:12:46 2017
  OS/Arch:    linux/amd64
  Experimental:    false
```



配置docker镜像加速

```
vi /etc/docker/daemon.json
{
  "registry-mirrors": ["https://registry.docker-cn.com"]
}   
```

#### **启动第一个容器**

```
[root@docker01 ~]# docker run -d -p 80:80 nginx
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
e7bb522d92ff: Pull complete 
6edc05228666: Pull complete 
cd866a17e81f: Pull complete 
Digest: sha256:285b49d42c703fdf257d1e2422765c4ba9d3e37768d6ea83d7fe2043dad6e63d
Status: Downloaded newer image for nginx:latest
8d8f81da12b5c10af6ba1a5d07f4abc041cb95b01f3d632c3d638922800b0b4d
# 容器启动后，在浏览器进行访问测试 
```



参数说明

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)



#### **Docker镜像生命周期**

![图片](https://mmbiz.qpic.cn/mmbiz_png/oTKHc6F8tsiaicIibGNyuxJNbNay2XqjcyNSxPFC21wFyyxKXFJRmXXwg45brbOIr6oI52Xo12opMk4YKmtLICv5Q/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

 

### **Docker镜像相关操作**

#### **搜索官方仓库镜像**

```
[root@docker01 ~]#  docker search centos
NAME                      DESCRIPTION                    STARS    OFFICIAL               AUTOMATED
centos                    The official build of CentOS.  3992     [OK]      
ansible/centos7-ansible   Ansible on Centos7             105                              [OK]
```



列表说明

![图片](https://mmbiz.qpic.cn/mmbiz_png/oTKHc6F8tsiaicIibGNyuxJNbNay2XqjcyNYehuNNwtQs3FPDfhGoocqoic7OuBpAicn1SOW3ANVkQDxb9LMsDGicUYg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



#### **获取镜像**

根据镜像名称拉取镜像

```
[root@docker01 ~]# docker pull centos
Using default tag: latest
latest: Pulling from library/centos
af4b0a2388c6: Downloading  34.65MB/73.67MB
```



查看当前主机镜像列表

```
[root@docker01 ~]# docker image list 
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
centos              latest              ff426288ea90        3 weeks ago         207MB
nginx               latest              3f8a4339aadd        5 weeks ago         108MB
```



拉第三方镜像方法

```
docker pull index.tenxcloud.com/tenxcloud/httpd
```

#### **导出镜像**

```
[root@docker01 ~]# docker image list 
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
centos              latest              ff426288ea90        3 weeks ago         207MB
nginx               latest              3f8a4339aadd        5 weeks ago         108MB
# 导出
[root@docker01 ~]# docker image save centos > docker-centos.tar.gz
```



#### **删除镜像**

```
[root@docker01 ~]# docker image rm centos:latest
[root@docker01 ~]# docker image list 
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
nginx               latest              3f8a4339aadd        5 weeks ago         108MB
```



#### **导入镜像**

```
[root@docker01 ~]# docker image load -i docker-centos.tar.gz  
e15afa4858b6: Loading layer  215.8MB/215.8MB
Loaded image: centos:latest
[root@docker01 ~]# docker image list 
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
centos              latest              ff426288ea90        3 weeks ago         207MB
nginx               latest              3f8a4339aadd        5 weeks ago         108MB
```



#### **查看镜像的详细信息**

```
[root@docker01 ~]# docker image inspect centos
```



### **容器的日常管理**

#### **容器的起/停**

最简单的运行一个容器

```
[root@docker01 ~]# docker run nginx
```



创建容器，两步走（不常用）

```
[root@docker01 ~]# docker create centos:latest  /bin/bash
bb7f32368ecf0492adb59e20032ab2e6cf6a563a0e6751e58930ee5f7aaef204
[root@docker01 ~]# docker start stupefied_nobel
stupefied_nobel
```



快速启动容器方法

```
[root@docker01 ~]# docker run  centos:latest  /usr/bin/sleep 20;
```



**容器内的第一个进程必须一直处于运行的状态，否则这个容器，就会处于退出状态！**



查看正在运行的容器

```
[root@docker01 ~]# docker container ls
    或
[root@docker01 ~]# docker ps 
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
8708e93fd767        nginx               "nginx -g 'daemon of…"   6 seconds ago       Up 4 seconds        80/tcp              keen_lewin
```





查看你容器详细信息/ip

```
[root@docker01 ~]# docker container  inspect  容器名称/id
```





查看你所有容器（包括未运行的）

```
[root@docker01 ~]# docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                      PORTS               NAMES
8708e93fd767        nginx               "nginx -g 'daemon of…"   4 minutes ago       Exited (0) 59 seconds ago                       keen_lewin
f9f3e6af7508        nginx               "nginx -g 'daemon of…"   5 minutes ago       Exited (0) 5 minutes ago                        optimistic_haibt
8d8f81da12b5        nginx               "nginx -g 'daemon of…"   3 hours ago         Exited (0) 3 hours ago                          lucid_bohr
```



停止容器

```
[root@docker01 ~]# docker stop 容器名称/id 
或
[root@docker01 ~]# docker container  kill  容器名称/id

```

#### **进入容器方法**

**启动时进去方法**

```
[root@docker01 ~]# docker run -it #参数：-it 可交互终端
[root@docker01 ~]# docker run -it nginx:latest  /bin/bash
root@79241093859e:/#
```



退出/离开容器

```
ctrl+p & ctrl+q
```



**启动后进入容器的方法**

启动一个docker

```
[root@docker01 ~]# docker run -it centos:latest 
[root@1bf0f43c4d2f /]# ps -ef 
UID         PID   PPID  C STIME TTY          TIME CMD
root          1      0  0 15:47 pts/0    00:00:00 /bin/bash
root         13      1  0 15:47 pts/0    00:00:00 ps -ef
```



attach进入容器，使用pts/0 ，会让所用通过此方法进如放入用户看到同样的操作。

```
[root@docker01 ~]# docker attach 1bf0f43c4d2f
[root@1bf0f43c4d2f /]# ps -ef 
UID         PID   PPID  C STIME TTY          TIME CMD
root          1      0  0 15:47 pts/0    00:00:00 /bin/bash
root         14      1  0 15:49 pts/0    00:00:00 ps -ef
```



自命名启动一个容器 --name

```
[root@docker01 ~]# docker attach 1bf0f43c4d2f
[root@1bf0f43c4d2f /]# ps -ef 
UID         PID   PPID  C STIME TTY          TIME CMD
root          1      0  0 15:47 pts/0    00:00:00 /bin/bash
root         14      1  0 15:49 pts/0    00:00:00 ps -ef
```



exec 进入容器方法（推荐使用）

```
[root@docker01 ~]# docker exec -it clsn1  /bin/bash 
[root@b20fa75b4b40 /]# 重新分配一个终端
[root@b20fa75b4b40 /]# ps -ef 
UID         PID   PPID  C STIME TTY          TIME CMD
root          1      0  0 16:11 pts/0    00:00:00 /bin/bash
root         13      0  0 16:14 pts/1    00:00:00 /bin/bash
root         26     13  0 16:14 pts/1    00:00:00 ps -ef
```

#### **删除所有容器**

```
[root@docker01 ~]# docker rm -f  `docker ps -a -q`
# -f 强制删除
```



#### **启动时进行端口映射**

-p参数端口映射

```
[root@docker01 ~]# docker run -d -p 8888:80  nginx:latest 
287bec5c60263166c03e1fc5b0b8262fe76507be3dfae4ce5cd2ee2d1e8a89a9
```



不同指定映射方法

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)



随机映射

```
docker run -P （大P）# 需要镜像支持
```

### **Docker 数据卷的管理**

#### **挂载时创建卷**

挂载卷

```
[root@docker01 ~]# docker run -d -p 80:80 -v /data:/usr/share/nginx/html nginx:latest
079786c1e297b5c5031e7a841160c74e91d4ad06516505043c60dbb78a259d09
```



容器内站点目录: /usr/share/nginx/html



在宿主机写入数据，查看

```
[root@docker01 ~]# echo "http://www.nmtui.com" >/data/index.html
[root@docker01 ~]# curl 10.0.0.100
http://www.nmtui.com
```



设置共享卷，使用同一个卷启动一个新的容器

```
[root@docker01 ~]# docker run -d -p 8080:80 -v /data:/usr/share/nginx/html nginx:latest 
351f0bd78d273604bd0971b186979aa0f3cbf45247274493d2490527babb4e42
[root@docker01 ~]# curl 10.0.0.100:8080
http://www.nmtui.com
```



查看卷列表

```
[root@docker01 ~]# docker volume ls
DRIVER              VOLUME NAME
```

#### **创建卷后挂载**

创建一个卷

```
[root@docker01 ~]# docker volume create 
f3b95f7bd17da220e63d4e70850b8d7fb3e20f8ad02043423a39fdd072b83521
[root@docker01 ~]# docker volume ls 
DRIVER              VOLUME NAME
local               f3b95f7bd17da220e63d4e70850b8d7fb3e20f8ad02043423a39fdd072b83521
```



指定卷名

```
[root@docker01 ~]# docker volume ls 
DRIVER              VOLUME NAME
local               clsn
local               f3b95f7bd17da220e63d4e70850b8d7fb3e20f8ad02043423a39fdd072b83521
```



查看卷路径

```
[root@docker01 ~]# docker volume inspect clsn 
[
    {
        "CreatedAt": "2018-02-01T00:39:25+08:00",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/clsn/_data",
        "Name": "clsn",
        "Options": {},
        "Scope": "local"
    }
]
```



使用卷创建

```
[root@docker01 ~]# docker run -d -p 9000:80 -v clsn:/usr/share/nginx/html nginx:latest 
1434559cff996162da7ce71820ed8f5937fb7c02113bbc84e965845c219d3503
# 宿主机测试
[root@docker01 ~]# echo 'blog.nmtui.com' >/var/lib/docker/volumes/clsn/_data/index.html 
[root@docker01 ~]# curl 10.0.0.100:9000
blog.nmtui.com
```



设置卷

```
[root@docker01 ~]# docker run  -d  -P  --volumes-from 079786c1e297 nginx:latest 
b54b9c9930b417ab3257c6e4a8280b54fae57043c0b76b9dc60b4788e92369fb
```



查看使用的端口

```
[root@docker01 ~]# netstat -lntup 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1400/sshd           
tcp        0      0 10.0.0.100:2375         0.0.0.0:*               LISTEN      26218/dockerd       
tcp6       0      0 :::9000                 :::*                    LISTEN      32015/docker-proxy  
tcp6       0      0 :::8080                 :::*                    LISTEN      31853/docker-proxy  
tcp6       0      0 :::80                   :::*                    LISTEN      31752/docker-proxy  
tcp6       0      0 :::22                   :::*                    LISTEN      1400/sshd           
tcp6       0      0 :::32769                :::*                    LISTEN      32300/docker-proxy  
[root@docker01 ~]# curl 10.0.0.100:32769
http://www.nmtui.com
```



#### **手动将容器保存为镜像**

本次是基于docker官方centos 6.8 镜像创建



官方镜像列表：

https://hub.docker.com/explore/



启动一个centos6.8的镜像

```
[root@docker01 ~]# docker pull  centos:6.8
[root@docker01 ~]# docker run -it -p 1022:22 centos:6.8  /bin/bash
# 在容器种安装sshd服务，并修改系统密码
[root@582051b2b92b ~]# yum install  openssh-server -y 
[root@582051b2b92b ~]# echo "root:123456" |chpasswd
[root@582051b2b92b ~]#  /etc/init.d/sshd start
```



启动完成后镜像ssh连接测试



将容器提交为镜像

```
[root@docker01 ~]# docker commit brave_mcclintock  centos6-ssh
```





使用新的镜像启动容器

```
[root@docker01 ~]# docker run -d  -p 1122:22  centos6-ssh:latest  /usr/sbin/sshd -D 
5b8161fda2a9f2c39c196c67e2eb9274977e7723fe51c4f08a0190217ae93094
```





在容器安装httpd服务

```
[root@5b8161fda2a9 /]#  yum install httpd -y
```



编写启动脚本脚本

```
[root@5b8161fda2a9 /]# cat  init.sh 
#!/bin/bash 
/etc/init.d/httpd start 
/usr/sbin/sshd -D
[root@5b8161fda2a9 /]# chmod +x init.sh 
# 注意执行权限
```





再次提交为新的镜像

```
[root@docker01 ~]# docker commit  5b8161fda2a9 centos6-httpd 
sha256:705d67a786cac040800b8485cf046fd57b1828b805c515377fc3e9cea3a481c1
```





启动镜像，做好端口映射。并在浏览器中测试访问

```
[root@docker01 ~]# docker run -d -p 1222:22 -p 80:80  centos6-httpd /init.sh 
46fa6a06644e31701dc019fb3a8c3b6ef008d4c2c10d46662a97664f838d8c2c
```



### **Dockerfile自动构建docker镜像**

官方构建dockerffile文件参考

https://github.com/CentOS/CentOS-Dockerfiles

#### **Dockerfile指令集**

dockerfile主要组成部分：

- 基础镜像信息 FROM centos:6.8
- 制作镜像操作指令RUN yum insatll openssh-server -y
- 容器启动时执行指令 CMD ["/bin/bash"]



dockerfile常用指令：

- FROM 这个镜像的妈妈是谁？（指定基础镜像）
- MAINTAINER 告诉别人，谁负责养它？（指定维护者信息，可以没有）
- RUN 你想让它干啥（在命令前面加上RUN即可）
- ADD 给它点创业资金（COPY文件，会自动解压）
- WORKDIR 我是cd,今天刚化了妆（设置当前工作目录）
- VOLUME 给它一个存放行李的地方（设置卷，挂载主机目录）
- EXPOSE 它要打开的门是啥（指定对外的端口）
- CMD 奔跑吧，兄弟！（指定容器启动后的要干的事情）



dockerfile其他指令： 

- COPY 复制文件
- ENV 环境变量
- ENTRYPOINT 容器启动后执行的命令

#### **创建一个Dockerfile**

创建第一个Dockerfile文件

```
# 创建目录
[root@docker01 base]# cd /opt/base
# 创建Dcokerfile文件，注意大小写
[root@docker01 base]# vim Dockerfile
FROM centos:6.8
RUN yum install openssh-server -y 
RUN echo "root:123456" |chpasswd
RUN /etc/init.d/sshd start 
CMD ["/usr/sbin/sshd","-D"]
```



构建docker镜像

```
[root@docker01 base]# docker image build  -t centos6.8-ssh . 
-t 为镜像标签打标签  . 表示当前路径
```



使用自构建的镜像启动

```
[root@docker01 base]# docker run  -d -p 2022:22 centos6.8-ssh-b 
dc3027d3c15dac881e8e2aeff80724216f3ac725f142daa66484f7cb5d074e7a
```



#### **使用Dcokerfile安装kodexplorer**

Dockerfile文件内容

```
FROM centos:6.8
RUN yum install wget unzip php php-gd php-mbstring -y && yum clean all
# 设置工作目录，之后的操作都在这个目录中
WORKDIR /var/www/html/
RUN wget -c http://static.kodcloud.com/update/download/kodexplorer4.25.zip
RUN unzip kodexplorer4.25.zip && rm -f kodexplorer4.25.zip
RUN chown -R apache.apache .
CMD ["/usr/sbin/apachectl","-D","FOREGROUND"]
```



更多的Dockerfile可以参考官方方法。

#### **Docker中的镜像分层**

参考文档：

http://www.maiziedu.com/wiki/cloud/dockerimage/



Docker 支持通过扩展现有镜像，创建新的镜像。实际上，Docker Hub 中 99% 的镜像都是通过在 base 镜像中安装和配置需要的软件构建出来的。



![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

 

从上图可以看到，新镜像是从 base 镜像一层一层叠加生成的。每安装一个软件，就在现有镜像的基础上增加一层。



#### **Docker 镜像为什么分层**

镜像分层最大的一个好处就是共享资源。



比如说有多个镜像都从相同的 base 镜像构建而来，那么 Docker Host 只需在磁盘上保存一份 base 镜像；同时内存中也只需加载一份 base 镜像，就可以为所有容器服务了。而且镜像的每一层都可以被共享。



如果多个容器共享一份基础镜像，当某个容器修改了基础镜像的内容，比如 /etc 下的文件，这时其他容器的 /etc 是不会被修改的，修改只会被限制在单个容器内。这就是容器 Copy-on-Write 特性。



#### **可写的容器层**

当容器启动时，一个新的可写层被加载到镜像的顶部。这一层通常被称作“容器层”，“容器层”之下的都叫“镜像层”。



![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)



 

所有对容器的改动 - 无论添加、删除、还是修改文件都只会发生在容器层中。只有**容器层是可写的，容器层下面的所有镜像层都是只读的。**



#### **容器层的细节说明**

镜像层数量可能会很多，所有镜像层会联合在一起组成一个统一的文件系统。如果不同层中有一个相同路径的文件，比如 /a，上层的 /a 会覆盖下层的 /a，也就是说用户只能访问到上层中的文件 /a。在容器层中，用户看到的是一个叠加之后的文件系统。



文件操作的

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)



只有当需要修改时才复制一份数据，这种特性被称作 Copy-on-Write。可见，容器层保存的是镜像变化的部分，不会对镜像本身进行任何修改。



这样就解释了我们前面提出的问题：容器层记录对镜像的修改，所有镜像层都是只读的，不会被容器修改，所以镜像可以被多个容器共享。



### **使用docker运行zabbix-server**

#### **容器间的互联**

在运行zabbix之前务必要了解容器间互联的方法

```
# 创建一个nginx容器
docker run -d -p 80:80 nginx
# 创建容器，做link，并进入容器中
docker run -it --link quirky_brown:web01 centos-ssh /bin/bash
# 在容器中访问nginx容器可以ping通
ping web01 
```



命令执行过程

```
# 启动apache容器
[root@docker01 ~]# docker run -d httpd:2.4  
3f1f7fc554720424327286bd2b04aeab1b084a3fb011a785b0deab6a34e56955
^[[A[root@docker01 docker ps -a
CONTAINER ID        IMAGE               COMMAND              CREATED             STATUS              PORTS               NAMES
3f1f7fc55472        httpd:2.4           "httpd-foreground"   6 seconds ago       Up 5 seconds        80/tcp              determined_clarke
# 拉取一个busybox 镜像
[root@docker01 ~]# docker pull busybox 
# 启动容器
[root@docker01 ~]# docker run -it  --link determined_clarke:web busybox:latest   /bin/sh 
/ # 
# 使用新的容器访问最初的web容器
/ # ping web 
PING web (172.17.0.2): 56 data bytes
64 bytes from 172.17.0.2: seq=0 ttl=64 time=0.058 ms
^C
--- web ping statistics ---
1 packets transmitted, 1 packets received, 0% packet loss
round-trip min/avg/max = 0.058/0.058/0.058 ms   
```



#### **启动zabbix容器**

1、启动一个mysql的容器

```
docker run --name mysql-server -t \
      -e MYSQL_DATABASE="zabbix" \
      -e MYSQL_USER="zabbix" \
      -e MYSQL_PASSWORD="zabbix_pwd" \
      -e MYSQL_ROOT_PASSWORD="root_pwd" \
      -d mysql:5.7 \
      --character-set-server=utf8 --collation-server=utf8_bin 
```



2、启动java-gateway容器监控java服务

```
docker run --name zabbix-java-gateway -t \
      -d zabbix/zabbix-java-gateway:latest
```



3、启动zabbix-mysql容器使用link连接mysql与java-gateway。

```
docker run --name zabbix-server-mysql -t \
      -e DB_SERVER_HOST="mysql-server" \
      -e MYSQL_DATABASE="zabbix" \
      -e MYSQL_USER="zabbix" \
      -e MYSQL_PASSWORD="zabbix_pwd" \
      -e MYSQL_ROOT_PASSWORD="root_pwd" \
      -e ZBX_JAVAGATEWAY="zabbix-java-gateway" \
      --link mysql-server:mysql \
      --link zabbix-java-gateway:zabbix-java-gateway \
      -p 10051:10051 \
      -d zabbix/zabbix-server-mysql:latest
```



4、启动zabbix web显示，使用link连接zabbix-mysql与mysql。

```
docker run --name zabbix-web-nginx-mysql -t \
      -e DB_SERVER_HOST="mysql-server" \
      -e MYSQL_DATABASE="zabbix" \
      -e MYSQL_USER="zabbix" \
      -e MYSQL_PASSWORD="zabbix_pwd" \
      -e MYSQL_ROOT_PASSWORD="root_pwd" \
      --link mysql-server:mysql \
      --link zabbix-server-mysql:zabbix-server \
      -p 80:80 \
      -d zabbix/zabbix-web-nginx-mysql:latest
```



#### **关于zabbix API**

关于zabbix API可以参考官方文档：

https://www.zabbix.com/documentation/3.4/zh/manual/api



1、获取token方法

```
# 获取token
[root@docker02 ~]# curl -s -X POST -H 'Content-Type:application/json' -d '
{
"jsonrpc": "2.0",
"method": "user.login",
"params": {
"user": "Admin",
"password": "zabbix"
},
"id": 1
}' http://10.0.0.100/api_jsonrpc.php
{"jsonrpc":"2.0","result":"d3be707f9e866ec5d0d1c242292cbebd","id":1}
```



### **docker 仓库（registry）**

#### **创建一个普通仓库**

1、创建仓库

```
docker run -d -p 5000:5000 --restart=always --name registry -v /opt/myregistry:/var/lib/registry  registry 
```





2、修改配置文件，使之支持http

```
[root@docker01 ~]# cat  /etc/docker/daemon.json 
{
  "registry-mirrors": ["https://registry.docker-cn.com"],
  "insecure-registries": ["10.0.0.100:5000"]
}
```



重启docker让修改生效

```
[root@docker01 ~]# systemctl restart  docker.service
```



```

```

3、修改镜像标签

```
[root@docker01 ~]# docker tag  busybox:latest  10.0.0.100:5000/clsn/busybox:1.0
[root@docker01 ~]# docker images
REPOSITORY                      TAG                 IMAGE ID            CREATED             SIZE
centos6-ssh                     latest              3c2b1e57a0f5        18 hours ago        393MB
httpd                           2.4                 2e202f453940        6 days ago          179MB
10.0.0.100:5000/clsn/busybox    1.0                 5b0d59026729        8 days ago          1.15MB
```



4、将新打标签的镜像上传镜像到仓库

```
[root@docker01 ~]# docker push   10.0.0.100:5000/clsn/busybox
```



#### **带basic认证的仓库**

1、安装加密工具

```
[root@docker01 clsn]# yum install httpd-tools  -y
```



2、设置认证密码

```
mkdir /opt/registry-var/auth/ -p
htpasswd  -Bbn clsn 123456  > /opt/registry-var/auth/htpasswd
```



3、启动容器，在启动时传入认证参数

```
docker run -d -p 5000:5000 -v /opt/registry-var/auth/:/auth/ -e "REGISTRY_AUTH=htpasswd" -e "REGISTRY_AUTH_HTPASSWD_REALM=Registry Realm" -e REGISTRY_AUTH_HTPASSWD_PATH=/auth/htpasswd registry
```



4、使用验证用户测试

```
# 登陆用户
[root@docker01 ~]# docker login 10.0.0.100:5000 
Username: clsn  
Password: 123456
Login Succeeded
# 推送镜像到仓库
[root@docker01 ~]# docker push 10.0.0.100:5000/clsn/busybox 
The push refers to repository [10.0.0.100:5000/clsn/busybox]
4febd3792a1f: Pushed 
1.0: digest: sha256:4cee1979ba0bf7db9fc5d28fb7b798ca69ae95a47c5fecf46327720df4ff352d size: 527
#认证文件的保存位置
[root@docker01 ~]# cat .docker/config.json 
{
    "auths": {
        "10.0.0.100:5000": {
            "auth": "Y2xzbjoxMjM0NTY="
        },
        "https://index.docker.io/v1/": {
            "auth": "Y2xzbjpIenNAMTk5Ng=="
        }
    },
    "HttpHeaders": {
        "User-Agent": "Docker-Client/17.12.0-ce (linux)"
    }
}
```



至此，一个简单的docker镜像仓库搭建完成

### **docker-compose编排工具**

#### **安装docker-compose**

安装docker-compose

```
# 下载pip软件
yum install -y python2-pip
# 下载 docker-compose
pip install docker-compose
```



国内开启pip 下载加速：

http://mirrors.aliyun.com/help/pypi

```
mkdir ~/.pip/
cat > ~/.pip/pip.conf <<'EOF'
[global]
index-url = https://mirrors.aliyun.com/pypi/simple/
[install]
trusted-host=mirrors.aliyun.com
EOF
```



#### **编排启动镜像**

1、创建文件目录

```
[root@docker01 ~]# mkdir /opt/my_wordpress/
[root@docker01 ~]# cd /opt/my_wordpress/
```



2、编写编排文件

```
[root@docker01 my_wordpress]# vim docker-compose.yml
version: '3'
services:
   db:
     image: mysql:5.7
     volumes:
       - /data/db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress
   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     volumes:
       - /data/web_data:/var/www/html
     ports: 
       - "8000:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
```



3、启动

```
[root@docker01 my_wordpress]# docker-compose up
　　#启动方法：docker-compose up
　　#后台启动方法：docker-compose up -d
```



4、浏览器上访问http://10.0.0.100:8000



进行wordpress的安装即可

#### **haproxy代理后端docker容器**

1、修改编排脚本

```
[root@docker01 my_wordpress]# cat docker-compose.yml 
version: '3'
services:
   db:
     image: mysql:5.7
     volumes:
       - /data/db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress
   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     volumes:
       - /data/web_data:/var/www/html
     ports: 
       - "80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
```



2、同时启动两台wordpress

```
[root@docker01 my_wordpress]# docker-compose scale wordpress=2 
WARNING: The scale command is deprecated. Use the up command with the --scale flag instead.
Starting mywordpress_wordpress_1 ... done
Creating mywordpress_wordpress_2 ... done
```



3、安装haproxy

```
[root@docker01 ~]# yum install haproxy -y
```



4、修改haproxy配置文件

关于配置文件的详细说明，参考：

https://www.cnblogs.com/MacoLee/p/5853413.html

```
[root@docker01 ~]#cp /etc/haproxy/haproxy.cfg{,.bak}
[root@docker01 ~]# vim /etc/haproxy/haproxy.cfg
global
    log         127.0.0.1 local2
    chroot      /var/lib/haproxy
    pidfile     /var/run/haproxy.pid
    maxconn     4000
    user        haproxy
    group       haproxy
    daemon
    stats socket /var/lib/haproxy/stats level admin  #支持命令行控制
defaults
    mode                    http
    log                     global
    option                  httplog
    option                  dontlognull
    option http-server-close
    option forwardfor       except 127.0.0.0/8
    option                  redispatch
    retries                 3
    timeout http-request    10s
    timeout queue           1m
    timeout connect         10s
    timeout client          1m
    timeout server          1m
    timeout http-keep-alive 10s
    timeout check           10s
    maxconn                 3000
listen stats
    mode http
    bind 0.0.0.0:8888
    stats enable
    stats uri     /haproxy-status 
    stats auth    admin:123456
frontend frontend_www_example_com
    bind 10.0.0.100:8000
    mode http
    option httplog
    log global
    default_backend backend_www_example_com
backend backend_www_example_com
    option forwardfor header X-REAL-IP
    option httpchk HEAD / HTTP/1.0
    balance roundrobin
    server web-node1  10.0.0.100:32768 check inter 2000 rise 30 fall 15
    server web-node2  10.0.0.100:32769 check inter 2000 rise 30 fall 15
```



5、启动haproxy

```
systemctl start haproxy
systemctl enable haproxy
```



6、使用浏览器访问hapeoxy监听的8000端口可以看到负载的情况

![图片](https://mmbiz.qpic.cn/mmbiz_png/oTKHc6F8tsiaicIibGNyuxJNbNay2XqjcyNic9DpCJXcR95mfbGbd9FGYfuIDH4vibYWmBCqTCVdDmlyiaP8j7PBkw3w/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



7、使用浏览器访问 

http://10.0.0.100:8888/haproxy-status



可以看到后端节点的监控状况，

![图片](https://mmbiz.qpic.cn/mmbiz_png/oTKHc6F8tsiaicIibGNyuxJNbNay2XqjcyNEnaATu6gVIjdjfqpZlrk5uhiaKM9yTYic80Q3Pq4qibnrWBibeiauLGDuwQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

 

#### **安装socat 直接操作socket控制haproxy**

1、安装软件

```
yum install socat.x86_64 -y
```



2、查看帮助

```
[root@docker01 web_data]# echo "help"|socat stdio /var/lib/haproxy/stats
```



3、下线后端节点

```
echo "disable server backend_www_example_com/web-node2"|socat stdio /var/lib/haproxy/stats
```



4、上线后端节点

```
echo "enable server backend_www_example_com/web-node3"|socat stdio /var/lib/haproxy/stats
```



5、编写php测试页，放到/data/web_data下，在浏览器中访问可以查看当前的节点

```
[root@docker01 web_data]# vim check.php
<html>
    <head>
        <title>PHP测试</title>
    </head>
    <body>
        <?php  echo '<p>Hello World </p>'; ?>
        <?php  echo "访问的服务器地址是:"."<fontcolor=red>".$_SERVER['SERVER_ADDR']."</font>"."<br>";
        echo"访问的服务器域名是:"."<fontcolor=red>".$_SERVER['SERVER_NAME']."</font>"."<br>";
        ?>
    </body>
</html>
```



### 重启docker服务，容器全部退出的解决办法

#### **在启动是指定自动重启**

```
docker run  --restart=always
```



#### **修改docker默认配置文件**

```
# 添加上下面这行
"live-restore": true
```





docker server配置文件 /etc/docker/daemon.json 参考

```
[root@docker02 ~]# cat  /etc/docker/daemon.json 
{
  "registry-mirrors": ["https://registry.docker-cn.com"],
  "graph": "/opt/mydocker", # 修改数据的存放目录到/opt/mydocker/，原/var/lib/docker/
  "insecure-registries": ["10.0.0.100:5000"],
  "live-restore": true
}
```



重启生效，只对在此之后启动的容器生效

```
[root@docker01 ~]# systemctl restart  docker.service
```



### **Docker网络类型**

![图片](https://mmbiz.qpic.cn/mmbiz_png/oTKHc6F8tsiaicIibGNyuxJNbNay2XqjcyN3O8G4N3W0f7o9MMbdtXhrkok419zbBSNicK98KFOeuibry2onlibKMxAw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



#### **docker的网络类型**

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)





Bridge默认docker网络隔离基于网络命名空间，在物理机上创建docker容器时会为每一个docker容器分配网络命名空间，并且把容器IP桥接到物理机的虚拟网桥上。



#### **不为容器配置网络功能**

此模式下创建容器是不会为容器配置任何网络参数的，如：容器网卡、IP、通信路由等，全部需要自己去配置。

```
[root@docker01 ~]# docker run  -it --network none busybox:latest  /bin/sh 
/ # ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
```





#### **与其他容器共享网络配置(Container）**

此模式和host模式很类似，只是此模式创建容器共享的是其他容器的IP和端口而不是物理机，此模式容器自身是不会配置网络和端口，创建此模式容器进去后，你会发现里边的IP是你所指定的那个容器IP并且端口也是共享的，而且其它还是互相隔离的，如进程等。



```
[root@docker01 ~]# docker run  -it --network container:mywordpress_db_1  busybox:latest  /bin/sh 
/ # ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
105: eth0@if106: <BROADCAST,MULTICAST,UP,LOWER_UP,M-DOWN> mtu 1500 qdisc noqueue 
    link/ether 02:42:ac:12:00:03 brd ff:ff:ff:ff:ff:ff
    inet 172.18.0.3/16 brd 172.18.255.255 scope global eth0
       valid_lft forever preferred_lft forever
```





#### **使用宿主机网络**

此模式创建的容器没有自己独立的网络命名空间，是和物理机共享一个Network Namespace，并且共享物理机的所有端口与IP，并且这个模式认为是不安全的。

```
[root@docker01 ~]# docker run  -it --network host  busybox:latest  /bin/sh
```



#### **查看网络列表**

```
[root@docker01 ~]# docker network list 
NETWORK ID          NAME                  DRIVER              SCOPE
b15e8a720d3b        bridge                bridge              local
345d65b4c2a0        host                  host                local
bc5e2a32bb55        mywordpress_default   bridge              local
ebf76eea91bb        none                  null                local
```





#### **用PIPEWORK为docker容器配置独立IP**

- 参考文档：

  blog.csdn.net/design321/article/details/48264825



- 官方网站：

  github.com/jpetazzo/pipework



- 宿主环境：centos7.2



1、安装pipework

```
wget https://github.com/jpetazzo/pipework/archive/master.zip
unzip master.zip 
cp pipework-master/pipework  /usr/local/bin/
chmod +x /usr/local/bin/pipework
```



2、配置桥接网卡

安装桥接工具

```
yum install bridge-utils.x86_64 -y
```



修改网卡配置，实现桥接

```
# 修改eth0配置，让br0实现桥接
[root@docker01 ~]# cat /etc/sysconfig/network-scripts/ifcfg-eth0 
TYPE=Ethernet
BOOTPROTO=static
NAME=eth0
DEVICE=eth0
ONBOOT=yes
BRIDGE=br0
[root@docker01 ~]# cat /etc/sysconfig/network-scripts/ifcfg-br0 
TYPE=Bridge
BOOTPROTO=static
NAME=br0
DEVICE=br0
ONBOOT=yes
IPADDR=10.0.0.100
NETMASK=255.255.255.0
GATEWAY=10.0.0.254
DNS1=223.5.5.5
# 重启网络
[root@docker01 ~]# /etc/init.d/network restart
```



3、运行一个容器镜像测试：

```
pipework br0 $(docker run -d -it -p 6880:80 --name  httpd_pw httpd) 10.0.0.220/24@10.0.0.254
```



在其他主机上测试端口及连通性

```
[root@docker01 ~]# curl 10.0.0.220
<html><body><h1>It works!</h1></body></html>
[root@docker01 ~]# ping 10.0.0.220 -c 1
PING 10.0.0.220 (10.0.0.220) 56(84) bytes of data.
64 bytes from 10.0.0.220: icmp_seq=1 ttl=64 time=0.043 ms
```



```
4、再运行一个容器，设置网路类型为none：
pipework br0 $(docker run -d -it --net=none --name test httpd:2.4) 10.0.0.221/24@10.0.0.254
```





进行访问测试

```
[root@docker01 ~]# curl 10.0.0.221
<html><body><h1>It works!</h1></body></html>
```



5、重启容器后需要再次指定：

```
pipework br0 testduliip  172.16.146.113/24@172.16.146.1
pipework br0 testduliip01  172.16.146.112/24@172.16.146.1
```



Dcoker跨主机通信之overlay可以参考：

cnblogs.com/CloudMan6/p/7270551.html

#### **Docker跨主机通信之macvlan**

创建网络

```
[root@docker01 ~]# docker network  create --driver macvlan  --subnet 10.1.0.0/24 --gateway 10.1.0.254 -o parent=eth0  macvlan_1
33a1f41dcc074f91b5bd45e7dfedabfb2b8ec82db16542f05213839a119b62ca
```



设置网卡为混杂模式

```
ip link set eth0 promisc on
```



创建使用macvlan网络容器

```
[root@docker02 ~]# docker run  -it --network macvlan_1  --ip=10.1.0.222 busybox /b
```



### **docker企业级镜像仓库harbor**

容器管理

```
[root@docker01 harbor]# pwd
/opt/harbor
[root@docker01 harbor]# docker-compose stop
```



1、安装docker、docker-compose

下载 harbor

```
cd /opt && https://storage.googleapis.com/harbor-releases/harbor-offline-installer-v1.3.0.tgz
tar xf harbor-offline-installer-v1.3.0.tgz
```



2、修改主机及web界面密码

```
[root@docker01 harbor]# vim harbor.cfg 
    ···
    hostname = 10.0.0.100
    harbor_admin_password = Harbor12345
    ···
```



3、执行安装脚本

```
[root@docker01 harbor]# ./install.sh
```



浏览器访问 http://10.0.0.11

![图片](https://mmbiz.qpic.cn/mmbiz_png/oTKHc6F8tsiaicIibGNyuxJNbNay2XqjcyNdibRRbq9WzbzMkicCf1xrbuZgmXVIQFxrvsalTniaFibq0XVnuxezP4JRA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1) 

添加一个项目

![图片](https://mmbiz.qpic.cn/mmbiz_png/oTKHc6F8tsiaicIibGNyuxJNbNay2XqjcyND9aeaeciacdebb7mWbrm4lGHHju8zVianusKOBbbJic3vcY3o7nLbV8tQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

4、镜像推送到仓库的指定项目

```
[root@docker02 ~]# docker  tag centos:6.8  10.0.0.100/clsn/centos6.8:1.0
[root@docker02 ~]#  
[root@docker02 ~]# docker images 
REPOSITORY                  TAG                 IMAGE ID            CREATED             SIZE
busybox                     latest              5b0d59026729        8 days ago          1.15MB
10.0.0.100/clsn/centos6.8   1.0                 6704d778b3ba        2 months ago        195MB
centos                      6.8                 6704d778b3ba        2 months ago        195MB
[root@docker02 ~]# docker login 10.0.0.100
Username: admin
Password: 
Login Succeeded
```



5、推送镜像

```
[root@docker02 ~]# docker push 10.0.0.100/clsn/centos6.8 
The push refers to repository [10.0.0.100/clsn/centos6.8]
e00c9229b481: Pushing  13.53MB/194.5MB
```



6、在web界面里查看

![图片](https://mmbiz.qpic.cn/mmbiz_png/oTKHc6F8tsiaicIibGNyuxJNbNay2XqjcyNQAAEboIdByNZWVv08D9ibvalrm9vefENnpY5lCWhEYQWS7oMK7cJx4A/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1) 

#### **使用容器的建议**

\1. 不要以拆分方式进行应用程序发布

\2. 不要创建大型镜像

\3. 不要在单个容器中运行多个进程

\4. 不要再镜像内保存凭证，不要依赖IP地址

\5. 以非root用户运行进程

\6. 不要使用“最新”标签

\7. 不要利用运行中的容器创建镜像

\8. 不要使用单层镜像

\9. 不要将数据存放在容器内

#### **关于Docker容器的监控**

**容器的基本信息**

- 包括容器的数量、ID、名称、镜像、启动命令、端口等信息



**容器的运行状态**

- 统计各状态的容器的数量，包括运行中、暂停、停止及异常退出



**容器的用量信息**

- 统计容器的CPU使用率、内存使用量、块设备I/O使用量、网络使用情况等资源的使用情况



### 参考文献

- redhat.com/zh/topics/containers/whats-a-linux-container
- redhat.com/zh/topics/containers/what-is-docker
- blog.51cto.com/dihaifeng/1713512
- cnblogs.com/Bourbon-tian/p/6867796.html
- cnblogs.com/CloudMan6/p/6806193.html

*作者：惨绿少年；**cnblogs.com/clsn/p/8410309.html*







# Mybatis-plus

## Mybatis-plus常用API全套教程，看完没有不懂的

作者：java架构师阿松

www.toutiao.com/i6869621037831717387

### 前言

官网：

> https://baomidou.com/

### 创建数据库

数据库名为mybatis_plus

### 创建表

创建user表

```sql
DROP TABLE IF EXISTS user;
CREATE TABLE user
(
id BIGINT(20) NOT NULL COMMENT '主键ID',
name VARCHAR(30) NULL DEFAULT NULL COMMENT '姓名',
age INT(11) NULL DEFAULT NULL COMMENT '年龄',
email VARCHAR(50) NULL DEFAULT NULL COMMENT '邮箱',
PRIMARY KEY (id)
);
INSERT INTO user (id, name, age, email) VALUES
(1, 'Jone', 18, 'test1@baomidou.com'),
(2, 'Jack', 20, 'test2@baomidou.com'),
(3, 'Tom', 28, 'test3@baomidou.com'),
(4, 'Sandy', 21, 'test4@baomidou.com'),
(5, 'Billie', 24, 'test5@baomidou.com');
```

注意：-- 真实开发中往往都会有这四个字段，version（乐观锁）、deleted（逻辑删除）、gmt_create（创建时间）、gmt_modified（修改时间）

### 初始化项目

使用SpringBoot器 初始化！

### 导入依赖

```xml
<!-- 数据库驱动 -->
<dependency>
  <groupId>mysql</groupId>
  <artifactId>mysql-connector-java</artifactId>
</dependency>
<!-- lombok -->
<dependency>
  <groupId>org.projectlombok</groupId>
  <artifactId>lombok</artifactId>
</dependency>
<!-- mybatis-plus -->
<!-- mybatis-plus 是自己开发，并非官方的！ -->
<dependency>
  <groupId>com.baomidou</groupId>
  <artifactId>mybatis-plus-boot-starter</artifactId>
  <version>3.0.5</version>
</dependency>
```

注意：尽量不要同时导入 mybatis 和 mybatis-plus！避免版本的差异造成无法预知的问题。

### 连接数据库

创建application.yml

```yaml
spring:
  profiles:
    active: dev
  datasource:
# 驱动不同 mysql 5  com.mysql.jdbc.Driver
#         mysql 8  com.mysql.cj.jdbc.Driver、需要增加时区的配置serverTimezone=GMT%2B8
    url: jdbc:mysql://localhost:3306/mybatis_plus?useSSL=false&useUnicode=true&characterEncoding=utf-8&serverTimezone=GMT%2B8
    driver-class-name: com.mysql.cj.jdbc.Driver
    username: root
    password: root
```

### 业务代码

实体类

```java
@Data
@AllArgsConstructor
@NoArgsConstructor
public class User {
  private Long id;
  private String name;
  private Integer age;
  private String email;
} 
```

mapper接口

```
import com.baomidou.mybatisplus.core.mapper.BaseMapper;
import com.kuang.pojo.User;
import org.springframework.stereotype.Repository;
// 在对应的Mapper上面继承基本的类 BaseMapper
@Repository // 代表持久层
public interface UserMapper extends BaseMapper<User> {
  // 所有的CRUD操作都已经编写完成了
}
```

注意点，我们需要在主启动类上去扫描我们的mapper包下的所有接口 @MapperScan(“com.kwhua.mapper”)

### 测试

```java
@SpringBootTest
class MybatisPlusApplicationTests {
  // 继承了BaseMapper，所有的方法都来自己父类
  // 我们也可以编写自己的扩展方法！
  @Autowired
  private UserMapper userMapper;
  @Test
  void contextLoads() {
    // 参数是一个 Wrapper ，条件构造器，这里我们先设置条件为空，查询所有。
    List<User> users = userMapper.selectList(null);
    users.forEach(System.out::println);
 }
} 
```

所有数据输出![图片](https://mmbiz.qpic.cn/mmbiz_png/Z2CXAHBzdZGCiaNL1XOGuKZRaibIdfuUltHsDqXkRd7mhmomHnicicMh5lVJB32RDWI1IYmVIYibNofIed2k0S8Gg6A/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### 配置日志

我们所有的sql现在是不可见的，我们希望知道它是怎么执行的，所有我们要配置日志的输出 application.yml文件添加日志配置

```yaml
#配置日志
mybatis-plus:
  configuration:
    log-impl: org.apache.ibatis.logging.stdout.StdOutImpl
```

查看执行sql的日志信息![图片](https://mmbiz.qpic.cn/mmbiz_png/Z2CXAHBzdZGCiaNL1XOGuKZRaibIdfuUlt2OCGaxaJC7zx8WF1l2lricRozhYBUWaqeiaoFDhah9YWXibVyicGyyX4Eg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

## 三.Mybatis-plus的CRUD

### 插入操作

```java
// 测试插入
    @Test
    public void testInsert(){
        User user = new User();
        user.setName("kwhua_mybatis-plus_insertTest");
        user.setAge(15);
        user.setEmail("310697723@qq.com");

        int result = userMapper.insert(user); // 帮我们自动生成id
        System.out.println(result); // 受影响的行数
        System.out.println(user); // 看到id会自动填充。    }  
```

![图片](https://mmbiz.qpic.cn/mmbiz_png/Z2CXAHBzdZGCiaNL1XOGuKZRaibIdfuUlt400vEbE48ETaEss8ibh5DQPjeKS54qfaQKpIlAzc7RXDt4CQ1fmTQPQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)看到id会自动填充。数据库插入的id的默认值为：全局的唯一id

### 主键生成策略

1）主键自增 1、实体类字段上 @TableId(type = IdType.AUTO)

2、数据库id字段设置为自增！![图片](https://mmbiz.qpic.cn/mmbiz_png/Z2CXAHBzdZGCiaNL1XOGuKZRaibIdfuUltqPFUaNedib6SIQzVGYwnTIuSpUlXHCekfUiczia8tskM2zEmFWmOz9zcw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)3、再次测试（可以看到id值比上次插入的大1）id的生成策略源码解释

![图片](https://mmbiz.qpic.cn/mmbiz_png/Z2CXAHBzdZGCiaNL1XOGuKZRaibIdfuUltbaibV03P7yY8gqWltAHicvVRt5icLjOhX9QlytnibkZB7PRicv7ELe8FyjA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)图片

```java
public enum IdType {
  AUTO(0), // 数据库id自增
  NONE(1), // 未设置主键
  INPUT(2), // 手动输入
  ID_WORKER(3), // 默认的方式,全局唯一id
  UUID(4), // 全局唯一id uuid
  ID_WORKER_STR(5); //ID_WORKER 字符串表示法
}
```

以上不再逐一测试。

### 更新操作

```java
 @Test
    public void testUpdate(){
        User user = new User();
        // 通过条件自动拼接动态sql
        user.setId(1302223874217295874L);
        user.setName("kwhua_mybatis-plus_updateTest");
        user.setAge(20);
        // 注意：updateById 但是参数是一个对象！
        int i = userMapper.updateById(user);
        System.out.println(i);
    }
```

![图片](https://mmbiz.qpic.cn/mmbiz_png/Z2CXAHBzdZGCiaNL1XOGuKZRaibIdfuUltmmDicf3Pqv8icPSKt6J2GffZQgkvUCrGQhvQG6dNytY4P0kIWvtHpHnQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)图片

### 自动填充

创建时间、修改时间！这两个字段操作都是自动化完成的，我们不希望手动更新！阿里巴巴开发手册：所有的数据库表都要配置上gmt_create、gmt_modified！而且需要自动化！

方式一：数据库级别（工作中一般不用）

1、在表中新增字段 gmt_create, gmt_modified

2、把实体类同步

```java
private Date gmtCreate;
private Date gmtModified;
```

3、再次查看![图片](https://mmbiz.qpic.cn/mmbiz_png/Z2CXAHBzdZGCiaNL1XOGuKZRaibIdfuUltk2iagNpPl0pgrweoMxOAaj8rfhicdCXcvvSb83RwvFHpJVzu287LM6vQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

方式二：代码级别 1、删除数据库的默认值、更新操作！

2、实体类字段属性上需要增加注解

```java
    // 字段添加填充内容
    @TableField(fill = FieldFill.INSERT)
    private Date gmt_create;

    @TableField(fill = FieldFill.INSERT_UPDATE)
    private Date gmt_modified;
```

3、编写处理器来处理这个注解即可！

```java
@Slf4j
@Component // 一定不要忘记把处理器加到IOC容器中！
public class MyMetaObjectHandler implements MetaObjectHandler {
    // 插入时的填充策略
    @Override
    public void insertFill(MetaObject metaObject) {
        log.info("start insert fill.....");
        // setFieldValByName(String fieldName, Object fieldVal, MetaObject metaObject
        this.setFieldValByName("gmt_create",new Date(),metaObject);
        this.setFieldValByName("gmt_modified",new Date(),metaObject);
    }

    // 更新时的填充策略
    @Override
    public void updateFill(MetaObject metaObject) {
        log.info("start update fill.....");
        this.setFieldValByName("gmt_modified",new Date(),metaObject);
    }
}
```

4、测试插入和更新，检查时间变化。

### 乐观锁

乐观锁 : 顾名思义，十分乐观，它总是认为不会出现问题，无论干什么不去上锁！如果出现了问题， 再次更新值测试 悲观锁：顾名思义，十分悲观，它总是认为总是出现问题，无论干什么都会上锁！再去操作！

乐观锁实现方式：

取出记录时，获取当前version 更新时，带上这个version 执行更新时， set version = newVersion where version = oldVersion 如果version不对，就更新失败

乐观锁：1、先查询，获得版本号 version = 1

```sql
-- A
update user set name = "kwhua", version = version + 1
where id = 2 and version = 1
-- B 线程抢先完成，这个时候 version = 2，会导致 A 修改失败！
update user set name = "kwhua", version = version + 1
where id = 2 and version = 1
```

乐观锁测试

1、给数据库中增加version字段！

![图片](https://mmbiz.qpic.cn/mmbiz_png/Z2CXAHBzdZGCiaNL1XOGuKZRaibIdfuUltJ06kHNnAjlUmbjTm0n9eYb20gRnwZE7SSoHkiboVybNZRpXz7YiaFy5g/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)图片

2、实体类加对应的字段

```java
    @Version //乐观锁Version注解
    private Integer version;
```

3、注册组件

```java
// 扫描我们的 mapper 文件夹
@MapperScan("com.kwhua.mapper")
@EnableTransactionManagement
@Configuration // 配置类
public class MyBatisPlusConfig {
    // 注册乐观锁插件
    @Bean
    public OptimisticLockerInterceptor optimisticLockerInterceptor() {
        return new OptimisticLockerInterceptor();
    }
   }
```

4、测试

```java
// 测试乐观锁成功！
    @Test
    public void testOptimisticLocker(){
        // 1、查询用户信息
        User user = userMapper.selectById(1L);
        // 2、修改用户信息
        user.setName("kwhua");
        user.setEmail("123456@qq.com");
        // 3、执行更新操作
        userMapper.updateById(user);
    }
```

version字段已经由1变成了2

```java
// 测试乐观锁失败！多线程下
    @Test
    public void testOptimisticLocker2(){

        // 线程 1
        User user = userMapper.selectById(1L);
        user.setName("kwhua111");
        user.setEmail("123456@qq.com");

        // 模拟另外一个线程执行了插队操作
        User user2 = userMapper.selectById(1L);
        user2.setName("kwhua222");
        user2.setEmail("123456@qq.com");
        userMapper.updateById(user2);

        // 自旋锁来多次尝试提交！
        userMapper.updateById(user); // 如果没有乐观锁就会覆盖插队线程的值！
    }
```

![图片](https://mmbiz.qpic.cn/mmbiz_png/Z2CXAHBzdZGCiaNL1XOGuKZRaibIdfuUltms3VarKOT1qaovHgibCCAA9AvPpxAeWajDrxcLTAjLibbVqCUJr2rDeg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)图片

可以看到线程1执行更新失败

### 查询操作

```java
// 测试查询
    @Test
    public void testSelectById(){
        User user = userMapper.selectById(1L);
        System.out.println(user);
    }

    // 测试批量查询！
    @Test
    public void testSelectByBatchId(){
        List<User> users = userMapper.selectBatchIds(Arrays.asList(1, 2, 3));
        users.forEach(System.out::println);
    }

    // 按条件查询之一使用map操作
    @Test
    public void testSelectByBatchIds(){
        HashMap<String, Object> map = new HashMap<>();
        // 自定义要查询
        map.put("name","kwhua");
        map.put("age",15);

        List<User> users = userMapper.selectByMap(map);
        users.forEach(System.out::println);
    }
```

1、配置拦截器组件

```java
// 分页插件
@Bean
public PaginationInterceptor paginationInterceptor() {
  return  new PaginationInterceptor();
}
```

2、直接使用Page对象即可！

```java
// 测试分页查询
@Test
public void testPage(){
  // 参数一：当前页
  // 参数二：页面大小
  Page<User> page = new Page<>(2,5);
  userMapper.selectPage(page,null);
  page.getRecords().forEach(System.out::println);
  System.out.println(page.getTotal());
}
```

### 物理删除

```java
// 测试删除
    @Test
    public void testDeleteById(){
        userMapper.deleteById(1L);
    }

    // 通过id批量删除
    @Test
    public void testDeleteBatchId(){
        userMapper.deleteBatchIds(Arrays.asList(2L,3L));
    }

    // 通过map删除
    @Test
    public void testDeleteMap(){
        HashMap<String, Object> map = new HashMap<>();
        map.put("name","kwhua");
        userMapper.deleteByMap(map);
    }
```

### 逻辑删除

物理删除 ：从数据库中直接移除 逻辑删除 ：在数据库中没有被移除，而是通过一个变量来让它失效！deleted = 0 => deleted = 1 管理员可以查看被删除的记录！防止数据的丢失，类似于回收站！

1、在数据表中增加一个 deleted 字段2、实体类中增加属性

```
 @TableLogic //逻辑删除
 private Integer deleted;
```

3、配置

```java
// 逻辑删除组件！
    @Bean
    public ISqlInjector sqlInjector() {
        return new LogicSqlInjector();
    }
```

配置文件配置

```yaml
 global-config:
    db-config:
      logic-delete-value: 1
      logic-not-delete-value: 0
```

4、测试 测试删除

![图片](https://mmbiz.qpic.cn/mmbiz_png/Z2CXAHBzdZGCiaNL1XOGuKZRaibIdfuUltSaUDp4ibbGWqahf61DVWNT0QojTEEpfvHfRqa8ANw949icrLiasHdXDpw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)图片

字段值也从0修改成了1测试查询

![图片](https://mmbiz.qpic.cn/mmbiz_png/Z2CXAHBzdZGCiaNL1XOGuKZRaibIdfuUltnrCbhicvlqjsiaibKXdaSue0wxibuuIo9slaoXsOpRSoSgED3RiaF5bCR2g/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)图片

### 性能分析插件

作用：性能分析拦截器，用于输出每条 SQL 语句及其执行时间 MP也提供性能分析插件，如果超过这个时间就停止运行！1、导入插件

```java
   /**
     * SQL执行效率插件
     */
    @Bean
    @Profile({"dev","test"})// 设置 dev test 环境开启，保证我们的效率
    public PerformanceInterceptor performanceInterceptor() {
        PerformanceInterceptor performanceInterceptor = new PerformanceInterceptor();
        performanceInterceptor.setMaxTime(100); //ms 设置sql执行的最大时间，如果超过了则不执行
        performanceInterceptor.setFormat(true);
        return performanceInterceptor;
    }
```

![图片](https://mmbiz.qpic.cn/mmbiz_png/Z2CXAHBzdZGCiaNL1XOGuKZRaibIdfuUlt8jwS7kN7m1n3rOqDiayRz1BIXDOotu9gNibbhqASaOAfU527e8TGc4Vg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)图片

### 条件构造器(Wrapper)

isNotNull .gt

```java
@Test
    void contextLoads() {
        // 查询name不为空的用户，并且邮箱不为空的用户，年龄大于等于12
        QueryWrapper<User> wrapper = new QueryWrapper<>();
        wrapper
                .isNotNull("name") //不为空
                .isNotNull("email")
                .ge("age",18);
        userMapper.selectList(wrapper).forEach(System.out::println); // 和我们刚才学习的map对比一下
    }
```

![图片](https://mmbiz.qpic.cn/mmbiz_png/Z2CXAHBzdZGCiaNL1XOGuKZRaibIdfuUltKY9oNvxkGBeI1n2Z6un31WMSldib6by7HicrpZkVmibzmhCvvNicV0vDtw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)图片

.eq

```java
 @Test
    void test2(){
        // 查询名字kwhua
        QueryWrapper<User> wrapper = new QueryWrapper<>();
        wrapper.eq("name","kwhua");
        User user = userMapper.selectOne(wrapper); // 查询一个数据用selectOne，查询多个结果使用List 或者 Map
        System.out.println(user);
    }
```

其他方法可以自己测试...

### 代码自动生成器

```java
// 代码自动生成器
public class generateCode {
   public static void main(String[] args) {
    // 需要构建一个 代码自动生成器 对象
    AutoGenerator mpg = new AutoGenerator();
    // 配置策略
    // 1、全局配置
    GlobalConfig gc = new GlobalConfig();
    String projectPath = System.getProperty("user.dir");
    gc.setOutputDir(projectPath+"/src/main/java");
    gc.setAuthor("kwhua");//作者名称
    gc.setOpen(false);
    gc.setFileOverride(false); // 是否覆盖
    gc.setIdType(IdType.ID_WORKER);
    gc.setDateType(DateType.ONLY_DATE);
    gc.setSwagger2(true);//实体属性 Swagger2 注解

    // 自定义文件命名，注意 %s 会自动填充表实体属性！
    gc.setServiceName("%sService"); 
    gc.setControllerName("%sController");
    gc.setServiceName("%sService");
    gc.setServiceImplName("%sServiceImpl");
    gc.setMapperName("%sMapper");
    gc.setXmlName("%sMapper");

    mpg.setGlobalConfig(gc);

    //2、设置数据源
    DataSourceConfig dsc = new DataSourceConfig();
    dsc.setUrl("jdbc:mysql://localhost:3306/kwhua_test?
useSSL=false&useUnicode=true&characterEncoding=utf-8&serverTimezone=GMT%2B8");
    dsc.setDriverName("com.mysql.cj.jdbc.Driver");
    // dsc.setDriverName("com.mysql.jdbc.Driver"); //mysql5.6以下的驱动
    dsc.setUsername("root");
    dsc.setPassword("root");
    dsc.setDbType(DbType.MYSQL);
    mpg.setDataSource(dsc);
    //3、包的配置
    PackageConfig pc = new PackageConfig();
    pc.setParent("com.kwhua"); //包名
    pc.setModuleName("model"); //模块名
    pc.setEntity("entity");
    pc.setMapper("mapper");
    pc.setService("service");
    pc.setController("controller");
    mpg.setPackageInfo(pc);

    //4、策略配置
    StrategyConfig strategy = new StrategyConfig();
    strategy.setInclude("user","course"); // 设置要映射的表名
    strategy.setNaming(NamingStrategy.underline_to_camel);
    strategy.setColumnNaming(NamingStrategy.underline_to_camel);
    strategy.setEntityLombokModel(true); // 自动lombok；
    strategy.setLogicDeleteFieldName("deleted");
    // 自动填充配置
    TableFill gmtCreate = new TableFill("gmt_create", FieldFill.INSERT);
    TableFill gmtModified = new TableFill("gmt_modified",FieldFill.INSERT_UPDATE);
    ArrayList<TableFill> tableFills = new ArrayList<>();
    tableFills.add(gmtCreate);
    tableFills.add(gmtModified);
    strategy.setTableFillList(tableFills);
    // 乐观锁
    strategy.setVersionFieldName("version");
    //根据你的表名来建对应的类名，如果你的表名没有下划线，比如test，那么你就可以取消这一步
    strategy.setTablePrefix("t_");
    strategy.setRestControllerStyle(true); //rest请求
    //自动转下划线，比如localhost:8080/hello_id_2
    strategy.setControllerMappingHyphenStyle(true); 
    mpg.setStrategy(strategy);
    mpg.execute(); //执行
 }
}
```

执行主方法即可生成对应代码



# Code Review

## 有必要做 Code Review 吗？？？

链接：https://juejin.im/post/6882333635203039239

众所周知，Code Review是开发过程中一个非常重要的环节，但是很多公司或者团队是没有这一环节的，今天笔者结合自己所在团队，浅谈Code Review的价值及如何实施。

## **1. Code Review的价值**

许多团队没有Code Review环节，或者因为追求项目快速上线，认为CR浪费时间；或者团队成员缺少CR观念，认为CR的价值并不大。所以想要推动CR在团队中的实施，最最重要的一点便是增强团队成员对CR环节的认同感。

Code Review环节，它更加依赖于团队成员的主观能动性，只有团队成员对其认可，他们才会积极地参入这一环节，CR的价值才能最大化的体现。如果团队成员不认可CR，即使强制设置了CR流程，也是形同虚设，反而可能阻碍正常开发流程的效率。那么如何让团队成员认可CR环节呢，自然是让他们意识到CR的价值，然后就会……真香！



#### **1.1 提升团队代码质量**

随着团队规模的扩大和项目的迭代升级，团队之间的信息透明度会越来越低，项目的可维护性也会越来越差，可能引发如下一系列问题：

- 已有的utils方法，重复造轮子
- 代码过于复杂，缺少必要注释，后人难以维护
- 目录结构五花八门，杂乱不堪

……

合理的CR环节，可以有效地把控每次提交的代码质量，不至于让项目的可维护性随着版本迭代和时间推移变得太差，这也是CR的首要目的。CR环节并不会降低开发效率，就一次代码提交来说，也许部分人认为CR可能花费了时间，但是有效的CR给后人扩展和维护时所节省的时间是远超于此的。



#### **1.2 团队技术交流**

Reviewer和Reviewee，在参与CR的过程中，都是可以收获到许多知识，进行技术交流的。

- 有利于帮助新人快速成长，团队有新人加入时（如实习生和校招生），往往需要以为导师带领一段时间，通过CR环节，可以使导师最直接的了解到新人开发过程中所遇到的问题，作出相应的指导。

- 通过CR环节，团队成员可以了解他人的业务，而不局限于自己的所负责的业务范围。项目发现问题时，可以迅速定位到相关业务的负责人进行修改。同时若有的团队成员离职后，也可以减少业务一人负责所带来的后期维护困难。

- 学习他人的优秀代码。通过CR环节，可以迅速接触到团队成员在项目中解决某些问题的优秀代码，或者使用的一些你所未接触过的一些api等。

  

#### **1.3 保证项目的统一规范**

既然要进行CR，首先要对项目的规范制定要求，包括编码风格规范、目录结构规范、业务规范等等。一方面，统一的项目规范才能保证项目的代码质量，提高项目的质量和可维护性；另一方面，在大家熟悉了统一的规范后，能够提升CR的效率，节省时间。



## **2. Code Review的实践**

关于Code Review的实践，要考虑的包括CR所花费的时间、CR的形式、何时进行CR等等。



#### **2.1 预留CR的时间**

首先不得不承认，CR环节是要耗费一定时间的，所以在项目排期中，不仅要考虑开发、联调、提测、改bug等时间，还要预留出CR的时间。包括担任Reviewer和Reviewee角色的时间都要考虑。

另外如果遇到的需求比较复杂，为了避免因为CR过程导致代码需要大量修改，最好提前和团队成员沟通好需求的设计和结果思路。



#### **2.2 CR的形式**

我所见过的CR大多有两种形式。一种是设立一个特定时间，例如每周或者每半月等等，团队成员一起对之前的Merge Request进行CR；另一种是对每次的Merge Request都进行CR。

我个人更偏向于后者。第一种定期CR，Merge Request的数量太多，不太可能对所有的MR进行CR，如果CR之后再对之前的诸多MR进行修改成本太大；而且一次性太多的CR会打击团队成员的积极性。第二种MR相对就轻松的多，可以考虑轮班每天设置2-3人对当天的MR进行CR即可。



#### **2.3 CR的时机**

CR的环节应该设立在提测环节之前。因为CR后如果优化代码虽然理论上只是代码优化，但很可能会对业务逻辑产生影响，如果在提测时候，那么可能会影响到已经测试过的功能点。

当然也要分情况，如果遇到比较紧急的需求或者bug修复，那么也可以先提测，后续再做相应的CR。



## **3. 对团队成员要求**

前面已经提到，要增强团队成员对CR环节的认同感。作为CR环节的参与者，还应该根据自己的团队特点，对团队成员做出相应要求，可以参考我们团队。



#### **3.1 Reviewer**

- 指明review的级别。reviewer再给相应的代码添加评论时，建议指明评论的级别，可以在评论前用[]作出标识，例如：

- - [request]xxxxxxx　　　　　　　此条评论的代码必须修改才能予以通过
  - [advise]xxxxxxxx　　　　　　　此条评论的代码建议修改，但不修改也可以通过
  - [question]xxxxxx　　　　　　　此条评论的代码有疑问，需reviewee进一步解释

- 讲明该评论的原因。在对代码做出评论时，应当解释清楚原因，如果自己有现成的更好地解决思路，应该把相应的解决思路也评论上，节省reviewee的修改时间。

- 平等友善的评论。评论者在review的过程中，目的是提升项目代码质量，而不是抨击别人，质疑别人的能力，应该保持平等友善的语气。

- 享受Code Review。只有积极的参与CR，把CR作为一种享受，才能将CR的价值最大化的体现。

#### **3.2 Reviewee**

- 注重注释。对于复杂代码写明相应注释，在进行commit时也应简明的写清楚背景，帮助reviewer理解，提高review的效率。
- 保持乐观的心态接受别人的review。团队成员的review不是对你的批判，而是帮助你的提升，所以要尊重别人的review，如果review你感觉不正确，可以在下面提出疑问，进一步解释。
- 完成相应review的修改应当在下面及时进行回复，保持信息同步



























