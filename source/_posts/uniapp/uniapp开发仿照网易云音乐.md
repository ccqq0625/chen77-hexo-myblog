---
title: uni-app开发仿照网易云音乐项目
excerpt: uniapp开发练习
categories:
    - uniapp
tags:
    - uniapp
math: true
date: 2022-8-9 18:44:00
---
# uni-app开发项目-仿照网易云音乐开发流程

## 一、新建项目，完善头部组件

下载HbuliderX，新建uniapp项目，项目名称为neteaseMusic

![新建项目结构](https://ooo.0x0.ooo/2024/03/08/Oyfa5v.png)

新建组件文件夹，新建组件musicHead组件

![新建组件文件夹](https://ooo.0x0.ooo/2024/03/08/OyfoKq.png)

![组件文件初始化](https://ooo.0x0.ooo/2024/03/08/OyfqSc.png)

引入icon资源文件

![引入icon资源文件](https://ooo.0x0.ooo/2024/03/08/Oyf5wr.png)

在主页导入组件musicHead

![在主页导入组件musicHead](https://ooo.0x0.ooo/2024/03/08/OyfT1M.png)

完善组件头部组件结构和布局

![完善头部组件结构和布局](https://ooo.0x0.ooo/2024/03/08/OyfUDG.png)

注意在引用阿里图标时候，要引入静态资源

![引用阿里图标](https://ooo.0x0.ooo/2024/03/08/OyfW81.png)

![image-20240308152819527](https://ooo.0x0.ooo/2024/03/08/OyfkkI.png)

最终效果：

![最终效果](https://ooo.0x0.ooo/2024/03/08/OyfxpD.png)

## 二、完善头部组件的逻辑功能

完成图标的路由跳转功能

![完成图标的路由跳转功能01](https://ooo.0x0.ooo/2024/03/08/OyfzfF.png)

![完成图标的路由跳转功能02](https://ooo.0x0.ooo/2024/03/08/Oyfh56.png)

## 三、首页任务分类-滚动区域

图标在首页隐藏

![图标在首页隐藏01](https://ooo.0x0.ooo/2024/03/08/OyfiKP.png)

![图标在首页隐藏02](https://ooo.0x0.ooo/2024/03/08/Oyfn0b.png)

搜索框静态结构：

![搜索框静态结构](https://ooo.0x0.ooo/2024/03/08/OyfN1g.png)

样式布局：

![样式](https://ooo.0x0.ooo/2024/03/08/OyfeHB.png)

得到的效果：

![效果](https://ooo.0x0.ooo/2024/03/08/Oyf1wl.png)

滚动区域布局和样式：

![滚动区域布局](https://ooo.0x0.ooo/2024/03/08/Oyfr8s.png)

![样式](https://ooo.0x0.ooo/2024/03/08/OyfZJa.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/OyfvfS.png)

## 四、运行后台

首先下载依赖`npm i`

![下载依赖](https://ooo.0x0.ooo/2024/03/08/OyfgBN.png)

再运行`node app.js`

![运行](https://ooo.0x0.ooo/2024/03/08/OyfmKC.png)

成功运行后端接口，效果:

![后端接口](https://ooo.0x0.ooo/2024/03/08/OyfPMi.png)

## 五、首页任务分类-数据渲染

查看接口文档的榜单地址：

![接口文档](https://ooo.0x0.ooo/2024/03/08/OyfR1X.png)

后台可以成功取到数据：

![验证后台数据](https://ooo.0x0.ooo/2024/03/08/OyftHt.png)

![验证后台数据](https://ooo.0x0.ooo/2024/03/08/Oyf4Xx.png)

新建api的js文件，config.js和app.js：

![config.js](https://ooo.0x0.ooo/2024/03/08/OyfHxj.png)

![app.js](https://ooo.0x0.ooo/2024/03/08/OyfLJp.png)

在首页导入获取到的数据:

![首页获取数据](https://ooo.0x0.ooo/2024/03/08/OyfElU.png)

前端后台可以成功获取到数据：

![获取到数据](https://ooo.0x0.ooo/2024/03/08/OyfQBY.png)

在静态中使用获取到的数据：

![静态中使用获取到的数据](https://ooo.0x0.ooo/2024/03/08/Oyf0cq.png)

渲染效果：

![渲染效果](https://ooo.0x0.ooo/2024/03/08/OyfdMc.png)

## 六、创建列表页

新建list页面：

![新建list页面](https://ooo.0x0.ooo/2024/03/08/Oyfs7r.png)

给榜单添加路由点击事件handleToList：

![添加路由点击事件](https://ooo.0x0.ooo/2024/03/08/OyfVLM.png)

![添加路由点击事件](https://ooo.0x0.ooo/2024/03/08/Oyflz1.png)

传递的参数是后台接口中每个榜单的id

在list页面获取传递过来的id参数：

![获取参数](https://ooo.0x0.ooo/2024/03/08/Oyf9JI.png)

实现背景图毛玻璃片效果：

结构：

![结构](https://ooo.0x0.ooo/2024/03/08/OyfjlD.png)

样式：

![样式](https://ooo.0x0.ooo/2024/03/08/Oyf8Z6.png)

效果：

![毛玻璃效果](https://ooo.0x0.ooo/2024/03/08/OyfXcP.png)

在list页面引入musichead组件：

同时传递一个颜色的参数color为白色white

![引入musichead组件](https://ooo.0x0.ooo/2024/03/08/OyfIOb.png)

在musicHead组件中新增一个关于颜色样式的参数color：

![新增一个关于颜色样式的参数](https://ooo.0x0.ooo/2024/03/08/OyfCLg.png)

为开发便利，在项目全局引入iconfont.css：

![全局引入iconfont.css](https://ooo.0x0.ooo/2024/03/08/OyfwuB.png)

最后效果：

![最后效果](https://ooo.0x0.ooo/2024/03/08/OylOzs.png)

## 七、列表页-头布局

结构：

![结构](https://ooo.0x0.ooo/2024/03/08/OylaPK.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/Oyl5TS.png)

样式修改：

![样式修改](https://ooo.0x0.ooo/2024/03/08/OylBvN.png)

为便于观察，换张背景图：

![换张背景图](https://ooo.0x0.ooo/2024/03/08/OylTcC.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/OylWOL.png)

## 八、列表页-分享和歌单布局

结构：

![结构](https://ooo.0x0.ooo/2024/03/08/OylbNi.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/OylkLX.png)

样式修改：

![样式修改](https://ooo.0x0.ooo/2024/03/08/Oylxut.png)

效果：

![效果](https://img.picgo.net/2024/03/08/imagee9117a05ccfc801f.png)

歌曲列表布局：

![歌曲列表布局](https://ooo.0x0.ooo/2024/03/08/OylPyF.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/OylRd6.png)

样式修改：

![样式修改](https://ooo.0x0.ooo/2024/03/08/Oyl4aP.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/OylDeb.png)

## 九、列表页-分享和歌单页面的数据获取

获取歌单数据：

![获取歌单数据](https://ooo.0x0.ooo/2024/03/08/OyllGi.png)

在页面引入：

![在页面引入](https://ooo.0x0.ooo/2024/03/08/Oyl9IX.png)

![初始化请求](https://ooo.0x0.ooo/2024/03/08/Oyl2ht.png)

后台成功打印出数据：

![后台成功打印出数据](https://ooo.0x0.ooo/2024/03/08/Oyl6tx.png)

将数据渲染，在页面中使用：

![数据渲染](https://ooo.0x0.ooo/2024/03/08/Oyl8jj.png)

```vue
<template>
    <view class="list">
        <view class="fixbg"></view>
        <musichead title="歌单" icon='true' color="white"></musichead>
        <view class="container">
            <scroll-view scroll-y="true">
                <view class="list-head">
                    <view class="list-head-img">
                        <image :src="playlist.coverImgUrl" mode=""></image>
                        <text class="iconfont iconyousanjiao">{{playlist.playCount | formatCount}}</text>
                        
                    </view>
                    <view class="list-head-text">
                        <view class="">
                            {{playlist.name}}
                        </view>
                        <view class="">
                            <image :src="playlist.creator.avatarUrl" mode=""></image>
                            {{playlist.creator.nickname}}
                        </view>
                        <view class="">
                            {{playlist.description}}
                        </view>
                    </view>
                </view>
                <!-- 分享按钮 -->
                <button class="list-share" open-type="share">
                    <text class="iconfont iconicon-"></text>分享给微信好友
                </button>
                <!-- 歌曲列表 -->
                <view class="list-music">
                    <view class="list-music-head">
                        <text class="iconfont iconbofang1"></text>
                        <text>播放全部</text>
                        <text>({{playlist.tracks.length}}首)</text>
                    </view>
                <!--    <view class="list-music-item">
                        <view class="list-music-top">1</view>
                        <view class="list-music-song">
                            <view class="">与我有关</view>
                            <view class="">
                                <image src="../../static/dujia.png" mode=""></image>
                                <image src="../../static/sq.png" mode=""></image>
                                阿冗-与我有关
                            </view>
                        </view>
                        <text class="iconfont iconbofang1"></text>
                    </view> -->
                    <view class="list-music-item" v-for="(item,index) in playlist.tracks">
                        <view class="list-music-top">{{index+1}}</view>
                        <view class="list-music-song">
                            <view class="">{{item.name}}</view>
                            <view class="">
                                <image v-if="privileges[index].flag>60&&privileges[index].flag<70" src="../../static/dujia.png" mode=""></image>
                                <image src="../../static/sq.png" mode=""></image>
                                {{item.ar[0].name}} - {{item.name}}
                            </view>
                        </view>
                        <text class="iconfont iconbofang1"></text>
                    </view>
                </view>
            </scroll-view>
        </view>
    </view>
</template>

```

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/OyluWp.png)

设置数字过滤器：

![设置数字过滤器](https://ooo.0x0.ooo/2024/03/08/OylIgU.png)

使得过万或是过亿的数字过滤掉后几位，然后带上相应地带上单位（万/亿）

![设置数字过滤器](https://ooo.0x0.ooo/2024/03/08/Oyl3sY.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/Oylwov.png)

更改歌单毛玻璃背景图：

![更改歌单毛玻璃背景图](https://ooo.0x0.ooo/2024/03/08/Oy9Mrq.png)

数据加载loading….：

![数据加载](https://ooo.0x0.ooo/2024/03/08/Oy9OGc.png)

## 十、歌曲详情页-初级配置

新建详情页：

![新建详情页](https://ooo.0x0.ooo/2024/03/08/Oy9a3r.png)

设置歌单跳转歌曲详情页方法：

![跳转歌曲详情页方法](https://ooo.0x0.ooo/2024/03/08/Oy9qiM.png)

Item.id是当前歌曲的id：

![跳转歌曲详情页方法](https://ooo.0x0.ooo/2024/03/08/Oy95tG.png)

修改歌曲详情页，查看详情页是否可以接收到歌曲id：

![接收到歌曲id](https://ooo.0x0.ooo/2024/03/08/Oy9B21.png)

随意点击一首歌，可以发生跳转并成功接收到歌曲id：

![测试](https://ooo.0x0.ooo/2024/03/08/Oy9UWI.png)

## 十一、歌曲详情页-布局

静态布局：

![详情页静布局](https://ooo.0x0.ooo/2024/03/08/Oy9bVF.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/Oy9xo6.png)

静态样式：

![静态样式](https://ooo.0x0.ooo/2024/03/08/Oy9zrP.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/Oy9FQb.png)

歌词部分布局：

![歌词部分布局](https://ooo.0x0.ooo/2024/03/08/Oy9h3l.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/Oy9nig.png)

样式修改：

![样式修改](https://ooo.0x0.ooo/2024/03/08/Oy914B.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/Oy972s.png)

收藏列表的布局：

![收藏列表的布局](https://ooo.0x0.ooo/2024/03/08/Oy9ebK.png)

样式：

![样式](https://ooo.0x0.ooo/2024/03/08/Oy9rma.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/Oy9AVS.png)

精彩评论布局：

![精彩评论布局](https://ooo.0x0.ooo/2024/03/08/Oy9ZqN.png)

样式美化：

![样式美化](https://ooo.0x0.ooo/2024/03/08/Oy9vrC.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/Oy9yQL.png)

## 十二、歌曲详情页-接口数据

接口方法：获取歌曲详情：

![获取歌曲详情](https://ooo.0x0.ooo/2024/03/08/Oy9gCi.png)

获取歌曲评论：

![获取歌曲评论](https://ooo.0x0.ooo/2024/03/08/Oy9piX.png)

获取歌词音频：

![获取歌词音频](https://ooo.0x0.ooo/2024/03/08/Oy9J4t.png)

获取相似歌曲：

![获取相似歌曲](https://ooo.0x0.ooo/2024/03/08/Oy9P6x.png)

获取歌词：

![获取歌词](https://ooo.0x0.ooo/2024/03/08/Oy9tbj.png)

## 十三、歌曲详情页-页面的数据渲染

将接口方法引入页面：

![将接口方法引入页面](https://ooo.0x0.ooo/2024/03/08/Oy94mp.png)

方法调用：

![方法调用](https://ooo.0x0.ooo/2024/03/08/Oy9DYU.png)

后台成功打印：

![后台成功打印](https://ooo.0x0.ooo/2024/03/08/Oy9LqY.png)

歌曲详情部分数据渲染：

![数据渲染](https://ooo.0x0.ooo/2024/03/08/Oy9EAv.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/Oy9GSq.png)

相似歌曲部分数据渲染：

![数据渲染](https://ooo.0x0.ooo/2024/03/08/Oy9QCc.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/Oy90nr.png)

精彩评论部分数据渲染：

![数据渲染](https://ooo.0x0.ooo/2024/03/08/Oy9cDM.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/Oy9d6G.png)

设置优化时间的过滤器：

![优化时间的过滤器](https://ooo.0x0.ooo/2024/03/08/Oy9Vk1.png)

![优化时间的过滤器](https://ooo.0x0.ooo/2024/03/08/Oy9YmI.png)

效果：

![效果](https://ooo.0x0.ooo/2024/03/08/Oy9fYD.png)

获取歌词数据：

![获取歌词数据](https://ooo.0x0.ooo/2024/03/08/Oy995F.png)

打印输出：

![打印输出](https://ooo.0x0.ooo/2024/03/08/Oy9jA6.png)

正侧处理歌词：

![正侧处理歌词](https://ooo.0x0.ooo/2024/03/08/Oy92SP.png)

效果：

![效果](https://img.picgo.net/2024/03/08/image0cc988e9ceffa16f.png)

将分钟格式化为秒：

![时间格式化](https://img.picgo.net/2024/03/08/imagead65ccf93379948d.png)

于是可以将字符串分解成对象数组：

![字符串分解成对象数组](https://img.picgo.net/2024/03/08/imaged5a3eaaa1f155024.png)

歌词部分渲染：

![歌词部分渲染](https://img.picgo.net/2024/03/08/image075541bd02fbd3da.png)

![歌词部分渲染](https://img.picgo.net/2024/03/08/image94b49811438acc97.png)

效果：

![效果](https://img.picgo.net/2024/03/08/image8ace54059bc66b96.png)

## 十四、歌曲详情页-播放联动设置

微信小程序端配置：

![微信小程序端配置](https://img.picgo.net/2024/03/08/image44c45cbe1e503a33.png)

![微信小程序端配置](https://img.picgo.net/2024/03/08/imaged8b5eb9c6bb9c274.png)

![微信小程序端配置](https://img.picgo.net/2024/03/08/imagef717b4163733a49b.png)

获取到了实例对象

![实例对象](https://img.picgo.net/2024/03/08/image57726a250ed735f9.png)

![实例对象](https://img.picgo.net/2024/03/08/imagecaf590c9d50cd1ab.png)完善：

![完善](https://img.picgo.net/2024/03/08/image7d5e9bd43b299660.png)

播放图标和图片旋转：

设置变量：

![设置变量设置变量](https://ooo.0x0.ooo/2024/03/08/Oy9wpK.png)

样式：

![样式](https://img.picgo.net/2024/03/08/image696a4673255c3b5b.png)

结构渲染：

![结构渲染](https://img.picgo.net/2024/03/08/imagebc7ab781cfc4a8f4.png)

效果：图片成功旋转起来

![图片成功旋转起来](https://img.picgo.net/2024/03/08/image799bcc3b0e9ce4a6.png)

## 十五、搜索页-静态布局

创建目录：

![创建目录](https://img.picgo.net/2024/03/08/image7dd28c7a3fb05547.png)

在index.vue页面添加路由跳转事件：

![路由跳转事件](https://img.picgo.net/2024/03/08/imageda52e32d440c0d50.png)

![路由跳转事件](https://img.picgo.net/2024/03/08/image0dfe8e006802844f.png)

搜索页search.vue页面静态布局：

![态布局](https://img.picgo.net/2024/03/08/imaged9554b3d5883cf60.png)

效果：

![效果](https://img.picgo.net/2024/03/08/image7249ba7aa3f0fd1b.png)

样式：

![样式](https://img.picgo.net/2024/03/08/imagecabf0dcaf8ac37ed.png)

效果：

![效果](https://img.picgo.net/2024/03/08/image50b3c0b1adc07d18.png)

热搜榜结构：

![热搜榜结构](https://img.picgo.net/2024/03/08/imageac71afd86b7b6721.png)

结构：

![结构](https://img.picgo.net/2024/03/08/image4c074aeb0ec957a0.png)

样式美化：

![样式美化](https://img.picgo.net/2024/03/08/image5fa8fc329a81ee2c.png)

效果：

![效果](https://img.picgo.net/2024/03/08/imageeec94a9a8f488728.png)

## 十六、搜索页-接口数据

搜索相关接口：

![搜索相关接口](https://img.picgo.net/2024/03/08/imageaeeb06b152d10c19.png)

使用接口：

![使用接口](https://img.picgo.net/2024/03/08/image6ee1c6a135b005ba.png)

测试打印成功：

![测试打印](https://img.picgo.net/2024/03/08/image2eaa0b16cf0b4e5e.png)

搜索榜数据渲染：

![搜索榜数据渲染](https://img.picgo.net/2024/03/08/image0e16d005e6b773eb.png)

![搜索榜数据渲染](https://img.picgo.net/2024/03/08/imaged1ccc7b3674d686c.png)

![搜索榜数据渲染](https://img.picgo.net/2024/03/08/imagee003d5b52e9a6cf7.png)

搜索历史数据渲染：将输入框中的字符存储在searchHistory数组中，然后在搜索历史区域循环渲染searchHistory数组，同时对该数组进行去重this.searchHistory=[...new Set(this.searchHistory)]和长度限制处理

![数据处理](https://img.picgo.net/2024/03/08/imageea12c986e7a812d0.png)

![页面渲染](https://img.picgo.net/2024/03/08/image707e4594c2c3db9f.png)

效果：

![效果](https://img.picgo.net/2024/03/08/image01736b13fdfc7c7f.png)

获得搜索结果的静态样式：

![静态结构](https://img.picgo.net/2024/03/08/imageeadf00de6acee6f4.png)

![样式](https://img.picgo.net/2024/03/08/image502b4659f24858c6.png)

调用接口获取并渲染数据：

![渲染数据](https://img.picgo.net/2024/03/08/imagee49022d419322465.png)

效果：

![效果](https://img.picgo.net/2024/03/08/imagea6408d6d2eaf456e.png)

搜索建议布局：

![布局](https://img.picgo.net/2024/03/08/imagebd121b34a2405972.png)

![样式](https://img.picgo.net/2024/03/08/image0a7f956963dca405.png)

![效果](https://img.picgo.net/2024/03/08/image81dab127c644fd92.png)

## 十七、部分代码

项目结构图：

![项目结构图](https://img.picgo.net/2024/03/08/image3dbfd65f1a87b92b.png)

common/api.js：

```js

import {
    baseUrl
} from './config.js';
// 获取榜单列表
export function topList() {
    return new Promise(function(reslove, reject) {
        uni.request({
            url: `${baseUrl}/toplist/detail`,
            method: 'GET',
            data: {},
            success: res => {
                console.log(res);
                let result = res.data.list;
                result.length = 4;
                // 将result作为参数抛出
                reslove(result);
            }
        })
    })
}
// 歌曲列表
export function list(listId) {
    return uni.request({
        url: `${baseUrl}/playlist/detail?id=${listId}`,
        method: 'GET'
    })
}
// 获取歌曲详情
export function songDetail(songId) {
    return uni.request({
        url: `${baseUrl}/song/detail?ids=${songId}`,
        method: 'GET'
    })
}
// 获取歌词
export function songLyric(songId) {
    return uni.request({
        url: `${baseUrl}/lyric?id=${songId}`,
        method: 'GET'
    })
}
// 获取歌曲url
export function songUrl(songId) {
    return uni.request({
        url: `${baseUrl}/song/url?id=${songId}`,
        method: 'GET'
    })
}
//获取相似音乐
export function songSimi(songId){
    return uni.request({
        url:`${baseUrl}/simi/song?id=${songId}`,
        method:'GET'
    })
}
//获取评论
export function songComment(songId){
    return uni.request({
        url:`${baseUrl}/comment/music?id=${songId}`
    })
}
// 热搜榜
export function searchHot(){
    return uni.request({
        url:`${baseUrl}/search/hot/detail`,
        method:'GET'
    })
}
// 搜索热词
export function searchWord(word){
    return uni.request({
        url:`${baseUrl}/search/suggest?keywords=${word}`,
        method:'GET'
    })
}
// 搜索建议
export function searchSuggest(word){
    return uni.request({
        url:`${baseUrl}/search/suggest?keywords=${word}&type=mobile`,
        method:'GET'
    })

}
```

common/config.js:

```js
// 请求根路由
export const baseUrl='http://localhost:3000';
```

common/iconfont.css:

```css
@font-face {font-family: "iconfont";
  src: url('~@/static/iconfont/iconfont.eot?t=1586310545675'); /* IE9 */
  src: url('~@/static/iconfont/iconfont.eot?t=1586310545675#iefix') format('embedded-opentype'), /* IE6-IE8 */
  url('data:application/x-font-woff2;charset=utf-8;base64,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') format('woff2'),
  url('~@/static/iconfont/iconfont.woff?t=1586310545675') format('woff'),
  url('~@/static/iconfont/iconfont.ttf?t=1586310545675') format('truetype'), /* chrome, firefox, opera, Safari, Android, iOS 4.2+ */
  url('~@/static/iconfont/iconfont.svg?t=1586310545675#iconfont') format('svg'); /* iOS 4.1- */
}
.iconfont {
  font-family: "iconfont" !important;
  font-size: 16px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.iconlajitong:before {
  content: "\e615";
}
.iconlike:before {
  content: "\e683";
}
.iconyousanjiao:before {
  content: "\e629";
}
.iconicon-:before {
  content: "\e605";
}
.iconsearch:before {
  content: "\e623";
}
.iconguanbi:before {
  content: "\e6cc";
}
.iconshouye:before {
  content: "\e60a";
}
.iconzuojiantou-copy:before {
  content: "\e653";
}
.iconpause:before {
  content: "\e673";
}
.iconbofang:before {
  content: "\e626";
}
.iconbofang1:before {
  content: "\e710";
}
```

components/musichead.vue:

```vue

<template>
    <view class="music-head" :style="{color:color}">
        <view class="music-head-icon" v-if='icon'>
            <text class="iconfont iconzuojiantou-copy" @tap="handleToBack()"></text> |
            <text class="iconfont iconshouye" @tap="handleToHome()"></text>
        </view>
        {{title}}
    </view>
</template>
<script>
    import iconfont from '../../common/iconfont.css';
    export default {
        props: ['title', 'icon','color'],
        data() {
            return {
            }
        },
        methods: {
            handleToBack() {
                // 返回上一页
                uni.navigateBack()
            },
            handleToHome() {
                // 返回主页
                uni.navigateTo({
                    url: '/pages/index/index'
                })
            }
        }
    }
</script>
<style scoped>
    .music-head {
        width: 100%;
        height: 60px;
        font-size: 16px;
        line-height: 80px;
        text-align: center;
        color: black;
        position: relative;
        overflow: hidden;
    }
    .music-head-icon {
        position: absolute;
        left: 8px;
        top: 26px;
        width: 90px;
        height: 31px;
        background: rgba(0, 0, 0, 0.4);
        color: white;
        line-height: 31px;
        border-radius: 15px;
        display: flex;
        justify-content: space-evenly;
    }
</style>

```

pages/detail/detail.vue:

```vue

<template>
    <view>
        <!-- 当前歌曲id是{{songId}} -->
        <view class="detail">
            <view class="fixbg" :style="{'background-image':'url('+songDetail.al.picUrl+')'}">
            </view>
            <musichead :title='songDetail.name' :icon="true" color="white" v-if="!isLoading"></musichead>
            <view class="container" v-show="!isLoading">
                <scroll-view scroll-y="true">
                    <view class="detail-play" @tap="handleToPlay">
                        <image :src="songDetail.al.picUrl" :class="{'detail-play-run':isPlayRotate}" mode=""></image>
                        <text class="iconfont" :class="iconPlay"></text>
                        <!-- 面条图 -->
                        <view class="">
                        </view>
                    </view>
                    <!-- 歌词 -->
                    <view class="detail-lyric">
                        <view class="detail-lyric-wrap" :style="{transform:'translateY('+ - (lyricIndex-1)*82+'rpx)'}">
                            <!-- <view class="detail-lyric-item">
                测试文字测试文字测试文字测试文字
              </view> -->
                            <view class="detail-lyric-item" :class="{active:lyricIndex==index}" 
                            v-for="(item,index) in songLyric" :key="index">
                                {{item.lyric}}
                            </view>
                        </view>
                    </view>
                    <!-- 下方列表：like表 -->
                    <view class="detail-like">
                        <view class="detail-like-head">
                            喜欢这首歌的人也听
                        </view>
                        <view class="detail-like-item" v-for="(item,index) in songSimi" :key="index"
                        @tap='handleToSimi(item.id)'>
                            <view class="detail-like-img">
                                <!-- 头像 -->
                                <image :src="item.album.picUrl" mode=""></image>
                            </view>
                            <view class="detail-like-song">
                                <!-- 歌曲 -->
                                <view>{{item.name}}</view>
                                <view class="">
                                    <image v-if="item.privilege.flag>60&&item.privilege.flag<70"
                                        src="../../static/dujia.png" mode=""></image>
                                    <image v-if="item.privilege.maxbr==999000" src="../../static/sq.png" mode="">
                                    </image>
                                    {{item.album.artists[0].name}}-{{item.name}}
                                </view>
                            </view>
                            <text class="iconfont iconbofang"></text>
                        </view>
                        <!--      <view class="detail-like-item">
              <view class="detail-like-img">
                <image src="../../static/logo.png" mode=""></image>
              </view>
              <view class="detail-like-song">
                <view>蓝</view>
                <view class="">
                  <image src="../../static/dujia.png" mode=""></image>
                  <image src="../../static/sq.png" mode=""></image>
                  石白其-蓝
                </view>
              </view>
              <text class="iconfont iconbofang"></text>
            </view> -->
                    </view>
                    <!-- 精彩评论 -->
                    <view class="detail-comment">
                        <view class="detail-comment-head">精彩评论</view>
                        <view class="detail-comment-item" v-for="(item,index) in songComment" :key="index">
                            <view class="detail-comment-img">
                                <image :src="item.user.avatarUrl" mode=""></image>
                            </view>
                            <view class="detail-comment-content">
                                <view class="detail-comment-title">
                                    <view class="detail-comment-name">
                                        <view class="">{{item.user.nickname}}</view>
                                        <view>{{item.time | formatTime}}</view>
                                    </view>
                                    <view class="detail-comment-like">
                                        {{item.likedCount|formatCount}} <text class="iconfont iconlike"></text>
                                    </view>
                                </view>
                                <!-- 评论内容 -->
                                <view class="detail-comment-text">
                                    {{item.content}}
                                </view>
                            </view>
                        </view>
                        <!-- <view class="detail-comment-item">
              <view class="detail-comment-img">
                <image src="../../static/logo.png" mode=""></image>
              </view>
              <view class="detail-comment-content">
                <view class="detail-comment-title">
                  <view class="detail-comment-name">
                    <view class="">是阿冗的冗</view>
                    <view>2020年1月2日</view>
                  </view>
                  <view class="detail-comment-like">
                    56027<text class="iconfont iconlike"></text>
                  </view>
                </view>
               评论内容 -->
                        <!--       <view class="detail-comment-text">
                  测试测试测试测试测试测试测试文字
                </view>
              </view>
            </view> --> 
                    </view>
                </scroll-view>
            </view>
        </view>
    </view>
</template>
<script>
    import musichead from '../../components/musichead/musichead.vue';
    import iconfont from '../../common/iconfont.css';
    import {
        songDetail,
        songComment,
        songSimi,
        songLyric,
        songUrl
    } from '../../common/api.js'
    export default {
        data() {
            return {
                isLoading:false,
                songId: 0,
                songDetail: {
                    name: '',
                    al: {picUrl:''}
                },
                songComment: [],
                songSimi: [],
                songLyric: [],
                lyricIndex:0,
                iconPlay:'iconpause',
                isPlayRotate:true,
            }
        },
        components:{musichead},
        onLoad(option) {
            this.songId = option.id;
            this.getMusic(this.songId);
        },
        onUnload() {
            this.cancelLyricIndex();
            // #ifdef H5
            this.bgAudioManager.destroy();
            // #endif
        },
        onHide() {
            this.cancelLyricIndex();
            // #ifdef H5
            this.bgAudioManager.destroy();
            // #endif
        },
        methods: {
        
            formatTimeToSec(value) {
                let arr = value.split(':');
                return (Number(arr[0] * 60) + Number(arr[1])).toFixed(1);
            },
            getMusic(id) {
                // 传递当前歌曲的id
                this.$store.commit('NEXT_ID',this.songId)
                uni.showLoading({
                    title:'加载中...',
                })
                this.isLoading=true;
                
                Promise.all([songDetail(id), songComment(id), songLyric(id), songSimi(id), songUrl(id)]).then((res) => {
                    // console.log('songDetail-歌曲详情', res[0]);
                    // console.log('songComment-歌曲评论', res[1]);
                    // console.log("songLyric--歌词", res[2]);
                    // console.log('songSimi-相似歌曲', res[3]);
                    console.log('songUrl--音频', res[4]);
                    if (res[0][1].data.code == '200') {
                        this.songDetail = res[0][1].data.songs[0];
                    }
                    if (res[1][1].data.code == '200') {
                        this.songComment = res[1][1].data.hotComments;
                    }
                    if (res[2][1].data.code == '200') {
                        let Lyric = res[2][1].data.lrc.lyric;
                        //console.log('歌词', Lyric);
                        let re = /\[([^\]]+)\]([^\[]+)/g;
                        var result = [];
                        Lyric.replace(re, ($0, $1, $2) => {
                            result.push({
                                'time': this.formatTimeToSec($1),
                                'lyric': $2
                            });
                        })
                        //console.log("result", result);
                        //console.log(typeof this.songLyric);
                        this.songLyric = result;
                    }
                    if (res[3][1].data.code == '200') {
                        this.songSimi = res[3][1].data.songs;
                    }
                    if (res[4][1].data.code == '200') {
                        //this.songUrl = res[4][1].data.data[0];
                        //console.log(res[4][1].data.data[0].url);
                        // #ifdef MP-WEIXIN
                        this.bgAudioManager = uni.getBackgroundAudioManager();
                        this.bgAudioManager.title=this.songDetail.name; 
                        // #endif
                        
                        // #ifdef H5
                        if(!this.bgAudioManager){
                            this.bgAudioManager=uni.createInnerAudioContext();
                        }
                        this.iconPlay='iconbofang1';
                        this.isPlayRotate=false;
                        // #endif   
                            
                        this.bgAudioManager.src=res[4][1].data.data[0].url||"";
                        this.listenLyricIndex();
                        console.log(this.bgAudioManager);
                        this.bgAudioManager.onPlay(()=>{
                            this.iconPlay='iconpause',
                            this.isPlayRotate=true;
                            this.listenLyricIndex();
                        });
                        this.bgAudioManager.onPause(()=>{
                            this.iconPlay='iconbofang1',
                            this.isPlayRotate=false;
                            this.listenLyricIndex();
                        });
                        // 当前歌曲播放结束之后，自动播放下一首
                        this.bgAudioManager.onEnded(()=>{
                            this.getMusic(this.$store.nextId);
                        });
                    }
                });
                uni.hideLoading();
                this.isLoading=false;
            },
            handleToPlay(){
                if(this.bgAudioManager.paused){
                    this.bgAudioManager.play();
                }else{
                    this.bgAudioManager.pause();
                }
            },
            //监听歌词滚动
            listenLyricIndex(){
                clearInterval(this.timer);
                this.timer=setInterval(()=>{
                    for(var i=0;i<this.songLyric.length;i++){
                        if(this.bgAudioManager.currentTime>this.songLyric[this.songLyric.length-1].time){
                            this.lyricIndex=this.songLyric.length-1;
                            break;
                        }
                        if(this.bgAudioManager.currentTime>this.songLyric[i].time&&
                        this.bgAudioManager.currentTime<this.songLyric[i+1].time){
                            this.lyricIndex=i;
                        }
                    }
                    console.log("this.lyricIndex--",this.lyricIndex);
                },500)
            },
            //关闭监听器
        cancelLyricIndex(){
            clearInterval(this.timer);
        },
        handleToSimi(songId){
            this.getMusic(songId);
        }

        }
    }
</script>
<style scoped>
    .detail-play {
        width: 580rpx;
        height: 580rpx;
        background: url(~@/static/disc.png);
        background-size: cover;
        margin: 214rpx auto 0 auto;
        position: relative;
    }
    .detail-play image {
        width: 370rpx;
        height: 370rpx;
        border-radius: 50%;
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        margin: auto;
        /* 旋转 */
        animation: 10s linear move infinite;
        animation-play-state: paused;
    }
.detail-play .detail-play-run{animation-play-state: running;}
@keyframes move{
    from{transform: rotate(0deg);}
    to{transform: rotate(360deg);}
}
    .detail-play text {
        width: 100rpx;
        height: 100rpx;
        font-size: 100rpx;
        color: white;
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        margin: auto;
    }
    .detail-play view {
        width: 230rpx;
        height: 360rpx;
        background: url(~@/static/needle.png);
        position: absolute;
        left: 60rpx;
        right: 0;
        top: -200rpx;
        margin: auto;
        background-size: cover;
    }
    /* 歌词 */
    .detail-lyric {
        font-size: 32rpx;
        line-height: 82rpx;
        height: 246rpx;
        text-align: center;
        overflow: hidden;
        color: #6f6e73;
    }
    .detail-lyric-wrap {
        transition: .5s;
    }
    .detail-lyric-item {
        height: 82rpx;
    }
    .detail-lyric-item.active {
        color: white;
    }
    /* like列表 */
    .detail-like {
        margin: 0 30rpx;
    }
    .detail-like-head {
        font-size: 36rpx;
        color: white;
        margin: 50rpx 0;
    }
    .detail-like-item {
        display: flex;
        align-items: center;
    }
    .detail-like-img {
        width: 82rpx;
        height: 82rpx;
        border-radius: 20rpx;
        overflow: hidden;
        margin-right: 20rpx;
    }
    .detail-like-img image {
        width: 100%;
        height: 100%;
    }
    .detail-like-song {
        flex: 1;
        color: #c6c2bf;
    }
    .detail-like-song view:nth-child(1) {
        font-size: 28rpx;
        color: white;
        margin-bottom: 12rpx;
    }
    .detail-like-song view:nth-child(2) {
        font-size: 22rpx;
    }
    .detail-like-song image {
        width: 26rpx;
        height: 20rpx;
        margin-right: 10rpx;
    }
    .detail-like-item text {
        font-size: 50rpx;
        color: #c6c2bf;
    }
    /* 精彩评论 */
    .detail-commet {
        margin: 0 30rpx;
    }
    .detail-comment-head {
        font-size: 36rpx;
        color: white;
        margin: 50rpx 0;
    }
    .detail-comment-item {
        margin-bottom: 28rpx;
        display: flex;
    }
    .detail-comment-img {
        width: 64rpx;
        height: 64rpx;
        border-radius: 50%;
        overflow: hidden;
        margin-right: 18rpx;
        margin-left: 18rpx;
    }
    .detail-comment-img image {
        width: 100%;
        height: 100%;
    }
    .detail-comment-content {
        flex: 1;
        color: #cbcacf;
    }
    .detail-comment-title {
        display: flex;
        justify-content: space-between;
    }
    .detail-comment-name {}
    .detail-comment-name view:nth-child(1) {
        font-size: 26rpx;
    }
    .detail-comment-name view:nth-child(2) {
        font-size: 20rpx
    }
    .detail-comment-like {
        font-size: 28rpx;
    }
    .detail-comment-text {
        font-size: 28rpx;
        line-height: 40rpx;
        color: white;
        margin-top: 20rpx;
        border-bottom: 1px solid #cbcacf;
        padding-bottom: 40rpx;
    }
</style>

```

pages/index/index.vue:

```vue

<template>
    <!-- 主页：启动页 -->
    <view class="content">
        <musichead title="云音乐" :icon="false"></musichead>
        <view class="container">
            <scroll-view scroll-y="true">
                <view class="index-search" @tap="handleSearch()">
                    <text class="iconfont iconsearch"></text>
                    <input type="text" placeholder="搜索歌曲">
                </view>
                <!-- 滚动区域 -->
                <view class="index-list">
                    <!-- <view class="index-list-item">
                        <view class="index-list-img">
                            <image src="../../static/wangyiyunyinyue.png" mode=""></image>
                            <text>每天更新</text>
                        </view>
                        <view class="index-list-text">
                            <view class="">1.与我无关-阿冗</view>
                            <view class="">1.与我无关-阿冗</view>
                            <view class="">1.与我无关-阿冗</view>
                        </view>
                    </view> -->
                    <view class="index-list-item" v-for="(item,index) in topList" :key="index" @tap="handToList(item.id)"
                    >
                        <view class="index-list-img">
                            <image :src="item.coverImgUrl" mode=""></image>
                            <text>{{item.updateFrequency}}</text>
                        </view>
                        <view class="index-list-text">
                            <view class="" v-for="(item1,index1) in item.tracks">
                                {{index1+1}}.{{item1.first}}--{{item1.second}}</view>
                        </view>
                    </view>



                </view>
            </scroll-view>
        </view>
    </view>
</template>
<script>
    import musichead from '../../components/musichead/musichead.vue';
    import {
        topList
    } from '../../common/api.js'
    export default {
        data() {
            return {
                topList: []
            }
        },
        components: {
            musichead
        },
        onLoad() {
            topList().then((res) => {
                    if (res.length) {
                        this.topList = res;
                        console.log("榜单数据", this.topList);
                    }
                })
        },
        methods: {
            handToList(listId) {
                //跳转到歌单详情页
                uni.navigateTo({
                    url: `/pages/list/list?id=`+listId,
                })
            },
            handleSearch(){
                uni.navigateTo({
                    url:'/pages/search/search',
                })
            }
        }
    }
</script>
<style scopd>
    .index {}
    .index-search {
        display: flex;
        align-items: center;
        height: 70rpx;
        margin: 5rpx 30rpx 30rpx 30rpx;
        background: #f7f7f7;
        border-radius: 50rpx;
    }
    .index-search text {
        font-size: 26rpx;
        margin-right: 26rpx;
        margin-left: 28rpx;
    }
    .index-search input {
        flex: 1;
        font-size: 28rpx;
    }
    /* 滚动区域 */
    .index-list {
        margin: 0 30rpx;
    }
    .index-list-item {
        display: flex;
        margin-bottom: 34rpx;
    }
    .index-list-img {
        width: 212rpx;
        height: 212rpx;
        position: relative;
        border: 30rpx;
        overflow: hidden;
        margin-right: 22rpx;
    }
    .index-list-img image {
        width: 100%;
        height: 100%;
    }
    .index-list-img text {
        position: absolute;
        left: 12rpx;
        bottom: 16rpx;
        color: white;
        font-size: 20rpx;
    }
    .index-list-text {
        font-size: 24rpx;
        line-height: 66rpx;
    }
</style>

```

pages/list/list.vue:

```vue

<template>
    <view class="list">
        <view class="fixbg" :style="{'background-image':'url('+playlist.coverImgUrl+')'}"></view>
        <musichead title="歌单" icon='true' color="white"></musichead>
        <view class="container">
            <scroll-view scroll-y="true">
                <view class="list-head">
                    <view class="list-head-img">
                        <image :src="playlist.coverImgUrl" mode=""></image>
                        <text class="iconfont iconyousanjiao">{{playlist.playCount |formatCount}}</text>
                    </view>
                    <view class="list-head-text">
                        <view class="">
                            {{playlist.name}}
                        </view>
                        <view class="">
                            <image :src="playlist.creator.avatarUrl" mode=""></image>
                            {{playlist.creator.nickname}}
                        </view>
                        <view class="">
                            {{playlist.description}}
                        </view>
                    </view>
                </view>
                <!-- 分享按钮 -->
                <button class="list-share" open-type="share">
                    <text class="iconfont iconicon-"></text>分享给微信好友
                </button>
                <!-- 歌曲列表 -->
                <view class="list-music">
                    <view class="list-music-head">
                        <text class="iconfont iconbofang1"></text>
                        <text>播放全部</text>
                        <text>({{playlist.tracks.length}}首)</text>
                    </view>
                    <!--    <view class="list-music-item">
                        <view class="list-music-top">1</view>
                        <view class="list-music-song">
                            <view class="">与我有关</view>
                            <view class="">
                                <image src="../../static/dujia.png" mode=""></image>
                                <image src="../../static/sq.png" mode=""></image>
                                阿冗-与我有关
                            </view>
                        </view>
                        <text class="iconfont iconbofang1"></text>
                    </view> -->
                    <view class="list-music-item" v-for="(item,index) in playlist.tracks" :key="index"
                        @tap="handleToDetail(item.id)">
                        <view class="list-music-top">{{index+1}}</view>
                        <view class="list-music-song">
                            <view class="">{{item.name}}</view>
                            <view class="">
                                <image v-if="privileges[index].flag>60&&privileges[index].flag<70"
                                    src="../../static/dujia.png" mode=""></image>
                                <image src="../../static/sq.png" mode=""></image>
                                {{item.ar[0].name}} - {{item.name}}
                            </view>
                        </view>
                        <text class="iconfont iconbofang1"></text>
                    </view>
                </view>



            </scroll-view>
        </view>
    </view>
</template>
<script>
    import musichead from '../../components/musichead/musichead.vue';
    import {
        list
    } from '../../common/api.js'
    export default {
        data() {
            return {
                id: '',
                playlist: {
                    coverImgUrl: '',
                    creator: {
                        avatarUrl: ''
                    },
                    tracks: []
                },
                privileges: [],
            }
        },
        components: {
            musichead
        },
        onLoad(options) {
            // 根据当前页路由获取id
            console.log(options.id)
            // 榜单的id，以便获取详细榜单歌曲数据
            this.id = options.id;
            uni.showLoading({
                title: '加载中...'
            })
            list(options.id).then((res) => {
                console.log("响应歌曲", res);
                if (res[1].data.code == '200') {
                    this.playlist = res[1].data.playlist;
                    this.privileges = res[1].data.privileges;
                    this.$store.commit('INIT_TOPLISTDS',res[1].data.playlist.trackIds);
                    // 表单中所有歌曲的id
                    console.log('list',res[1].data.playlist.trackIds);
                    console.log('列表', this.playlist);
                    
                }
            })
            uni.hideLoading();
        },
        methods: {
            handleToDetail(songId) {
                uni.navigateTo({
                    url: '/pages/detail/detail?id=' + songId
                })
            }
        }
    }
</script>
<style scoped>
    .list-head {
        display: flex;
        margin: 30rpx;
    }
    .list-head-img {
        width: 300rpx;
        height: 264rpx;
        border-radius: 30rpx;
        overflow: hidden;
        position: relative;
        margin-right: 42rpx;
    }
    .list-head-img image {
        width: 100%;
        height: 100%;
    }
    .list-head-img text {
        position: absolute;
        right: 8rpx;
        top: 8rpx;
        color: white;
        font-size: 26rpx;
    }
    .list-head-text view:nth-child(1) {
        color: white;
        font-size: 34rpx;
    }
    .list-head-text view:nth-child(2) {
        color: white;
        display: flex;
        margin: 20rpx 0;
        font-size: 24rpx;
        align-items: center;
    }
    .list-head-text view:nth-child(2) image {
        width: 54rpx;
        height: 54rpx;
        border: 50%;
        border-radius: 50%;
        margin-right: 14rpx;
    }
    .list-head-text view:nth-child(3) {
        color: white;
        line-height: 34rpx;
        font-size: 22rpx;
    }
    /* 分享 */
    .list-share {
        width: 330rpx;
        height: 74rpx;
        margin: 0 auto;
        background: rgba(0, 0, 0, 0.4);
        border-radius: 37px;
        color: white;
        text-align: center;
        line-height: 74rpx;
        font-size: 28rpx;
    }
    .list-share text {
        margin-right: 18rpx;
    }
    /* 歌曲列表 */
    .list-music {
        background: white;
        border-radius: 50rpx;
        margin-top: 40rpx;
        overflow: hidden;
    }
    .list-music-head {
        height: 50rpx;
        margin: 30rpx 0 70rpx 30rpx;
    }
    .list-music-head text:nth-child(1) {
        height: 50rpx;
        font-size: 50rpx;
        margin-left: 20rpx;
    }
    .list-music-head text:nth-child(2) {
        font-size: 30rpx;
        margin: 0rpx 10rpx 0 26rpx;
    }
    .list-music-head text:nth-child(3) {
        font-size: 26rpx;
        color: #b2b2b2;
    }
    .list-music-item {
        display: flex;
        margin: 0 32rpx 66rpx 46rpx;
        align-items: center;
        color: #959595;
    }
    .list-music-top {
        width: 58rpx;
        font-size: 50rpx;
        line-height: 50rpx;
    }
    .list-music-song {
        flex: 1;
    }
    .list-music-song view:nth-child(1) {
        font-size: 28rpx;
        color: black;
        width: 70vw;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }
    .list-music-song view:nth-child(2) {
        font-size: 20rpx;
        align-items: center;
        width: 60vw;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }
    .list-music-song view:nth-child(2) image {
        width: 32rpx;
        height: 20rpx;
        margin-right: 10rpx;
        flex-shrink: 0;
    }
    .list-music-item text {
        font-size: 50rpx;
        color: #c7c7c7;
    }
</style>

```

pages/search/search.vue:

```vue
<template>
    <view class="search">
        <musichead title="搜索" icon="true"></musichead>
        <view class="container">
            <scroll-view scroll-y="true">
                <!-- 搜索框 -->
                <view class="search-search">
                    <text class="iconfont iconsearch"></text>
                    <input type="text" placeholder="搜索歌曲" v-model="searchWord" @confirm="handleToSearch(searchWord)"
                    @input="handleToSuggest">
                    <text class="iconfont iconguanbi" @tap="handleToClose()"></text>
                </view>
                <block v-if="searchType==1">
                <!-- 历史记录 -->
                <view class="search-history">
                    <view class="search-history-head">
                        <text>历史记录</text>
                        <text class="iconfont iconlajitong" @tap="handleToClear()"></text>
                    </view>
                    <view class="search-history-list">
                        <view v-for="(item,index) in searchHistory" :key="index" @tap="handleToWord(item)">
                        {{item}}</view>
                    </view>
                </view>
                <!-- 热搜榜 -->
                <view class="search-hot">
                    <view class="search-hot-head">
                        热搜榜
                    </view>
                <!--    <view class="search-hot-item">
                        <view class="search-hot-top">
                            1
                        </view>
                        <view class="search-hot-word">
                            <view class="">
                                少年<image src="../../static/dujia.png" mode="aspectFill"></image>
                            </view>
                            <view>"少年"一词太美</view>
                        </view>
                        <text class="search-hot-count">1234543</text>
                    </view> -->
                    <view class="search-hot-item" v-for="(item,index) in searchHot" :key="index" @tap="handleToWord(item.searchWord)">
                        <view class="search-hot-top">
                            {{index+1}}
                        </view>
                        <view class="search-hot-word">
                            <view class="">
                            {{item.searchWord}}<image :src="item.iconUrl" mode="aspectFill"></image>
                            </view>
                            <view>{{item.content}}</view>
                        </view>
                        <text class="search-hot-count">{{item.score}}</text>
                    </view>
                
                </view>
                </block>
                <!-- 搜索结果 -->
                <block v-if="searchType==2">
                    <view class="search-result">
                    <!--    <view class="search-result-item">
                            <view class="search-result-word">
                                <view>少年</view>
                                <view>测试歌曲</view>
                            </view>
                            <text class="iconfont iconbofang"></text>
                        </view> -->
                        <view class="search-result-item" v-for="(item,index) in searchList" :key="index"
                        @tap="handleToDetail(item.id)">
                            <view class="search-result-word">
                                <view>{{item.name}}</view>
                                <view>{{item.artists[0].name}}--{{item.album.name}}</view>
                            </view>
                            <text class="iconfont iconbofang"></text>
                        </view>
                    </view>
                </block>
                <!-- 搜索建议 -->
                <block v-if="searchType==3">
                    <view class="search-suggest">
                        <view class="search-suggest-head">搜索“{{searchWord}}”</view>
                    <!--    <view class="search-suggest-item">
                            <text class="iconfont iconsearch"></text>少年抖音
                        </view> -->
                        <view class="search-suggest-item" v-for="(item,index) in searchSuggest" :key="index" 
                        @tap="handleToWord(item.keyword)">
                            <text class="iconfont iconsearch"></text>{{item.keyword}}
                        </view>
                    
                    </view>
                
                </block>
            </scroll-view>
        </view>
    </view>
</template>
<script>
    import musichead from '../../components/musichead/musichead.vue';
    import {searchHot,searchWord,searchSuggest} from '../../common/api.js'
    export default {
        data() {
            return {
                searchHot:[],
                searchWord:'',
                searchHistory:[],
                searchType:1,
                searchList:[],
                searchSuggest:[],
            }
        },
        components:{
            musichead
        },
        onLoad() {
            searchHot().then((res)=>{
                console.log(res);
                if(res[1].data.code=='200'){
                    this.searchHot=res[1].data.data;
                }
            });
            // 每次加载都要从浏览器中取出值
            uni.getStorage({
                key:'searchHistory',
                success:(res)=> {
                    this.searchHistory=res.data;
                }
            })
        },
        methods: {
            handleToWord(word){
                this.searchWord=word;
                // 触发搜索结果
                this.handleToSearch(word);
            },
            // 将输入字符串存储在历史记录中
            handleToSearch(word){
                console.log(word);
                this.searchHistory.unshift(word);
                // 数组去重，es6写法
                this.searchHistory=[...new Set(this.searchHistory)];
                // 使得数组长度保持在10
                if(this.searchHistory.length>10){
                    this.searchHistory.length=10;
                }
                // 将searchHistory存储在浏览器中
                uni.setStorage({
                    key:'searchHistory',
                    data:this.searchHistory
                });
                // 触发搜索结果
                this.getSearchList(word);
            },
            // 垃圾桶图标的清除
            handleToClear(){
                uni.removeStorage({
                    key:'searchHistory',
                    success: (res) => {
                        this.searchHistory=[];
                    }
                });
            },
            // 获取搜索结果
            getSearchList(word){
                searchWord(word).then((res)=>{
                    if(res[1].data.code=='200'){
                        this.searchList=res[1].data.result.songs;
                        this.searchType=2;
                    }
                    //console.log("this.searchList",this.searchList);
                })
            },
            // 输入框清空
            handleToClose(){
                this.searchWord="";
                this.searchType=1;
                
            },
            // 跳转到歌曲详情页进行播放
            handleToDetail(songId){
                console.log("id",songId);
                uni.navigateTo({
                    url:'/pages/detail/detail?id='+songId
                })
            },
            // 根据输入的值得到搜索建议
            handleToSuggest(ev){
                console.log(ev);
                console.log("测试1",this.searchType);
                // 拿到输入的值
                let value=ev.detail.value;
                if(!value){
                    this.searchType=1;
                    return;
                }
                searchSuggest(value).then((res)=>{
                    if(res[1].data.code=='200'){
                        this.searchSuggest=res[1].data.result.allMatch;
                        this.searchType=3;
                    }
                })
                
            }
        }
    }
</script>
<style scoped>
.search-search{display: flex;align-items: center;height: 70rpx;
margin: 70rpx 30rpx 30rpx 30rpx;
background: #f7f7f7;border-radius: 50rpx;}
.search-search text{margin: 0rpx 26rpx;}
.search-search input{flex: 1;font-size: 26rpx;}
.search-history{margin: 40rpx 30rpx;font-size: 26rpx;}
.search-history-head{display: flex;justify-content: space-between;margin-bottom: 36rpx;}
.search-history-list{display: flex;flex-wrap: wrap;}
.search-history-list view{padding: 16rpx 28rpx;border-radius: 40rpx;margin-right: 30rpx;
margin-bottom: 30rpx;background: #f7f7f7;}
/* 热搜榜 */
.search-hot{margin: 0 30rpx;font-size: 26rpx;}
.search-hot-head{margin-bottom: 36rpx;}
.search-hot-item{display: flex;align-items: center;margin-bottom: 50rpx;}
.search-hot-top{color: #fb2222;width: 60rpx;margin-left: 8rpx;}
.search-hot-word{flex: 1;}
.search-hot-word view:nth-child(1){font-size: 30rpx;color: black;}
.search-hot-word view:nth-child(2){font-size: 20rpx;color: #878787;}
.search-hot-word image{width: 48rpx;height: 22rpx;margin-left: 10rpx;}
/* 搜索结果 */
.search-result{border-top: 2rpx #e4e4e4 solid;padding: 30rpx;}
.search-result-item{display: flex;justify-content: space-between;align-items: center;
padding-bottom: 20rpx;margin-bottom: 30rpx;border-bottom: 2rpx solid #e4e4e4;}
.search-result-word{}
.search-result-word view:nth-child(1){font-size: 28rpx;color: #235790;margin-bottom: 12rpx;}
.search-result-word view:nth-child(2){font-size: 20rpx;color: #898989;}
.search-result-item text{font-size: 50rpx;}
/* 搜索建议 */
.search-suggest{border-top: 2rpx #e4e4e4 solid;padding: 20rpx;font-size: 26rpx;}
.search-suggest-head{color: #4574a5;margin-bottom: 30rpx;}
.search-suggest-item{color: #5d5d5d;margin-bottom:40rpx;}
.search-suggest-item text{color: #bdbdbd;margin-right: 28rpx;position: relative;}
</style>

```

store/index.js:

```js
import Vue from 'vue'
import Vuex from 'vuex'
Vue.use(Vuex);
export default new Vuex.Store({
    state:{
        nextId:'',
        topListIds:[],
    },
    mutations:{
        INIT_TOPLISTDS(state,payload){
            state.topListIds=payload;
        },
        NEXT_ID(state,payload){
            for(var i=0;i<state.topListIds.length;i++){
                if(state.topListIds[i].id==payload){
                    state.nextId=state.topListIds[i+1].id;
                }
            }
        }
    }
})
```

store/index.js:

```js
import Vue from 'vue'
import Vuex from 'vuex'
Vue.use(Vuex);
export default new Vuex.Store({
    state:{
        nextId:'',
        topListIds:[],
    },
    mutations:{
        INIT_TOPLISTDS(state,payload){
            state.topListIds=payload;
        },
        NEXT_ID(state,payload){
            for(var i=0;i<state.topListIds.length;i++){
                if(state.topListIds[i].id==payload){
                    state.nextId=state.topListIds[i+1].id;
                }
            }
        }
    }
})

```

App.vue:

```vue
<script>
    
    export default {
        onLaunch: function() {
            console.log('App Launch')
        },
        onShow: function() {
            console.log('App Show')
        },
        onHide: function() {
            console.log('App Hide')
        }
    }
</script>
<style>
    @import "@/common/iconfont.css";
    /*每个页面公共css */
    .container{width: 100%;height: calc(100vh - 70px);overflow: auto;}
    .container scroll-view{height: 100%;}
    .fixbg{
        /* 背景毛玻璃片效果 */
        width: 100%;height: 100vh;
        position: fixed;
        left: 0;top: 0;
        background-image: url(static/logo.png);
        background-size: cover;
        background-position: center 0;
        filter: blur(20rpx);
    }
</style>
```

main.js:

```js

import App from './App'
// 引用store
import store from 'store/index.js'
// #ifndef VUE3
import Vue from 'vue'
Vue.config.productionTip = false
App.mpType = 'app'
const app = new Vue({
    ...App,
    store
})
// 过滤数
Vue.filter('formatCount',function(value){
    if(value>=10000&&value<=100000000)
    {
        value/=10000;
        return value.toFixed(1)+'万';
    }else if(value>100000000){
        value/=100000000;
        return value.toFixed(1)+'亿';
    }else{
        return value;
    }
})
// 过滤时间戳
Vue.filter('formatTime',function(value){
    var date=new Date(value);
    return date.getFullYear()+'年'+(date.getMonth()+1)+'月'+date.getDate()+'日';
})
app.$mount()
// #endif
// #ifdef VUE3
import { createSSRApp } from 'vue'
// 全局引入iconfont
import iconfont from '@/common/iconfont.css';
export function createApp() {
  const app = createSSRApp(App)
  return {
    app
  }
}
// #endif
```

最后，代码仓库地址为：

https://gitee.com/ccqq0625/netease-cloud-music-api.git



