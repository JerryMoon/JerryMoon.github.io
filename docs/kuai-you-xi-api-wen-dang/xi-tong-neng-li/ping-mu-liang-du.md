# 屏幕亮度

---

## 接口定义

### qg.getScreenBrightness\(Object object\)

获得当前屏幕亮度值

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### success返回值：

| 参数值 | 类型 | 说明 |
| :--- | :--- | :--- |
| value | Integer | 屏幕亮度，取值范围0-255 |

#### 示例：

```js
qg.getScreenBrightness({
  success:function(data){
    console.log(`handling success, value = ${data.value}`)
  },
  fail: function(data, code){
    console.log(`handling fail, code = ${code}`)
  }
})
```

### qg.setScreenBrightness\(Object object\)

设置当前屏幕亮度值

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | Integer | 是 | 屏幕亮度，取值范围0-255 |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

#### 示例：

```js
qg.setScreenBrightness({
  value: 100,
  success: function () {
    console.log('handling success')
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```

### qg.getScreenBrightnessMode\(Object objec\)

获得当前屏幕亮度模式

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### success返回值：

| 参数值 | 类型 | 说明 |
| :--- | :--- | :--- |
| mode | Integer | 0为手动调节屏幕亮度,1为自动调节屏幕亮度 |

#### 示例：

```js
qg.getScreenBrightnessMode({
  success: function (data) {
    console.log(`handling success, mode = ${data.mode}`)
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```

### qg.setScreenBrightnessMode\(Object object\)

设置当前屏幕亮度模式

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| mode | Integer | 是 | 0为手动调节屏幕亮度,1为自动调节屏幕亮度 |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

#### 示例：

```js
qg.setScreenBrightnessMode({
  mode: 1,
  success: function () {
    console.log('handling success')
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```

### qg.setKeepScreenOn\(Object object\)

设置是否保持常亮状态。仅在当前快游戏生效，离开快游戏后设置失效。

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| keepSrceenOn | boolean | 是 | 设置是否保持常亮状态 |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

#### 示例：

```js
qg.setKeepScreenOn({
  keepScreenOn: true,
  success: function () {
    console.log('handling success')
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```



