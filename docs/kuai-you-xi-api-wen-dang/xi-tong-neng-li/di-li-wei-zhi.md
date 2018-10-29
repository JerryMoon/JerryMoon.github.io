# 地理位置

---

## 接口定义

### qg.getLocation\(OBJECT\)

获取地理位置

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| timeout | Long | 否 | 设置超时时间，单位是ms，默认值为30000。在权限被系统拒绝或者定位设置不当的情况下，有可能永远不能返回结果，因而需要设置超时。超时后会使用fail回调 |
| success | Function | 是 | 成功回调 |
| fail | Function | 否 | 失败回调，原因可能是用户拒绝 |
| complete | Function | 否 | 执行结束后的回调 |

##### success返回值：

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| longitude | Number | 经度 |
| latitude | Number | 纬度 |

##### fail返回错误代码

| 错误码 | 说明 |
| :--- | :--- |
| 201 | 用户拒绝，获取定位权限失败 |
| 204 | 超时返回 |
| 1000 | 系统位置开关关闭 |

#### 示例：

```js
qg.getLocation({
  success: function (data) {
    console.log(`handling success: longitude = ${data.longitude}, latitude = ${data.latitude}`)
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```

### qg.getLocationType\(OBJECT\)

获取系统当前支持的定位类型

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| success | Function | 是 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### success返回值：

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| types | Array | 支持的类型\['gps','network'\] |

#### 示例：

```js
qg.getLocationType({
  success: function (data) {
    console.log(`handling success: locationType = ${data.types}`)
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```

### qg.subscribeLocation\(Object object\)

监听地理位置。如果多次调用，仅最后一次调用生效

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| callback | Function | 是 | 每次位置信息发生变化，都会被回调 |
| fail | Function | 否 | 失败回调，原因可能是用户拒绝 |

##### callback返回值：

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| longitude | Number | 经度 |
| latitude | Number | 纬度 |

##### fail返回错误代码

| 错误码 | 说明 |
| :--- | :--- |
| 201 | 用户拒绝，获取定位权限失败 |
| 1000 | 系统位置开关关闭 |

#### 示例：

```js
qg.subscribeLocation({
  callback: function (data) {
    console.log(`handling success: longitude = ${data.longitude}, latitude = ${data.latitude}`)
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```

### qg.unsubscribeLocation\(\)

取消监听地理位置

#### 参数：

无

#### 示例：

```js
qg.unsubscribeLocation()
```



