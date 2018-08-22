# Canvas
---

### 画布对象

## 属性：
| 属性      | 类型       | 说明  |
| -------- | -------- | ---- |
| width | number | 画布的宽度    |
| height | number | 画布的高度    |

## 接口定义

### RenderingContext Canvas.getContext(string contextType)

获取画布对象的绘图上下文

#### 参数：

| 参数名      | 类型       | 必填   | 说明       |
| -------- | -------- | ---- | -------- |
| contextType | String | 是    | 上下文类型     |

##### contextType取值：

| 值      | 类型      | 说明       |
| -------- | -------- | -------- |
| 2d | String  | 2d 绘图上下文     |
| webgl | String  | webgl 绘图上下文     |

#### 返回值：
[RenderingContext](/xuan-ran/hua-bu/renderingcontext.md) 绘图上下文

#### 示例：

```javascript
var canvas = qg.createCanvas();
var gl = canvas.getContext("webgl");
console.log("gl = " + gl);
```



