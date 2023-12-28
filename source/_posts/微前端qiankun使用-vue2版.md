---
title: 微前端qiankun的使用——vue2版
excerpt: 微前端qiankun的使用——vue2版
categories:
  - 微前端
tags:
  - qiankun
date: 2023-12-28 16:59
---
# 微前端qiankun的使用——vue2版

## 一、微前端

### 什么是微前端？

微前端是将微服务理念应用于前端，将前端应用由一个单体应用转变为由多个小型独立应用的嵌合一体的应用。

### 微前端可以解决的现实问题：

-  将一个大的功能应用拆分为多个独立的子应用，各个子应用之间技术栈完全独立，可以分配给多个团队开发，提高开发效率。
- 对于一个体量大的前端应用，由于node内存限制，打包时不仅需要的时间增长，而且还可能出现内存溢出的问题，使用微前端之后，各个子应用可以分开打包，打包速度提高。
- 对于开发时间较为久远且技术栈较为老旧的前端应用，想要重构或是新添功能时开发成本巨大，此时使用微前端，便可以使用最新的技术来开发新需求并直接接入老应用中，而对老应用不影响。

### 微前端的核心价值

- 技术栈无关
  - 主应用和子应用之间以及各个子应用之间不限制技术栈，自由度高
- 独立开发，独立部署，独立运行
  - 微服务可以使得后端各个服务之间完全独立，互不影响。微前端同样如此，可以使各个子应用之间相对独立
- 增量升级
  - 上文中可解决的现实问题中以及提及

## 一、qiankun

qiankun是一种实现微前端的手段，使用qiankun与其他前端依赖库一样，只需要在主应用中配置子应用的入口和在子应用中配置识别qiankun环境的加载方式就可以实现微前端。

### 为什么不使用iframe

在传统的子应用“嵌入”主应用的实现方式中，iframe确实是一种常用的选择，但是使用iframe会产生的问题也很难避免。

#### iframe的缺点

- url丢失。
  - 刷新页面之后，当前状态下iframe显示的url会丢失，且页面中的前进后退效果无法使用。
- ui不同步。
  - 由于iframe内外DOM隔离，所以主，子应用之间的样式也被隔绝
- 加载速度慢
  - 每次刷新页面之后，iframe中的资源都需要重新请求
- 数据隔离。
  - 内外主，子应用内存变量不共享，导致内外通信困难

以上的问题不是完全不能解决，但是解决这些问题需要的时间成本较高，且交互不灵活。

## 三、qiankun使用

1. 使用Vue CIL新建一个test-a项目作为主应用，同样新建一个test-b作为子应用

```js
vue create test-a
vue create test-b
```

2. 搭建主应用基本框架：在test-a中下载element UI并应用，再使用layout布局搭建最基本的系统结构

![](C:\Users\Dell\Desktop\chen77-hexo-myblog\source\img\qiankuun\4.png)

实现形如这样的样式，就是一个常见的最基本的主应用结构了，注意此时主应用的运行地址是http://localhost:8080，**要注意主，子应用的地址不能相同**

3. 在主应用test-a中，下载qiankun依赖

```js
npm install qiankun
```

4. 在主应用test-a的入口文件main.js中，定义子应用的入口

![](C:\Users\Dell\Desktop\chen77-hexo-myblog\source\img\qiankuun\3.png)

```js
// qiankun
// start
import { registerMicroApps, start} from 'qiankun';

registerMicroApps([
  {
    name: 'childApp',			// 自定义的微应用名称
    entry: '//localhost:8081',	// 访问子应用的域名和端口号
    container: '#MainchildApp',	// 指定子应用渲染的容器（须在页面中提前声明）
    activeRule: '/childApp',	// 匹配不同子应用的路由规则
  }
]);
start();
// end
```

其中的【container】是指这个名为【name:'childApp'】的子应用要挂载的地方

5. 在主应用test-a中添加子应用需要挂载的位置，注意此时的id需要与以上定义的入口容器相互匹配

例如：

![](C:\Users\Dell\Desktop\chen77-hexo-myblog\source\img\qiankuun\2.png)

6. 在主应用的路由中设置与子应用对应的路由，但是主应用中与子路由相关的路由必须要一个标识（对应入口文件中定义的【activeRule】）

例如：

![](C:\Users\Dell\Desktop\chen77-hexo-myblog\source\img\qiankuun\1.png)

7. 设置子应用的服务路由

![](C:\Users\Dell\Desktop\chen77-hexo-myblog\source\img\qiankuun\5.png)

```js
devServer: {
    // 固定端口号
    port: 8081,
    open: true,
    host: 'localhost',
    headers: {
      "Access-Control-Allow-Origin": "*"//允许跨域
    }
  },
```

8. 在子应用中配置打包

![](C:\Users\Dell\Desktop\chen77-hexo-myblog\source\img\qiankuun\6.png)

```js
 // 配置打包！！！！
  configureWebpack: {
    output: {
      library: 'childApp',
      libraryTarget: 'umd'
    }
  }
```

9. 在子应用中的new [VueRouter](https://so.csdn.net/so/search?q=VueRouter&spm=1001.2101.3001.7020)的base要进行是否是qiankun的判断，加 “/childApp”（与主应用【activeRule】对应） , 是因为主应用要通过这个来进行激活规则

![](C:\Users\Dell\Desktop\chen77-hexo-myblog\source\img\qiankuun\77.png)

```js
const router = new VueRouter({
    // qiankun环境监测
    base: window.__POWERED_BY_QIANKUN__ ? '/childApp/' : '/',
    mode: 'history', // 使用 HTML5 历史模式，也可以使用默认的 hash 模式
    routes
});
```

10. 在子应用的入口文件main.js中添加qiankun生命周期函数

![](C:\Users\Dell\Desktop\chen77-hexo-myblog\source\img\qiankuun\8.png)

```js
if(window.__POWERED_BY_QIANKUN__){
  __webpack_public_path__=window.__INJECTED_PUBLIC_PATH_BY_QIANKUN__
}
let instance=null;
if(!window.__POWERED_BY_QIANKUN__){
  render();
}

function render(props){
  const {container}=props||{};
  instance=new Vue({
    router,
    render:h=>h(App),
  }).$mount(container?container.querySelector('#App'):"#App")
}
export async function bootstrap(){
  console.log("bootstrap");
}

export async function mount(props){
  console.log("mount-----");
  render(props);
}
export async function unmount(props){
  console.log("unmount--------");
  
  instance.$destroy()
}
export async function update(props){
  console.log("update----");
  render(props);
}

```

11. *__webpack_public_path__*可能会报错，需要在package.json中添加全局配置

![](C:\Users\Dell\Desktop\chen77-hexo-myblog\source\img\qiankuun\9.png)

```json
 "globals": {
      "__webpack_public_path__":true
    }
```

12. 在主应用菜单中配置对应的路由，进行使用

![](C:\Users\Dell\Desktop\chen77-hexo-myblog\source\img\qiankuun\10.png)