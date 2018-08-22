# 支付
---

### 支付服务

## 接口定义

### qg.pay(Object object)

使用支付完成付款。

#### 参数：

| 参数名      | 类型       | 必填   | 说明       |
| -------- | -------- | ---- | -------- |
| orderInfo | string | 是    | 订单信息。|
| success | Function | 否    | 成功回调。 |
| fail | Function | 否    | 失败回调。 |
| complete | Function | 否    | 执行结束后的回调。 |

#### success返回值：
| 参数名      | 类型      | 说明       |
| -------- | -------- | -------- |
| code | number | 返回状态码。 |
| message | string  | 消息内容。 |
| result | string  | 支付结果。 |

#### fail返回错误代码：
| 参数名      | 类型      | 说明       |
| -------- | -------- | -------- |
| code | number | 返回状态码。 |
| message | string  | 消息内容。 |

#### 示例：

```javascript
qg.pay({
  orderInfo: 'order1',
  success: function (data) {
    console.log(`handling success: ${data.code}`)
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```

