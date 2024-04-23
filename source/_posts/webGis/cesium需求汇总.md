---
title: cesium笔记
excerpt: cesium需求笔记
categories:
  - cesiumJs
tags:
  - Cesium
math: true
date: 2024-4-23 10:23:00
---

## 一.cesium初始化

可以选择在官方github代码库中直接下载最新的release版的代码，但是由于github访问可能不稳定，所以也可以选择通过其他途径获取一个示例代码。

```
国内Cesium历史版本快速下载：(只需要下载并使用最新版就行)
链接：https://pan.baidu.com/s/1VG_lyy76xywOLyoq235JQA 提取码：bren

Github下载地址[缓慢]：
https://github.com/CesiumGS/cesium/releases
```

获取到最新代码的压缩包之后，解压就可以得到一个这样结构的项目了：

![](https://secure2.wostatic.cn/static/s7Sy5pritZ971FcXBLYrxA/image.png?auth_key=1713839336-jVCNtkCLRd4KemU5hBhyB1-0-036a6f79557a5ddc5c3ee5f9341418ca&file_size=57440)

在项目根目录下运行`npm i`下载依赖

如果出现了node_modules文件夹，则说明下载成功。

运行 `npm start` 或 `npm server.js`来执行程序

如果出现了类似于 **This process does not have permission to listen on port 8080 **的报错信息，则多半是由于端口出错，在server.js中修改默认端口为其他端口就可以解决了。

出现这样的本地地址，则说明运行成功：

![运行成功](https://secure2.wostatic.cn/static/mJJHT2J5jisKE6gYS8hqy8/image.png?auth_key=1713839418-qJTEBHzJx97uWhTmof17bg-0-5837e62ebccea79cc9a6980046b5d2a7&file_size=2768)

通过该地址就可以访问一个cesium的基础程序了，效果如下：

![cesium基础效果图](https://secure2.wostatic.cn/static/cRoKphrx9nE4qE5JVUmKb6/image.png?auth_key=1713839483-rKrF2BUr7rBAb31cgwaNMp-0-42c6c6fd4cf17b4d731ccbad0554bae0&file_size=83703)

点进去之后，会出现中心的3D地图无法显示的问题：

![3D地图不显示](https://secure2.wostatic.cn/static/hpA7s7oyQS81f25eVNhknY/image.png?auth_key=1713839540-uvKdRbcTEr8DSK27bykib7-0-b5344f24246d2df10ec6edb4d93fcb5c&file_size=1082293)

这是因为示例程序中的token key过期或失效了，需要自行到官网再注册一个key值并替换就好了。

官网  https://ion.cesium.com/  注册一个账号，然后在此就可以获得一个有效的key值：

![官网申请key](https://secure2.wostatic.cn/static/2kVzmAVvj4uzYMHcU1Qrh4/image.png?auth_key=1713839607-v5ynqxno977cyXbdryyaou-0-059dd59267d389890668103bb982b26e&file_size=72306)

将获取到的新tokens值替换Source\Core\Ion.js中的默认defaultAccessToken就行。

![替换默认的AccessToken](https://secure2.wostatic.cn/static/rvgVAY41RMDPjsXxNUKTo6/image.png?auth_key=1713839642-ja5sGFR3pQP9XzMAcF997n-0-cd1f7776c2f3f9249863212c0e5cae1d&file_size=190583)

重新运行之后，可以发现3D地图正常显示了：

![正常显示](https://secure2.wostatic.cn/static/3ehBk7xHh43RTZ6Qx5k4UL/image.png?auth_key=1713839697-4akotmaGAmPUBMAqALmtmU-0-67c15514c8539d8868122b18a524a63f&file_size=1383459)

## 二.自定义全屏显示

### 1.效果

<video src="https://secure2.wostatic.cn/static/npzZHTJnKqHWjjhGYqiGHX/QQ2024423-10443.mp4?auth_key=1713840291-mLiL31yDQa3w8jj4fcKffF-0-f492efe79e63918028c660510bbd6491&file_size=1587389" style='width:900px;height:417px'></video>

在cesium视图上添加一个全屏显示样式的按钮，再给其绑定全屏显示的方法。

### 2.实现

#### HTML部分：

```vue

<div class="home" style="position: relative">
  <div class="imgSample">
    <!-- 实现全屏显示 -->
      <el-button
        icon="FullScreen"
        id="FullScreen"
        size="small"
        circle
        @click="changeFullScreen()"
      />
  </div>
    <!-- cesium主图渲染区 -->
    <div class="container" id="container"></div>
  </div>

  <style scoped lang="scss">
#container {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  overflow: hidden;
}

.home {
  height: 90vh;
  .imgSample {
    position: absolute;
    left: 10px;
    top: 10px;
    z-index: 1;
    .content {
      text-align: center;
    }
  }
  .latlng_show {
    position: absolute;
    right: 0;
    bottom: 10px;
    z-index: 1;
    width: 300px;
    height: 20px;
    display: none;
  }
  .earth {
    position: absolute;
    left: 10px;
    top: 10px;
  }
}

</style>
```

#### JS部分：

```js
 const viewer = new Cesium.Viewer("container");//渲染cesium视图
 //实现全屏功能的方法
 function changeFullScreen() {
 //先判断当前是否有全屏的元素（兼容各个浏览器版本的内核）
  if (
    !document.fullscreenElement && 
    !document.mozFullScreenElement &&
    !document.webkitFullscreenElement &&
    !document.msFullscreenElement
  ) {
    //将指定元素全屏，也就是我们当前渲染cesium视图得到的viewer
    if (viewer.container.requestFullscreen) {
      viewer.container.requestFullscreen()
    } else if (viewer.container.msRequestFullscreen) {
      viewer.container.msRequestFullscreen()
    } else if (viewer.container.mozRequestFullScreen) {
      viewer.container.mozRequestFullScreen()
    } else if (viewer.container.webkitRequestFullscreen) {
      viewer.container.webkitRequestFullscreen(Element.ALLOW_KEYBOARD_INPUT)
    }
  } else {//如果存在全屏的元素，则退出当前全屏
    if (document.exitFullscreen) {
      document.exitFullscreen()
    } else if (document.msExitFullscreen) {
      document.msExitFullscreen()
    } else if (document.mozCancelFullScreen) {
      document.mozCancelFullScreen()
    } else if (document.webkitExitFullscreen) {
      document.webkitExitFullscreen()
    }
  }
}
```

## 三.打点

### 1.效果

![打点效果](https://secure2.wostatic.cn/static/nY1ddTy9XzkXos7DYtTBmi/image.png?auth_key=1713840605-sK5Kwp36E6mYpVeBYuWEF8-0-acd02c2cb3377c6a5136a8b2e41378de&file_size=2453277)

### 2.实现

#### HTML部分

```html
 <div class="container" id="container"></div>
```

#### JS部分

```js
//初始化渲染cesium视图
 const viewer = new Cesium.Viewer("container");//渲染cesium视图
 const pointsData=[
   //一个点：经度longitude和维度latitude是必传的，但是高度height是非必有的
   {name:"点01",longitude:118.6357,latitude:24.9019,height:60},
    {name:"点02",longitude:109.1074,latitude:34.237,height:60}
    //更多的点位
 ];
  pointsData.forEach((point) => {
    // console.log("单个点位", point)
    const entity = new Cesium.Entity({
      position: Cesium.Cartesian3.fromDegrees(
        Number(point.longitude),
        Number(point.latitude),
        Number(point.height)
      ),
      billboard: {
        image: '自定义图标的路径' // 自定义图标的 URL，例如"/map/测斜仪 (green).png",
        scale: 0.15 // 图标缩放比例
      },
      label: new Cesium.LbelGraphics({//图标下的label
        text: point.name,
        scale: 0.5,
        pixelOffset: new Cesium.Cartesian3(0, 35), // 调整文本位置偏移
        horizontalOrigin: Cesium.HorizontalOrigin.CENTER,
        verticalOrigin: Cesium.VerticalOrigin.BOTTOM,
        fillColor: Cesium.Color.WHITE,
        outlineColor: Cesium.Color.BLACK,
        outlineWidth: 1.0,
        style: Cesium.LabelStyle.FILL_AND_OUTLINE
      }),
      info: {//自定义点的一些信息，可以不叫info
        name: point.name,
        longitude: point.longitude,
        latitude: point.latitude,
      },
    })
    viewer.entities.add(entity);
 }
```

## 四.指南针组件

### 1.效果

![img](https://secure2.wostatic.cn/static/4YJvpGVrVc7dX186o91Rse/image.png?auth_key=1713840661-3riZHD3BGVEZDottaCjKex-0-30ca1a1661d898f3a65b457af39dec60)

### 2.实现

#### html部分

```HTML
  <div class="container" id="container"></div>
```

#### js部分

```JavaScript
 import * as Cesium from "cesium";
import CesiumNavigation from "cesium-navigation-es6";//导航组件

 const viewer = new Cesium.Viewer(documentId);
  // 地图指南针小组件
function navigation() {
        const options = {};
        // 用于在使用重置导航重置地图视图时设置默认视图控制。接受的值是Cesium.Cartographic 和Cesium.Rectangle.
        options.defaultResetView = Cesium.Cartographic.fromDegrees(110, 30, 2000000);
        // 用于启用或禁用罗盘。true是启用罗盘，false是禁用罗盘。默认值为true。如果将选项设置为false，则罗盘将不会添加到地图中。
        options.enableCompass = true;
        // 用于启用或禁用缩放控件。true是启用，false是禁用。默认值为true。如果将选项设置为false，则缩放控件 将不会添加到地图中。
        options.enableZoomControls = true;
        // 用于启用或禁用距离图例。true是启用，false是禁用。默认值为true。如果将选项设置为false，距离图例将不会添加到地图中。
        options.enableDistanceLegend = true;
        // 用于启用或禁用指南针外环。true是启用，false是禁用。默认值为true。如果将选项设置为false，则该环将可见但无效。
        options.enableCompassOuterRing = true;
        new CesiumNavigation(viewer, options);
```

## 五.实时获取鼠标移动的经度、维度和高度

### 1.效果

![img](https://secure2.wostatic.cn/static/gTBe8VSLqDXm8Px7Y16FL7/image.png?auth_key=1713840747-9zKinZk9AsJXsdBrafg2Zd-0-38f8c1343baedbb268bc23c6e94af987)

根据鼠标移入的位置，实时动态的获取当前鼠标指向的经纬度和高度

### 1.实现

#### html部分

```Vue
<template>
  <div class="container" id="container"></div>
</template>
<script setup>
import { onMounted } from "vue"
import CesiumTools from "@/utils/cesiumTools"
let cesiumTools = new CesiumTools() //一个实例对象

onMounted(() => {
  cesiumTools.init("container")
})
</script>
<style scoped>
.container {
  width: 99vw;
  height: 95vh;
  margin: 0;
  padding: 0;
  overflow: hidden;
}
</style>
```

#### js

```JavaScript
import * as Cesium from "cesium";
import CesiumNavigation from "cesium-navigation-es6";//导航组件



class CesiumTools {
    init(documentId) {
        //初始化
        Cesium.Ion.defaultAccessToken =
            "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiIzYTBjZGFlOS01YWYzLTRkNTQtODNmYS1lMDNlODU4ZTU4N2EiLCJpZCI6MTAyNDA5LCJpYXQiOjE2NTg3MzM3NTB9.KlBMyEsHLQcZkNqlbMTj5PzQtW_10rbJ_9kkD20duuE"

        this.viewer = new Cesium.Viewer(documentId);
        this.navigation()
        this.moveDegress()
    }

    // 地图指南针小组件
    navigation() {
        const options = {};
        // 用于在使用重置导航重置地图视图时设置默认视图控制。接受的值是Cesium.Cartographic 和Cesium.Rectangle.
        options.defaultResetView = Cesium.Cartographic.fromDegrees(110, 30, 2000000);
        // 用于启用或禁用罗盘。true是启用罗盘，false是禁用罗盘。默认值为true。如果将选项设置为false，则罗盘将不会添加到地图中。
        options.enableCompass = true;
        // 用于启用或禁用缩放控件。true是启用，false是禁用。默认值为true。如果将选项设置为false，则缩放控件 将不会添加到地图中。
        options.enableZoomControls = true;
        // 用于启用或禁用距离图例。true是启用，false是禁用。默认值为true。如果将选项设置为false，距离图例将不会添加到地图中。
        options.enableDistanceLegend = true;
        // 用于启用或禁用指南针外环。true是启用，false是禁用。默认值为true。如果将选项设置为false，则该环将可见但无效。
        options.enableCompassOuterRing = true;
        new CesiumNavigation(this.viewer, options);
    }
    // 鼠标移入获得实时经纬度
    moveDegress() {
        const viewer = this.viewer
        const canvas = viewer.scene.canvas
        const ellipsoid = viewer.scene.globe.ellipsoid
        const handler = new Cesium.ScreenSpaceEventHandler(canvas)
        handler.setInputAction(function (movement) {
            const cartesian = viewer.camera.pickEllipsoid(movement.endPosition, ellipsoid)
            if (cartesian) {
                const cartographic = viewer.scene.globe.ellipsoid.cartesianToCartographic(cartesian) //将地图坐标（弧度）转为十进制的度数
                const long_String = Cesium.Math.toDegrees(cartographic.longitude).toFixed(4) //经
                const lat_String = Cesium.Math.toDegrees(cartographic.latitude).toFixed(4) // 纬

                const alti_String = (viewer.camera.positionCartographic.height / 1000).toFixed(2) //高
                //打印结果
                console.log("经度", long_String, "纬度", lat_String, "高程", alti_String);
            }


        }, Cesium.ScreenSpaceEventType.MOUSE_MOVE)
    }
}

export default CesiumTools;
```

## 六.在地图上自定义某个地方显示实时经纬度和高度

### 1.效果

![img](https://secure2.wostatic.cn/static/kdT12ztmLJEzuE8jgoTaAz/image.png?auth_key=1713840747-kb6YMVKH2jPV2M8cfRG3bo-0-3b1a33d4753ae8ecbcf0b33085cd0a95)

### 2.实现

#### html部分

先自定义一个用于显示经度，纬度和高度的div，并确定其样式和位置

```Vue
<template>
  <div class="home" style="position: relative">
    <!-- cesium 容器 -->
    <div class="container" id="container"></div>
    <!-- 经纬度和视角 -->
    <div id="latlng_show" class="latlng_show">
      <div style="float: left">
        <span size="1" color="white"
          >经度：<span id="longitude_show"></span
        ></span>
        &nbsp;&nbsp;
      </div>
      <div style="float: left">
        <span size="1" color="white"
          >纬度：<span id="latitude_show"></span
        ></span>
        &nbsp;&nbsp;
      </div>
      <div style="float: left">
        <span size="1" color="white"
          >视角高：<span id="altitude_show"></span>km</span
        >
      </div>
    </div>
  </div>
</template>
<script setup>
import { onMounted } from "vue"
import CesiumTools from "@/utils/cesiumTools"
let cesiumTools = new CesiumTools() //一个实例对象
//给经纬度高度赋值
function handleShowLongAndLat(option) {
  // console.log("经纬度", option)
  if (option) {
    document.getElementById("latlng_show").style = "display: block"
    document.getElementById("longitude_show").innerHTML = option.longitude
    document.getElementById("latitude_show").innerHTML = option.latitude
    document.getElementById("altitude_show").innerHTML = option.altitude
  } else {
    document.getElementById("latlng_show").style = "display:none"
  }
}
onMounted(() => {
  cesiumTools.init("container")
  cesiumTools.moveDegress(handleShowLongAndLat)
})
</script>
<style scoped lang="scss">
.home {
  .container {
    width: 99vw;
    height: 95vh;
    margin: 0;
    padding: 0;
    overflow: hidden;
  }

  .latlng_show {
    position: absolute;
    right: 10px;
    bottom: 10px;
    z-index: 1;
    width: 500px;
    height: 20px;
    display: none;
    span {
      color: white;
    }
  }
}
</style>
```

#### js部分

```JavaScript
import * as Cesium from "cesium";
import CesiumNavigation from "cesium-navigation-es6";//导航组件

class CesiumTools {
    init(documentId) {
        //初始化
        Cesium.Ion.defaultAccessToken =
            "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiIzYTBjZGFlOS01YWYzLTRkNTQtODNmYS1lMDNlODU4ZTU4N2EiLCJpZCI6MTAyNDA5LCJpYXQiOjE2NTg3MzM3NTB9.KlBMyEsHLQcZkNqlbMTj5PzQtW_10rbJ_9kkD20duuE"

        this.viewer = new Cesium.Viewer(documentId, {
            //地形图层TerrainProvider
            // terrainProvider: Cesium.createWorldTerrain({
            //     requestWaterMask: true, //水面特效
            //     requestVertexNormals: true // 地形光照
            // }),
            // 图层控件显隐控制
            timeline: false, //隐藏时间轴
            animation: false, //隐藏动画控制器
            geocoder: true, //隐藏地名查找控制器
            homeButton: true, //隐藏Home按钮
            // terrainProviderViewModels: [], // 设置地形
            sceneModePicker: true, //场景模式，切换2D、3D 和 Columbus View (CV) 模式
            baseLayerPicker: true, //隐藏图层选择控制器
            navigationHelpButton: false, //隐藏帮助按钮
            fullscreenButton: false //隐藏全屏按钮
        });
        this.navigation()
    }

    // 地图指南针小组件
    navigation() {
        const options = {};
        // 用于在使用重置导航重置地图视图时设置默认视图控制。接受的值是Cesium.Cartographic 和Cesium.Rectangle.
        options.defaultResetView = Cesium.Cartographic.fromDegrees(110, 30, 2000000);
        // 用于启用或禁用罗盘。true是启用罗盘，false是禁用罗盘。默认值为true。如果将选项设置为false，则罗盘将不会添加到地图中。
        options.enableCompass = true;
        // 用于启用或禁用缩放控件。true是启用，false是禁用。默认值为true。如果将选项设置为false，则缩放控件 将不会添加到地图中。
        options.enableZoomControls = true;
        // 用于启用或禁用距离图例。true是启用，false是禁用。默认值为true。如果将选项设置为false，距离图例将不会添加到地图中。
        options.enableDistanceLegend = true;
        // 用于启用或禁用指南针外环。true是启用，false是禁用。默认值为true。如果将选项设置为false，则该环将可见但无效。
        options.enableCompassOuterRing = true;
        new CesiumNavigation(this.viewer, options);
    }
    /**
   * 监听鼠标移动，事件回调用于在地图上显示经纬度
   * @param {*} callback 
   */
    // 鼠标移入获得实时经纬度
    moveDegress(callback) {
        const viewer = this.viewer
        const canvas = viewer.scene.canvas
        const ellipsoid = viewer.scene.globe.ellipsoid
        const handler = new Cesium.ScreenSpaceEventHandler(canvas)
        handler.setInputAction(function (movement) {
            const cartesian = viewer.camera.pickEllipsoid(movement.endPosition, ellipsoid)
            if (cartesian) {
                const cartographic = viewer.scene.globe.ellipsoid.cartesianToCartographic(cartesian) //将地图坐标（弧度）转为十进制的度数
                const long_String = Cesium.Math.toDegrees(cartographic.longitude).toFixed(4) //经
                const lat_String = Cesium.Math.toDegrees(cartographic.latitude).toFixed(4) // 纬
                const alti_String = (viewer.camera.positionCartographic.height / 1000).toFixed(2) //高
                // console.log("经度", long_String, "纬度", lat_String, "高程", alti_String);
                callback({ longitude: long_String, latitude: lat_String, altitude: alti_String })
            } else {
                callback()
            }
        }, Cesium.ScreenSpaceEventType.MOUSE_MOVE)
    }
}

export default CesiumTools;
```

## 七.处理并加载tif影像瓦片地图服务

对于一个tif为后缀的影像文件，在渲染开始之前需要将该文件进行切片

例如一个这样的文件：

![img](https://secure2.wostatic.cn/static/iMD7iK8DkYtQxZ7azkTbex/image.png?auth_key=1713840922-5MNyfumnsQrCeHrU6JgVXs-0-dd6aef83718e20f6d87749d612f18d71)

### 1.使用cesiumLab进行切片（账号注册登录部分省略）

![img](https://secure2.wostatic.cn/static/oWoi5jkwW1bEs5XDDmddLX/9ab64310c012924549763ed26ceceb9b.png?auth_key=1713840922-q7BfvcCz5y6jXhGDXUbs3K-0-89ff283058674ef4675a1b3f68f8ec2c)

选择一个切片的输出路径之后，等待切片完成

![img](https://secure2.wostatic.cn/static/gXHDYFUf1EZVLXVcGs8ur9/image.png?auth_key=1713840922-qFKvx473MABrFNrWGqzuBw-0-92c3874abaa03c1718446f6b15265417)

切片完成之后，可以预览渲染之后的效果

![img](https://secure2.wostatic.cn/static/phsS53VuqsdsosH48eUcbt/image.png?auth_key=1713840922-udqVqMrAf74PV47rgNZKim-0-0fc17572e4e762de2b4a948b78eaa67c)

类似这样：

![img](https://secure2.wostatic.cn/static/8sqArghVe1HsJjYFZo8TDL/image.png?auth_key=1713840922-hmFG6Yi5zfaX1EFPvAwiQQ-0-5ffb97a340fef78cea6593f34163dcd2)

根据切片导出的文件路径，可以获得本地的切片结果：

![img](https://secure2.wostatic.cn/static/gJs6T1APKjtLbJUnkJpCsj/image.png?auth_key=1713840922-m6J4jECJDQryQmrTGWTRYh-0-b4e2400b3830581fb95aa4ab17fb42d3)

### 2.切片完成后，在项目中渲染影像切片

html部分

```Vue
<template>
  <div class="home" style="position: relative">
    <!-- cesium 容器 -->
    <div class="container" id="container"></div>
    <!-- 经纬度和视角 -->
    <div id="latlng_show" class="latlng_show">
      <div style="float: left">
        <span size="1" color="white"
          >经度：<span id="longitude_show"></span
        ></span>
        &nbsp;&nbsp;
      </div>
      <div style="float: left">
        <span size="1" color="white"
          >纬度：<span id="latitude_show"></span
        ></span>
        &nbsp;&nbsp;
      </div>
      <div style="float: left">
        <span size="1" color="white"
          >视角高：<span id="altitude_show"></span>km</span
        >
      </div>
    </div>
  </div>
</template>
<script setup>
import { onMounted } from "vue"
import CesiumTools from "@/utils/cesiumTools"
let cesiumTools = new CesiumTools() //一个实例对象
//给经纬度高度赋值
function handleShowLongAndLat(option) {
  // console.log("经纬度", option)
  if (option) {
    document.getElementById("latlng_show").style = "display: block"
    document.getElementById("longitude_show").innerHTML = option.longitude
    document.getElementById("latitude_show").innerHTML = option.latitude
    document.getElementById("altitude_show").innerHTML = option.altitude
  } else {
    document.getElementById("latlng_show").style = "display:none"
  }
}
onMounted(() => {
  cesiumTools.init("container")
  cesiumTools.moveDegress(handleShowLongAndLat)
  //将影像切片的本地文件放在项目下相关位置
  //渲染服务器中的切片文件同理
  //根据切片方式的不同有时候写法不同
**  //  /.../{z}/{x}/{reverseY}.png
  // /.../{z}/{x}/{y}.png**
  cesiumTools.loadImagery("/test/{z}/{x}/{reverseY}.png")
})
</script>
<style scoped lang="scss">
.home {
  .container {
    width: 99vw;
    height: 95vh;
    margin: 0;
    padding: 0;
    overflow: hidden;
  }

  .latlng_show {
    position: absolute;
    right: 10px;
    bottom: 10px;
    z-index: 1;
    width: 500px;
    height: 20px;
    display: none;
    span {
      color: white;
    }
  }
}
</style>
```

js部分

```JavaScript
import * as Cesium from "cesium";
import CesiumNavigation from "cesium-navigation-es6";//导航组件

class CesiumTools {
    init(documentId) {
        //初始化
        Cesium.Ion.defaultAccessToken =
            "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiIzYTBjZGFlOS01YWYzLTRkNTQtODNmYS1lMDNlODU4ZTU4N2EiLCJpZCI6MTAyNDA5LCJpYXQiOjE2NTg3MzM3NTB9.KlBMyEsHLQcZkNqlbMTj5PzQtW_10rbJ_9kkD20duuE"

        this.viewer = new Cesium.Viewer(documentId, {
            //地形图层TerrainProvider
            // terrainProvider: Cesium.createWorldTerrain({
            //     requestWaterMask: true, //水面特效
            //     requestVertexNormals: true // 地形光照
            // }),
            // 图层控件显隐控制
            timeline: false, //隐藏时间轴
            animation: false, //隐藏动画控制器
            geocoder: true, //隐藏地名查找控制器
            homeButton: true, //隐藏Home按钮
            // terrainProviderViewModels: [], // 设置地形
            sceneModePicker: true, //场景模式，切换2D、3D 和 Columbus View (CV) 模式
            baseLayerPicker: true, //隐藏图层选择控制器
            navigationHelpButton: false, //隐藏帮助按钮
            fullscreenButton: false //隐藏全屏按钮
        });
        // this.navigation()

    }

    // 地图指南针小组件
    navigation() {
        const options = {};
        // 用于在使用重置导航重置地图视图时设置默认视图控制。接受的值是Cesium.Cartographic 和Cesium.Rectangle.
        options.defaultResetView = Cesium.Cartographic.fromDegrees(110, 30, 2000000);
        // 用于启用或禁用罗盘。true是启用罗盘，false是禁用罗盘。默认值为true。如果将选项设置为false，则罗盘将不会添加到地图中。
        options.enableCompass = true;
        // 用于启用或禁用缩放控件。true是启用，false是禁用。默认值为true。如果将选项设置为false，则缩放控件 将不会添加到地图中。
        options.enableZoomControls = true;
        // 用于启用或禁用距离图例。true是启用，false是禁用。默认值为true。如果将选项设置为false，距离图例将不会添加到地图中。
        options.enableDistanceLegend = true;
        // 用于启用或禁用指南针外环。true是启用，false是禁用。默认值为true。如果将选项设置为false，则该环将可见但无效。
        options.enableCompassOuterRing = true;
        new CesiumNavigation(this.viewer, options);
    }
    /**
   * 监听鼠标移动，事件回调用于在地图上显示经纬度
   * @param {*} callback 
   */
    // 鼠标移入获得实时经纬度
    moveDegress(callback) {
        const viewer = this.viewer
        const canvas = viewer.scene.canvas
        const ellipsoid = viewer.scene.globe.ellipsoid
        const handler = new Cesium.ScreenSpaceEventHandler(canvas)
        handler.setInputAction(function (movement) {
            const cartesian = viewer.camera.pickEllipsoid(movement.endPosition, ellipsoid)
            if (cartesian) {
                const cartographic = viewer.scene.globe.ellipsoid.cartesianToCartographic(cartesian) //将地图坐标（弧度）转为十进制的度数
                const long_String = Cesium.Math.toDegrees(cartographic.longitude).toFixed(4) //经
                const lat_String = Cesium.Math.toDegrees(cartographic.latitude).toFixed(4) // 纬

                const alti_String = (viewer.camera.positionCartographic.height / 1000).toFixed(2) //高
                // console.log("经度", long_String, "纬度", lat_String, "高程", alti_String);
                callback({ longitude: long_String, latitude: lat_String, altitude: alti_String })
            } else {
                callback()
            }


        }, Cesium.ScreenSpaceEventType.MOUSE_MOVE)
    }
    // 加载影像切片
    loadImagery(url) {
        this.viewer.imageryLayers.addImageryProvider(
            new Cesium.UrlTemplateImageryProvider({
                url: url,
                minimumLevel: 0,
                maximumLevel: 18
            })
        )
    }

}

export default CesiumTools;
```

### 3.效果

最后发现在项目中渲染得到的效果与cesiumLab中的效果相同

![img](https://secure2.wostatic.cn/static/unb9pJ1FH7j9DbnoUmEKwW/image.png?auth_key=1713840922-m7apkwxANhorw94uzfQNEd-0-f2c810ba8123b853caf408f2dd1468ca)