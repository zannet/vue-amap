# 多边形

---

## 示例

```html
<div id="demoComponent" class="demo-component">
    <amap id="amap" :zoom="zoom" :center="center">
      <amap-polygon v-for="polygon in polygons" :path="polygon.path" :events="polygon.events"></amap-polygon>
    </amap>
  </div>
</div>
```

```javascript
export default {
  name: 'demoComponent',
  data () {
    return {
      zoom: 15,
      center: [121.5273285, 31.21515044],
      polygons: [
        {
          path: [[121.5273285, 31.21515044], [121.5293285, 31.21515044], [121.5293285, 31.21915044], [121.5273285, 31.21515044]],
          events: {
            click() {
              alert('click polygon');
            },
            init(o) {
              // o为多边形覆盖物实例
              // 这里为直接操作实例的入口
              // 不推荐使用
            }
          }
        }
      ]
    }
  }
}
```


<div class="map-present">
  <div id="demoComponent" class="demo-component">
      <amap id="amap" :zoom="zoom" :center="center">
        <amap-polygon v-for="polygon in polygons" :path="polygon.path" :events="polygon.events"></amap-polygon>
      </amap>
    </div>
  </div>
</div>

<script>
export default {
  name: 'demoComponent',
  data () {
    return {
      zoom: 15,
      center: [121.5273285, 31.21515044],
      polygons: [
        {
          path: [[121.5273285, 31.21515044], [121.5293285, 31.21515044], [121.5293285, 31.21915044], [121.5273285, 31.21515044]],
          events: {
            click() {
              alert('click polygon');
            }
          }
        }
      ]
    }
  }
}
</script>

## 静态属性
仅且可以初始化配置，不支持响应式。

名称 | 类型 | 说明
---|---|---|
zIndex | Number | 多边形覆盖物的叠加顺序。地图上存在多个多边形覆盖物叠加时，通过该属性使级别较高的多边形覆盖物在上层显示默认zIndex：10
bubble | Boolean | 是否将覆盖物的鼠标或touch等事件冒泡到地图上（自v1.3 新增）默认值：false
strokeColor | String | 线条颜色，使用16进制颜色代码赋值。默认值为#006600
strokeOpacity | float | 轮廓线透明度，取值范围[0,1]，0表示完全透明，1表示不透明。默认为0.9
strokeWeight | Number | 轮廓线宽度
fillColor | String | 多边形填充颜色，使用16进制颜色代码赋值，如：#FFAA00
fillOpacity | Float | 多边形填充透明度，取值范围[0,1]，0表示完全透明，1表示不透明。默认为0.9
extData | Any | 用户自定义属性，支持JavaScript API任意数据类型，如Polygon的id等
strokeStyle | String | 轮廓线样式，实线:solid，虚线:dashed

## 动态属性
支持响应式。

名称 | 类型 | 说明
---|---|---|
path | Array| 多边形轮廓线的节点坐标数组，当为“环”多边形时（多边形区域在多边形内显示为“岛”），path为二维数组，数组元素为多边形轮廓的节点坐标数组“环”多边形时，要求数组第一个元素为外多边形，其余为“岛”多边形，外多边形需包含“岛”多边形，否则程序不作处理

## 事件

事件 | 参数 | 说明
---|---|---|
init |[Polygon](http://lbs.amap.com/api/javascript-api/reference/overlay/#Polygon) | 高德多边形覆盖物实例
click | [MapsEvent](http://lbs.amap.com/api/javascript-api/reference/event/#MapsEvent) | 鼠标左键单击事件
dblclick | [MapsEvent](http://lbs.amap.com/api/javascript-api/reference/event/#MapsEvent) | 鼠标左键双击事件
rightclick | [MapsEvent](http://lbs.amap.com/api/javascript-api/reference/event/#MapsEvent) | 右键单击
hide | {type, target} | 隐藏
show | {type, target} | 显示
mousedown | [MapsEvent](http://lbs.amap.com/api/javascript-api/reference/event/#MapsEvent) | 鼠标按下
mouseup | [MapsEvent](http://lbs.amap.com/api/javascript-api/reference/event/#MapsEvent) | 鼠标抬起
mouseover | [MapsEvent](http://lbs.amap.com/api/javascript-api/reference/event/#MapsEvent) | 鼠标经过
mouseout | [MapsEvent](http://lbs.amap.com/api/javascript-api/reference/event/#MapsEvent) | 鼠标移出
change |  | 属性发生变化时
touchstart | [MapsEvent](http://lbs.amap.com/api/javascript-api/reference/event/#MapsEvent) | 触摸开始时触发事件，仅适用移动设备
touchmove | [MapsEvent](http://lbs.amap.com/api/javascript-api/reference/event/#MapsEvent) | 触摸移动进行中时触发事件，仅适用移动设备
touchend | [MapsEvent](http://lbs.amap.com/api/javascript-api/reference/event/#MapsEvent) | 触摸结束时触发事件，仅适用移动设备