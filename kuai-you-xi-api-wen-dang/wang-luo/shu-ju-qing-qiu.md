# 数据请求

## 接口定义

### qg.request(OBJECT)

发起网络请求

#### 参数：

建议使用标准的XMLHttpRequest参数，请查看相关 API 文档
https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest


#### 返回值
RequestTask

网络请求任务对象

DownloadTask.abort()

中断请求任务

#### 示例：

```javascript
var requestTask = qg.request({
    url: 'http://www.example.com',
    success: function (msg) {
        console.log("request success " + msg)
    },
    fail: function (msg) {
        console.log("request fail, errMsg =" + msg["errMsg"])
    }
});
requestTask.abort();
```