# markImage 图片标注插件
使用canvas进行图片标注，独立js插件，方便二次开发，可在任意web前端框架中使用。

## 功能

1. 自由缩放图片，适配图片到容器区域
2. 编辑拖拽框选矩形大小与位置，8个控制点调整大小
3. 实时输出框选位置
4. 记忆缩放中心位置
5. 实时输出框选矩形列表

<img src="./example.png">

## 使用方法

1. 直接引入MarkImage.js。
2. 如果是模块引入，需要修改MarkImage.js的导出方式。

```javascript
  const markImage = new MarkImage({
    el: '.container',                  // 挂载节点，HTMLElement，string，都可以
    imageSrc: './test1.jpg',           // 引入需要标注的图片
    showLabel: true,                   // 默认为true
    showPix: true,                     // 默认为true
    data: [                            // 初始化默认的标注位置
       [461, 348, 573, 467],
       [922, 351, 1019, 469],
       [683, 51, 792, 162],
       [31, 663, 187, 799],
       [656, 677, 797, 812],
       [41, 139, 173, 244],
       [842, 682, 991, 846],
    ],
    onSelect(index, coor) {            // 输出当前选中的标注矩形，参数 index为索引,coor为坐标
      console.log(index,coor)
    },          
    onResult(list) {                   // 输出标注的矩形列表，也可以直接通过markImage.dataset获取
      console.log(list)
    }                  
  })
  
  // 放大
  markImage.zoomIn()
  // 缩小
  markImage.zoomOut()
  // 适配
  markImage.fitting()
  // 切换可移动状态，状态可通过markImage.lockImage来获取
  markImage.setAutoLock()
  // 删除
  markImage.remove(index)
```
详细参考index.html
