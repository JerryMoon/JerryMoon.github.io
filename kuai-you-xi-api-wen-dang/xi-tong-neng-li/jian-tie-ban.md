# 剪贴板

---

## 接口定义

### qg.setClipboardData\(Object object\)

修改剪贴板内容

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| text | String | 是 | 需要放到剪切板的内容 |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

#### 示例：

```js
qg.setClipboardData({
  text: 'text'
})
```

### qg.getClipboardData\(Object object\)

读取剪贴板内容

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### success返回值：

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| text | String | 剪切板内容 |

#### 示例：

```js
qg.getClipboardData({
  success: function (data) {
    console.log(`handling success: ${data.text}`)
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```

  


