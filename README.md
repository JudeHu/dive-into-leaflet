# dive-into-leaflet
leaflet源码剖析，介绍leaflet实现原理和webgis基础知识，并对具体代码进行剖析。   

> 使用leaflet开发web地图已经有近两年的时间了，是时候该总结沉淀一下了，也是给后来者分享自身在开发和学习过程中积累的经验和知识。目前国内详细介绍leaflet的博客或书籍比较少，开发者往往也只是参考官方的api文档，对其具体实现大多数都是一些零星的说明和讨论，因此撰写本书主要目的是为了让大家了解对leaflet进一步深入的认识，了解leaflet的实现原理，便于更好的进行功能拓展和插件二次开发等。

>本书的主要是搜集整理现有知识和结合自身理解进行阐述，文中部分内容是直接摘自互联网（会有相关引用说明），如涉及版权问题请与我联系

不一定是逐行去读代码，更多的是讲实现的原理，并给出一两个源码的例子来说明实现过程。

##### leafet介绍
参见百度百科：   
>Leaflet 是一个为建设移动设备友好的互动地图，而开发的现代的、开源的 JavaScript 库。它是由 Vladimir Agafonkin 带领一个专业贡献者团队开发，虽然代码仅有 33 KB，但它具有开发人员开发在线地图的大部分功能。Leaflet设计坚持简便、高性能和可用性好的思想，在所有主要桌面和移动平台能高效运作，在现代浏览器上会利用HTML5和CSS3的优势，同时也支持旧的浏览器访问。支持插件扩展，有一个友好、易于使用的API文档和一个简单的、可读的源代码。 

Leaflet是空间数据可视化的“佼佼者”，也是商用地图Mapbox.js的“父亲”，由于其小巧轻便、简单易用、开源，生态好，插件多等特点，迅速赢得开发者的青睐，占领webgis的开发市场，甚至与老大哥openlayers并驾齐驱。   

尽管leaflet在大数据性能和3D效果方面有所欠缺，但在一般的空间数据可视化项目应用方面有着巨大的优势。


## 本书目录结构

- ### leaflet基本功能介绍
- ### webgis基础知识
  - 地理坐标与投影坐标
  - 投影坐标系crs
  - ogc
  - 栅格切片与矢量切片
- ### JavaScript基础知识
  - 原型与类
  - dom事件绑定
  - 绘制与动画
- ### leaflet的基本实现原理
  - leaflet基本概念介绍
    - 三种坐标
    - bounds
    - map容器与leaflet图层
  - 结合crs再谈map容器
  - 绘制原理SVG和Canvas
  - dom事件方法
- ### leaflet源码目录结构及功能介绍
- ### core目录
  -  原型与原型链extend、bind等   
  -  L.Class的实现机制和开发使用风格规范   
  -  L.Event事件绑定的实现
  -  L.Handler自定义交互的实现
    如何写一个自己的交互插件
  -  L.Browser浏览器
- ### geo与geometry目录
  - proj4leaflet
  - 常用的crs
  - 常用的projection
  - latlng与bounds
  - geo相关工具
- ### map目录
  - 主角map
  -  map的视图接口map.js
  -  map的交互handler
  选取L.Map.Drag和ScrollWheelZoom为例
  - ext与anim动画
- ### layer目录
  - 我们看到的都是layer
  - layer的实现框架layer.js
  - 栅格图层
  - 矢量图层
    -  线面
  - dom元素图层Popup、Marker
  - 图层的管理LayerGroup
  - setInterval动画实现
- ### dom目录-dom的动画与事件
- ### control目录-ui控件
  - 什么是控件及实现逻辑
  - 例子说明
- ## 常用的leaflet的plugins
  - leaflet.draw
- ## 离线地图数据源与geojson数据分享
- ## 算法工具分享
- ## leaflet的问题与未来
  - 大数据渲染支持有限
  - 不支持旋转，不支持3D效果
