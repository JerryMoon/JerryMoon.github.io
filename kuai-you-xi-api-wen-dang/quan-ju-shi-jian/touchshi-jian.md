# 触摸事件
---

## 接口定义

### 参数

#### OBJECT参数：

| 参数名   | 类型     | 必填 | 说明         |
| -------- | -------- | ---- | ------------ |
| callback | Function | 否   | 接收触摸事件 |

#### callback参数：

| 参数名         | 类型          | 说明                     |
| -------------- | ------------- | ------------------------ |
| touches        | Array.<Touch> | 当前所有触摸点的列表     |
| changedTouches | Array.<Touch> | 触发此次事件的触摸点列表 |
| timeStamp      | number        | 事件触发时的时间戳       |

#### Touch属性：

| 参数       | 类型   | 说明                             |
| ---------- | ------ | -------------------------------- |
| identifier | number | Touch 对象的唯一标识符，只读属性 |
| clientX    | number | 触点相对于视图左边沿的 X 坐标    |
| clientY    | number | 触点相对于视图上边沿的 Y 坐标。  |



### 方法

### qg.onTouchStart(function callback)

监听触摸开始事件

```javascript
var startHandler = function () {
  // do something
};
this.handleStart=this.startHandler.bind(this)
qg.onTouchStart(this.handleStart)
```

### qg.offTouchStart(function callback)

取消监听开始触摸事件

#### 示例：

```javascript
qg.offTouchStart(this.handleStart)
```
### qg.onTouchMove(function callback)

接收触摸移动事件

```javascript
var moveHandler = function () {
  // do something
};
this.handleMove = this.moveHandler.bind(this)
qg.onTouchMove(this.handleMove)
```

### qg.offTouchMove(function callback)

取消监听触点移动事件

#### 示例：

```javascript
qg.offTouchMove(this.handleMove)
```
### qg.onTouchCancel(function callback)

接收触摸取消事件

```javascript
var cancelHandler = function () {
  // do something
};
this.handleCancel = this.cancelHandler.bind(this)
qg.onTouchCancel(this.handleCancel)
```

### qg.offTouchCancel(function callback)

取消监听触摸结束事件

#### 示例：

```javascript
qg.offTouchCancel(this.handleCancel)
```
### qg.onTouchEnd(function callback)

接收触摸结束事件

```javascript
var endHandler = function () {
  // do something
};
this.handleEnd = this.endHandler.bind(this)
qg.onTouchEnd(this.handleEnd)
```

### qg.offTouchEnd(function callback)

取消监听触点失效事件

#### 示例：

```javascript
qg.offTouchEnd(this.handleEnd)
```
