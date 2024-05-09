---
title: 在一个画布内画出多个echarts图表
date: 2024-05-09 14:11:43
updated: 2024-05-09 14:11:43
excerpt: 使用同一个id（同一个画布）渲染出两个echarts图表
categories:
  - 需求池
tags:
  - Echarts
  - 折线图
---

# 使用一个div渲染多个echarts图

## 1.需求描述

对于一个普通的echart图表，一般是一个div id渲染一个图表，每个图表在渲染上是独立的，一个div就代表一个canvas画布。但是如果需要使用一个div id 渲染多个图表（在一个画布上），就需要使用`grid`配置项分别对多个图表进行位置的配置。

## 2.效果

![效果图](/img/在一个画布内画出多个echarts图表/效果图1.png)

![效果图](/img/在一个画布内画出多个echarts图表/效果图2.png)

## 3.实现

```js

  // 基于准备好的dom，初始化echarts实例
	//只使用一个
  var chart = echarts.init(document.getElementById("lineChart"))

  var option
  option = {
    grid: [
         // 调整每个图表的位置
      {
       //左边图表的位置
        left: "10%",
        right: "60%"
      },
      {
        //右边图表的位置
        left: "50%",
        right: "20%"
      }
    ],
    dataZoom: [
      {
        type: "inside",
        filterMode: "none"
      },
      {
        type: "inside",
        yAxisIndex: 1,//缩放单独控制
        xAxisIndex: 1,
        filterMode: "none"
      }
    ],
    legend: {
      type: "scroll", // ：可滚动翻页的图例。当图例数量较多时可以使用。
      orient: "vertical",
      x: "right",
      //可以同时控制多个图表中有相同series的name的折线的显示与隐藏
      data: ["2024-5-9 ZQ01", "2024-5-9 ZQ02", "2024-5-9 ZQ03"]
    },
    tooltip: {
      show: true,
    },
    xAxis: [
      {
        type: "value",
        name: "第一个X轴",
        nameLocation: "middle", // x轴name处于x轴的什么位置
        nameGap: 25, // x轴name与横坐标轴线的间距
        axisLabel: {
          show: true
        },
        splitLine: {
          show: true
        },
        axisTick: {
          show: true
        },
        axisLine: { show: true }
      },
      {
        type: "value",
        name: "第二个X轴",
        nameLocation: "middle", // x轴name处于x轴的什么位置
        nameGap: 25, // x轴name与横坐标轴线的间距
        axisLabel: {
          show: true
        },
        splitLine: {
          show: true
        },
        axisTick: {
          show: true
        },
        axisLine: { show: true },
        gridIndex: 1
      }
    ],
    yAxis: [
      {
        type: "category",
        name: "深度(m)",
        inverse: true,
        nameGap: 25,
        nameLocation: "middle",
        axisLine: { onZero: true },
        splitLine: {
          show: true
        },
        axisLabel: {
          show: true
        },
        boundaryGap: true,
        axisTick: {
          show: true
        },
        data: [1, 2, 3, 4, 5]
      },
      {
        type: "category",
        name: "深度(m)",
        inverse: true,
        nameGap: 25,
        nameLocation: "middle",
        axisLine: { onZero: true },
        splitLine: {
          show: true
        },
        axisLabel: {
          show: true
        },
        boundaryGap: true,
        axisTick: {
          show: true
        },
        data: [6, 5, 3, 2, 4],
        gridIndex: 1
      }
    ],
    series: [
      {
        name: "2024-5-9 ZQ01",
        type: "line",
        symbol: "circle",
        smooth: true,
        symbolSize: 8,
        showAllSymbol: true, //标注所有数据点
        lineStyle: {
          width: 2,
          symbolSize: 5
        },
        emphasis: {
          lineStyle: {
            width: 3 // hover时的折线宽度
          },
          itemStyle: {
            shadowBlur: 10, // 阴影的模糊大小
            shadowColor: "rgba(0, 0, 0, 0.5)", // 阴影颜色为半透明的黑色
            shadowOffsetX: 0, // 阴影的水平偏移量
            shadowOffsetY: 0 // 阴影的垂直偏移量
          }
        },
        data: [6, 7, 8, 9, 10]
      },
      {
        name: "2024-5-9 ZQ02",
        type: "line",
        symbol: "circle",
        smooth: true,
        symbolSize: 8,
        showAllSymbol: true, //标注所有数据点
        lineStyle: {
          width: 2,
          symbolSize: 5
        },
        emphasis: {
          lineStyle: {
            width: 3 // hover时的折线宽度
          },
          itemStyle: {
            shadowBlur: 10, // 阴影的模糊大小
            shadowColor: "rgba(0, 0, 0, 0.5)", // 阴影颜色为半透明的黑色
            shadowOffsetX: 0, // 阴影的水平偏移量
            shadowOffsetY: 0 // 阴影的垂直偏移量
          }
        },
        data: [6, 0, 11, 9, 10]
      },
      {
        name: "2024-5-9 ZQ01",
        type: "line",
        symbol: "circle",
        smooth: true,
        symbolSize: 8,
        showAllSymbol: true, //标注所有数据点
        lineStyle: {
          width: 2,
          symbolSize: 5
        },
        emphasis: {
          lineStyle: {
            width: 3 // hover时的折线宽度
          },
          itemStyle: {
            shadowBlur: 10, // 阴影的模糊大小
            shadowColor: "rgba(0, 0, 0, 0.5)", // 阴影颜色为半透明的黑色
            shadowOffsetX: 0, // 阴影的水平偏移量
            shadowOffsetY: 0 // 阴影的垂直偏移量
          }
        },
        data: [9, 0, 5, 3, 5],
        xAxisIndex: 1,
        yAxisIndex: 1
      },
      {
        name: "2024-5-9 ZQ02",
        type: "line",
        symbol: "circle",
        smooth: true,
        symbolSize: 8,
        showAllSymbol: true, //标注所有数据点
        lineStyle: {
          width: 2,
          symbolSize: 5
        },
        emphasis: {
          lineStyle: {
            width: 3 // hover时的折线宽度
          },
          itemStyle: {
            shadowBlur: 10, // 阴影的模糊大小
            shadowColor: "rgba(0, 0, 0, 0.5)", // 阴影颜色为半透明的黑色
            shadowOffsetX: 0, // 阴影的水平偏移量
            shadowOffsetY: 0 // 阴影的垂直偏移量
          }
        },
        data: [6, 2, 1, 3, 5],
        xAxisIndex: 1,
        yAxisIndex: 1
      }
    ]
  }

  chart.setOption(option, true)
  window.addEventListener("resize", () => {
    chart.resize()
  })
```

