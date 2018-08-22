# 图片
---
## 接口定义

### Image qg.createImage()

创建一个图片对象

#### 参数：
无

##### 返回值：

[Image](/xuan-ran/tu-pian/image.md) 图片对象

#### 示例：

```javascript
var image = qg.createImage();
image.src = 'http://www.w3school.com.cn/i/eg_tulip.jpg';
image.onload = function() {
    console.log("w = " + image.width + ", h = " + image.height);
}
```


