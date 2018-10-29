# 帧率
---

### 渲染帧率

## 接口定义

### qg.setPreferredFramesPerSecond(number fps)

可以修改渲染帧率。默认渲染帧率为 60 帧每秒。修改后，requestAnimationFrame 的回调频率会发生改变。

#### 参数：

| 参数名      | 类型       | 必填   | 说明       |
| -------- | -------- | ---- | -------- |
| fps | number | 是    | 帧率，有效范围 1 - 60。     |

#### 示例：

```javascript
qg.setPreferredFramesPerSecond(60);
```
### number requestAnimationFrame(function callback)

在下次进行重绘时执行。

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| callback | function | 是 | 执行的 callback。 |

#### 返回值：
number 请求ID

#### 示例：

```javascript
var frameCallback = function() {
    console.log("frameCallback");
}
var id = requestAnimationFrame(frameCallback);
console.log("id = " + id);
```
### cancelAnimationFrame(number requestID)

取消一个先前通过调用 requestAnimationFrame 方法添加到计划中的动画帧请求

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| requestID | number | 是 | id |

#### 示例：

```javascript
qg.setPreferredFramesPerSecond(30);
var frameCallback = function() {
    console.log("frameCallback");
}
var id = requestAnimationFrame(frameCallback);
console.log("id = " + id);
cancelAnimationFrame(id);
```



