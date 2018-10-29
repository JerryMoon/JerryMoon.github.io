# 画布
---
## 接口定义

### Canvas qg.createCanvas()

创建一个画布对象。首次调用创建的是显示在屏幕上的画布，之后调用创建的都是离屏画布。

#### 参数：
无

##### 返回值：

[Canvas](/xuan-ran/hua-bu/canvas.md) 画布对象

#### 示例：

```javascript
var canvas = qg.createCanvas();
console.log("canvas = " + canvas);
```


