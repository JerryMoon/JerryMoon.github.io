# 电量信息

---

## 接口定义

### qg.getBatteryInfo\(Object object\)

获取设备的电量信息

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### success返回值：

| 参数值 | 类型 | 说明 |
| :--- | :--- | :--- |
| charging | Boolean | 是否正在充电。 |
| level | Number | 当前电量，0.0 - 1.0 之间。 |

#### 示例：

```js
qg.getBatteryInfo({
  success: function (data) {
    console.log(`handling success: ${data.level}`)
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```

### qg.getBatteryInfoSync\(\)

获取设备的电量信息的同步版本

#### 参数：

##### 返回值：

##### Object res {#object-res}

| 参数值 | 类型 | 说明 |
| :--- | :--- | :--- |
| charging | Boolean | 是否正在充电。 |
| level | Number | 当前电量，0.0 - 1.0 之间。 |

#### 示例：

```js
var data = qg.getBatteryInfoSync();
```



