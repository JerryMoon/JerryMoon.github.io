# 多媒体
---
## 接口定义

### qg.takePhoto(OBJECT)

拍摄照片

#### 参数：

| 参数名      | 类型       | 必填   | 说明       |
| -------- | -------- | ---- | -------- |
| success  | Function | 否    | 成功回调     |
| fail     | Function | 否    | 失败回调     |
| cancel   | Function | 否    | 取消回调     |
| complete | Function | 否    | 执行结束后的回调 |

##### success返回值：

| 参数名  | 类型     | 说明      |
| ---- | ------ | ------- |
| uri  | String | 选取的文件路径 |

##### fail返回错误代码

| 错误码  | 说明            |
| ---- | ------------- |
| 201  | 用户拒绝，获取相机权限失败 |

#### 示例：

```javascript
qg.takePhoto({
  success: function (data) {
    console.log(`handling success: ${data.uri}`)
  },
  fail: function (code) {
    console.log(`handling fail: ${code}`)
  },
})
```

### qg.pickImage(OBJECT)

选择图片

#### 参数：

| 参数名      | 类型       | 必填   | 说明       |
| -------- | -------- | ---- | -------- |
| success  | Function | 否    | 成功回调     |
| fail     | Function | 否    | 失败回调     |
| cancel   | Function | 否    | 取消回调     |
| complete | Function | 否    | 执行结束后的回调 |

##### success返回值：

| 参数名  | 类型     | 说明      |
| ---- | ------ | ------- |
| uri  | String | 选取的文件路径 |

#### 示例：

```javascript
qg.pickImage({
  success: function (data) {
    console.log(`handling success: ${data.uri}`)
  }
})
```

### qg.saveToPhotosAlbum(OBJECT)

将图片/视频保存到相册中．需要用户授权

#### 参数：

| 参数名      | 类型       | 必填   | 说明                         |
| -------- | -------- | ---- | -------------------------- |
| uri      | String   | 是    | 源文件的uri，文件的扩展名必须是图片或视频的扩展名 |
| success  | Function | 否    | 成功回调                       |
| fail     | Function | 否    | 失败回调                       |
| complete | Function | 否    | 执行结束后的回调                   |

##### fail返回错误代码：

| 错误码  | 说明    |
| ---- | ----- |
| 201  | 用户拒绝  |
| 202  | 参数错误  |
| 300  | I/O错误 |

#### 示例：

```javascript
media.saveToPhotosAlbum({
  uri:'internal://tmp/abc.jpg',
  success: function () {
    console.log(`save success`)
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```
### qg.previewImage(OBJECT)

图片预览

#### 参数：

| 参数名      | 类型       | 必填   | 说明                         |
| -------- | -------- | ---- | -------------------------- |
| uris      | String[]   | 是    | 源文件的uri，可以是internal路径，也可以是网络url |
| success  | Function | 否    | 成功回调                       |
| fail     | Function | 否    | 失败回调                       |
| complete | Function | 否    | 执行结束后的回调                   |

##### fail返回错误代码：

| 错误码  | 说明    |
| ---- | ----- |
| 202  | 参数错误  |

#### 示例：

```javascript
qg.previewImage({
  uri:['internal://tmp/abc.jpg',    
      'https://shopstatic.vivo.com.cn/vivoshop/commodity/20180813/20180813172027904331_original.jpg']
  success: function () {
    console.log(`save success`)
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```


