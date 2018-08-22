# 上传下载

## 接口定义

### qg.uploadFile(OBJECT)

上传文件

#### 参数：

| 参数名       | 类型     | 必填 | 说明                                                         |
| ------------ | -------- | ---- | ------------------------------------------------------------ |
| url          | String   | 是   | 资源url                                                      |
| header       | Object   | 否   | 请求的header，会将其所有属性设置到请求的header部分。useragent设置无效。 |
| method       | String   | 否   | 默认为POST，可以是： POST, PUT                               |
| files        | Array    | 是   | 需要上传的文件列表，使用multipart/form-data方式提交          |
| data | Array    | 否   | HTTP请求中其他额外的form data                                |
| success      | Function | 否   | 成功返回的回调函数                                           |
| fail         | Function | 否   | 失败的回调函数                                               |
| complete     | Function | 否   | 结束的回调函数（调用成功、失败都会执行）                     |

##### files参数 ：

  files参数是一个file对象的数组，file对象的结构如下：

| 参数名   | 类型   | 必填 | 说明                                                       |
| -------- | ------ | ---- | ---------------------------------------------------------- |
| filename | String | 否   | multipart提交时，header中的文件名                          |
| name     | String | 否   | multipart提交时，表单的项目名,默认file                     |
| uri      | String | 是   | 文件的本地地址                                             |
| type     | String | 否   | 文件的Content-Type格式,默认会根据filename或者uri的后缀获取 |

##### data参数：

| 参数名 | 类型   | 必填 | 说明             |
| ------ | ------ | ---- | ---------------- |
| name   | String | 是   | form元素的名称。 |
| value  | String | 是   | form元素的值。   |

##### success返回值：

| 参数名  | 类型    | 说明                                                         |
| ------- | ------- | ------------------------------------------------------------ |
| code    | Integer | 服务器状态code                                               |
| data    | String  | 如果服务器返回的header中type是text/*或application/json、application/javascript、application/xml，值是文本内容，否则是存储的临时文件的uri临时文件如果是图片或者视频内容，可以将图片设置到image或video控件上显示 |
| headers | Object  | 服务器response的所有header                                   |

#### 示例：

```javascript
qg.uploadFile({
  url: 'http://www.example.com',
  files: [
    {
      uri: 'internal://xxx/xxx/test',
      name: 'file1',
      filename: 'test.png'
    }
  ],
  data: [
    {
      name: 'param1',
      value: 'value1'
    }
  ],
  success: function (data) {
    console.log('handling success')
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```

### qg.download(OBJECT)

下载文件资源到本地，客户端直接发起一个 HTTP GET 请求，返回文件的本地文件路径。

#### 参数：

| 属性     | 键值类型 | 是否必填 | 说明                                          |
| :------- | :------- | :------- | :-------------------------------------------- |
| url      | string   | 是       | 下载资源的 url                                |
| header   | Object   | 是       | HTTP 请求的 Header，Header 中不能设置 Referer           |
| success  | function | 否       | 接口调用成功的回调函                          |
| fail     | function | 否       | 接口调用失败的回调函数                        |
| complete | function | 否       | 接口调用结束的回调函数                        |

#### 回调函数

| 属性         | 键值类型 | 说明                           |
| :----------- | :------- | :----------------------------- |
| tempFilePath | string   | 临时文件路径                   |
| statusCode   | number   | 开发者服务器返回的 HTTP 状态码 |

#### 返回值
DownloadTask

一个可以监听下载进度变化事件，以及取消下载任务的对象

DownloadTask.abort()

中断下载任务

DownloadTask.onProgressUpdate(function callback)

监听下载进度变化事件

#### 示例：

```javascript
var downloadTask = qg.download({
  url: 'http://www.example.com',
  success: function (data) {
    console.log(`handling success${data.token}`)
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
downloadTask.onProgressUpdate = function (msg) {
    var progress = msg["progress"];
    console.log("onProgressUpdate " + progress);
};
downloadTask.abort();
```