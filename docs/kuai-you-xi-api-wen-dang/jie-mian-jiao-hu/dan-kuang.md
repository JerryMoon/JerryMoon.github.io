# 弹窗

------

## 接口定义

### qg.showToast\(Object object\)

显示Toast

#### 参数：

| 参数名   | 类型   | 必填 | 说明                    |
| :------- | :----- | :--- | :---------------------- |
| message  | String | 是   | 要显示的文本            |
| duration | Number | 否   | 0为短时，1为长时，默认0 |

#### 示例：

```js
qg.showToast({
  message: 'message'
})
```

### qg.showDialog\(Object object\)

显示对话框

#### 参数：

| 参数名   | 类型     | 必填 | 说明                                                         |
| :------- | :------- | :--- | :----------------------------------------------------------- |
| title    | String   | 否   | 标题                                                         |
| message  | String   | 否   | 内容                                                         |
| buttons  | Array    | 否   | 按钮的数组，按钮结构：{text:'text',color:'\#333333'}，color可选：buttons的第1项为positive button；buttons的第2项（如果有）为negative button；buttons的第3项（如果有）为neutral button。最多支持3个button |
| success  | Function | 否   | 成功回调                                                     |
| cancel   | Function | 否   | 取消回调                                                     |
| complete | Function | 否   | 执行结束后的回调                                             |

##### success返回值：

| 参数名 | 类型    | 说明                          |
| :----- | :------ | :---------------------------- |
| index  | Integer | 选中按钮在buttons数组中的序号 |

#### 示例：

```js
qg.showDialog({
  title: 'title',
  message: 'message',
  buttons: [
    {
      text: 'btn',
      color: '#33dd44'
    }
  ],
  success: function (data) {
    console.log('handling callback')
  },
  cancel: function () {
    console.log('handling cancel')
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```

### qg.showLoading\(Object object\)

显示loading提示框

#### 参数：

| 参数名   | 类型     | 必填 | 说明             |
| :------- | :------- | :--- | :--------------- |
| message  | String   | 否   | 要显示的文字     |
| success  | Function | 否   | 成功回调         |
| cancel   | Function | 否   | 取消回调         |
| complete | Function | 否   | 执行结束后的回调 |

#### 示例：

```js
qg.showLoading({
    message: "loading",
    success: function () {
        console.log('handling success')
    },
    fail: function (data, code) {
        console.log(`handling fail, code = ${code}`)
    }
})
```

### qg.hideLoading\(\)

隐藏loading提示框

#### 参数：

无

#### 示例：

```js
qg.hideLoading()
```



