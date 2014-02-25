# 了解Cocos2d-html5 2.2.2分辨率策略

## Background背景

作为网络开发人员，我们都知道，要提供跨浏览器和跨平台的优质体验是相当困难的。一个主要的问题就是不断调整浏览器窗口的内容大小。现在有一种叫做响应式网页设计的东西，所以，对于Cocos2d-html5的开发人员，我们在2.2.2版本中为你带来了新的分辨率策略设计




cc.EGLView.getInstance().setDesignResolutionSize(320, 480, cc.RESOLUTION_POLICY.SHOW_ALL);



cc.EGLView.getInstance().setResolutionPolicy(cc.RESOLUTION_POLICY.NO_BORDER);


<body>


```




### 1. 帧




![](./res/showall.png)


### 2. NO_BORDER（与帧同等大小+无边框）

![](./res/noborder.png)

无边框策略（No border policy）将按比例调整容器大小，使其填满整个帧。在这种情况下，如果帧的宽/高比例与你设计的比例不一致，你游戏中的一些区域将被剪掉。

### 3. EXACT_FIT（与帧同等大小+精准配合）

![](./res/exactfit.png)

精确配合策略（Exact fit policy）将调整容器大小以精确符合帧，所以游戏的宽/高比例可能会丢失。

### 4. FIXED_WIDTH（与帧同等大小+固定宽度）

![](./res/fixedwidth.png)

固定宽度策略（Fixed width policy）将调整容器的宽度以符合帧的宽度，其高度也会做相应调整。

看起来好像和显示全部策略并无两样，但是这里，整个画面能填满整个帧，游戏世界的坐标系统和画面坐标系统一致。

### 5. FIXED_HEIGHT（与帧同等大小+固定高度）

![](./res/fixedheight.png)

游戏的宽度比游戏的高度要大，所以固定宽度策略有点像显示全部策略，而固定高度策略有点像无边框策略。相反，如果游戏的宽度比游戏的高度要小，那么固定宽度策略就会像无边框策略，而固定高度策略就有点像显示全部策略。但是固定高度及固定宽度策略都将视整个帧为可视窗及游戏世界矩形界面。






var policy = new cc.ResolutionPolicy(cc.ContainerStrategy.PROPORTION_TO_FRAME, cc.ContentStrategy.EXACT_FIT);





```

```
