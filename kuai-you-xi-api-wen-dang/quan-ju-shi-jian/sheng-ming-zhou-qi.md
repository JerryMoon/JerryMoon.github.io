# 生命周期
---

## 接口定义

### 方法

### qg.onShow\(OBJECT\)

监听游戏切入前台

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | ------------ |
| callback | Function | 是 | 接收前台事件回调 |

#### 示例：

```javascript
var showf = function (data) {
  console.log('game enter foreground')
}
qg.onShow(showf)
```

### qg.offShow\(OBJECT\)

取消监听游戏切入前台

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | ------------ |
| callback | Function | 否 | 需要取消的监听回调 |
注意：参数为空，将取消所有监听

#### 示例：

```javascript
var showf = function (data) {
  console.log('game enter foreground')
}
qg.onShow(showf);
......
qg.offShow(showf);
```

### qg.onHide\(OBJECT\)

监听游戏切入后台

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | ------------ |
| callback | Function | 是 | 接收后台事件回调 |

#### 示例：

```javascript
var hidef = function (data) {
  console.log('game enter background')
}
qg.onHide(hidef)
```

### qg.offHide\(OBJECT\)

取消监听游戏切入后台

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | ------------ |
| callback | Function | 否 | 需要取消的监听回调 |
注意：参数为空，将取消所有监听

#### 示例：

```javascript
var hidef = function (data) {
  console.log('game enter background')
}
qg.onHide(hidef)
......
qg.offHide(hidef)
```



