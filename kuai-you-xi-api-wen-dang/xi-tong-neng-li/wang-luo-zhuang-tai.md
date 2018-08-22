# 网络状态

---

## 接口定义

### qg.getNetworkType\(Object object\)

获取网络类型

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调，可能是因为缺乏权限 |
| complete | Function | 否 | 执行结束后的回调 |

##### success返回值：

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| metered | Boolean | 是否按照流量计费 |
| type | String | 网络类型，可能的值为2g，3g，4g，wifi，none |

#### 示例：

```js
qg.getNetworkType({
  success: function (data) {
    console.log(`handling success: ${data.type}`)
  }
})
```

### qg.subscribeNetworkStatus\(Object object\)

监听网络连接状态。如果多次调用，仅最后一次调用生效

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| callback | Function | 否 | 每次网络发生变化，都会被回调 |
| fail | Function | 否 | 失败回调，可能是因为缺乏权限 |

##### callback返回值：

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| metered | Boolean | 是否按照流量计费 |
| type | String | 网络类型，可能的值为2g，3g，4g，wifi，none |

#### 示例：

```js
qg.subscribeNetworkStatus({
  callback: function (data) {
    console.log('handling callback')
  }
})
```

### qg.unsubscribeNetworkStatus\(\)

取消监听网络连接状态

#### 参数：

无

#### 示例：

```js
qg.unsubscribeNetworkStatus()
```

### qg.getWifiSignalSync\(\)

获得wifi强度

##### 返回值：

##### Object res {#object-res}

| 参数值 | 类型 | 说明 |
| :--- | :--- | :--- |
| value | Integer | wifi信号强度，范围0 - 4 |

#### 示例：

```js
var data = qg.getWifiSignalSync();
```



