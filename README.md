# 室内地图-蜂鸟地图

<a name="cRDYT"></a>
### 一.简介
蜂鸟地图是基于第三方地图厂商北京蜂鸟视图科技有限公司(官网: [https://www.fengmap.com/](https://www.fengmap.com/))提供的SDK, 以及在蜂鸟云定制好的地图文件(star.fmap), 进行可视化展示的一种地图类型.<br />

<a name="werZo"></a>
### 二.地图厂商JSSDK自带的功能


<a name="yjjBY"></a>
#### 1. 地图展示
![image.png](https://cdn.nlark.com/yuque/0/2019/png/182173/1564975224652-45a51bf4-c148-4bb3-8a06-05b02100671c.png#align=left&display=inline&height=156&name=image.png&originHeight=311&originWidth=670&size=68023&status=done&width=335)
<a name="3OHpL"></a>
#### 2. 楼层切换
![fengmap.gif](https://cdn.nlark.com/yuque/0/2019/gif/182173/1564975479119-03950f2d-414d-459b-8d08-90d82fe39149.gif#align=left&display=inline&height=230&name=fengmap.gif&originHeight=391&originWidth=761&size=367168&status=done&width=448)

<a name="leWpX"></a>
#### 3. 2D - 3D 渲染模式的切换
![2D~3D.gif](https://cdn.nlark.com/yuque/0/2019/gif/182173/1564975557163-9a0a755e-ba01-4a89-a3ed-e4edcc2bcae3.gif#align=left&display=inline&height=211&name=2D~3D.gif&originHeight=391&originWidth=761&size=83882&status=done&width=410)

<a name="YrxIC"></a>
#### 4. 地图主题的切换
![theme.gif](https://cdn.nlark.com/yuque/0/2019/gif/182173/1564976721921-d27a72fe-269e-49fe-a056-d256d5a98d3e.gif#align=left&display=inline&height=191&name=theme.gif&originHeight=391&originWidth=750&size=284545&status=done&width=366)


<a name="CO8QI"></a>
### 三.基于JSSDK自主实现的功能
<a name="2WLF0"></a>
#### 1. colorby
![colorBy.gif](https://cdn.nlark.com/yuque/0/2019/gif/182173/1564977081882-9d613e9f-188d-497a-aa2a-7dc9fe04dee7.gif#align=left&display=inline&height=181&name=colorBy.gif&originHeight=391&originWidth=750&size=464369&status=done&width=348)
<a name="9iUuB"></a>
#### 2. tooltip 展示更多的信息
![colorBy.gif](https://cdn.nlark.com/yuque/0/2019/gif/182173/1564977081882-9d613e9f-188d-497a-aa2a-7dc9fe04dee7.gif#align=left&display=inline&height=181&name=colorBy.gif&originHeight=391&originWidth=750&size=464369&status=done&width=348)

<a name="Zhm4T"></a>
#### 3. 联动其他卡片
![link.gif](https://cdn.nlark.com/yuque/0/2019/gif/182173/1564977979400-962ed8fc-ba6c-41c1-a90e-aee3625d1f53.gif#align=left&display=inline&height=136&name=link.gif&originHeight=480&originWidth=1179&size=745931&status=done&width=333)
<a name="8AiKi"></a>
#### 4. 版本管理
![mitileVersion.gif](https://cdn.nlark.com/yuque/0/2019/gif/182173/1564977614342-bb3e42db-6da5-451c-9435-a28597b2144a.gif#align=left&display=inline&height=172&name=mitileVersion.gif&originHeight=391&originWidth=750&size=127808&status=done&width=329)


<br />
<br />

<a name="uvn8o"></a>
### 四.所使用用到的JSSDK所提供的功能接口
<a name="FOt1D"></a>
#### 1. 提供基础config加载地图(主题, 渲染模式, 地图文件路径等在此进行配置)

```javascript
new fengmap.FMMap(options)
```
[https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMMap.html](https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMMap.html)
<a name="7lnpA"></a>
#### 2. tooltip控件
```javascript
new fengmap.FMPopInfoWindow(map, ctrlOpts, marker)
```

[https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMPopInfoWindow.html](https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMPopInfoWindow.html)

<a name="FN7IA"></a>
#### 3. 多楼层按钮
```javascript
new fengmap.FMButtonGroupsControl(map, ctrlOpts)
```

[https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMButtonGroupsControl.html](https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMButtonGroupsControl.html)

<a name="6RVzm"></a>
#### 4. 自定义地图区块文字(用于版本管理)
```javascript
new fengmap.FMTextMarker(opts)

FMLabelLayer
```

[https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMTextMarker.html](https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMTextMarker.html)<br />[https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMLabelLayer.html](https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMLabelLayer.html)

<a name="9VUfz"></a>
#### 5. Event: 注册hover到每个区块的回调函数 (tooltip)
```javascript
map.on('mapHoverNode', (e) => {
	
})
```
[https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMMap.html#event:mapHoverNode](https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMMap.html#event:mapHoverNode)

<a name="nf3rn"></a>
#### 6.Event: 注册click到每个区块的回调函数 (跳转、联动、下钻)
```javascript
map.on('mapClickNode', (e) => {
	
})
```
[https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMMap.html#event:mapClickNode](https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMMap.html#event:mapClickNode)

<a name="9P5Uo"></a>
#### 7. Event: 注册地图加载完成的回调函数
```javascript
map.on('loadComplete', (e) => {
	
})
```
[https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMMap.html#event:loadComplete](https://www.fengmap.com/docs/js/v2.3.0_beta/fengmap.FMMap.html#event:loadComplete)

