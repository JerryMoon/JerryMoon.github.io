# RenderingContext
---
## 绘图上下文

### 说明
通过 Canvas.getContext('2d') 接口可以获取 CanvasRenderingContext2D 对象。CanvasRenderingContext2D 实现了 [HTML Canvas 2D Context](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D) 定义的一部分属性、方法。
通过 Canvas.getContext('webgl') 接口可以获取 WebGLRenderingContext 对象。 WebGLRenderingContext 实现了 [WebGL 1.0](https://developer.mozilla.org/zh-CN/docs/Web/API/WebGLRenderingContext) 定义的所有属性、方法、常量。

#### 2d 接口支持情况
CanvasRenderingContext2D 仅用于文字渲染等功能，暂不支持游戏开发。

#### WebGL 暂不支持的接口
* pixelStorei 当第一个参数是 gl.UNPACK_COLORSPACE_CONVERSION_WEBGL 时
* compressedTexImage2D
* compressedTexSubImage2D
* getExtension
* getSupportedExtensions
    






