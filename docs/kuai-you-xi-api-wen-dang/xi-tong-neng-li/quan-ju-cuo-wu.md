# 全局错误


## 接口定义

### 方法

### qg.onError(OBJECT)

接收全局错误

#### OBJECT参数：

| 参数名   | 类型     | 必填 | 说明         |
| -------- | -------- | ---- | ------------ |
| callback | Function | 否   | 接收全局错误 |

#### callback参数：

| 参数名  | 类型   | 说明         |
| ------- | ------ | ------------ |
| message | String | 错误堆栈信息 |

#### 示例：

```javascript
qg.onError = function (data) {
  console.log(`message is ${data.message}`)
};
```
