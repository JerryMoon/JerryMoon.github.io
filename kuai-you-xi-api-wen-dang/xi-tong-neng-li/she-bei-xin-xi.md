# 设备信息

---

## 接口定义

### qg.getSystemInfo\(Object object\)

获取系统信息

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### success返回值：

| 参数值 | 类型 | 说明 |
| :--- | :--- | :--- |
| brand | String | 设备品牌 |
| manufacturer | String | 设备生产商 |
| model | String | 设备型号 |
| product | String | 设备代号 |
| osType | String | 操作系统名称 |
| osVersionName | String | 操作系统版本名称 |
| osVersionCode | Integer | 操作系统版本号 |
| platformVersionName | String | 运行平台版本名称 |
| platformVersionCode | Integer | 运行平台版本号 |
| language | String | 系统语言 |
| region | String | 系统地区 |
| screenWidth | Integer | 屏幕宽 |
| screenHeight | Integer | 屏幕高 |
| battery | Number | 当前电量，0.0 - 1.0 之间 |
| wifiSignal | Integer | wifi信号强度，范围0 - 4 |

#### 示例：

```js
qg.getSystemInfo({
  success: function (ret) {
    console.log(`handling success， brand = ${ret.brand}`)
  }
})
```

### qg.getSystemInfoSync\(Object object\)

获取系统信息的同步版本

##### 返回值：

##### Object res {#object-res}

| 参数值 | 类型 | 说明 |
| :--- | :--- | :--- |
| brand | String | 设备品牌 |
| manufacturer | String | 设备生产商 |
| model | String | 设备型号 |
| product | String | 设备代号 |
| osType | String | 操作系统名称 |
| osVersionName | String | 操作系统版本名称 |
| osVersionCode | Integer | 操作系统版本号 |
| platformVersionName | String | 运行平台版本名称 |
| platformVersionCode | Integer | 运行平台版本号 |
| language | String | 系统语言 |
| region | String | 系统地区 |
| screenWidth | Integer | 屏幕宽 |
| screenHeight | Integer | 屏幕高 |
| battery | Number | 当前电量，0.0 - 1.0 之间 |
| wifiSignal | Integer | wifi信号强度，范围0 - 4 |

#### 示例：

```js
var data = qg.getSystemInfoSync()
```



