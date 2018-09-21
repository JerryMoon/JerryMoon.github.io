# 数据请求

## 接口定义

### qg.request(OBJECT)

发起网络请求

#### 参数：

| 参数名       | 类型     | 必填 | 说明                                                         |
| ------------ | -------- | ---- | ------------------------------------------------------------ |
| url          | String   | 是   | 资源url                                                      |
| header       | Object   | 否   | 请求的header |
| method       | String   | 否   | HTTP 请求方法，默认为GET                               |
| data | String    | 否   | 请求的参数                                |
| dataType | String    | 否   | 返回的数据格式，可以是：json、arraybuffer、string，默认为 json       |
| success      | Function | 否   | 成功返回的回调函数                                           |
| fail         | Function | 否   | 失败的回调函数                                               |
| complete     | Function | 否   | 结束的回调函数（调用成功、失败都会执行）    

##### method 的合法值：

| 值       |  说明                                                         |
| ------------ | -------- | ---- | ------------------------------------------------------------ |
| GET          | HTTP 请求 GET           
| HEAD          | HTTP 请求 HEAD         
| POST          | HTTP 请求 POST         
| PUT          | HTTP 请求 PUT         
| DELETE          | HTTP 请求 DELETE          
| TRACE          | HTTP 请求 TRACE      
| DELETE          | HTTP 请求 DELETE      
| CONNECT          | HTTP 请求 CONNECT                                                

##### dataType 的合法值：

| 值       |  说明                                                         |
| ------------ | -------- | ---- | ------------------------------------------------------------ |
| json          | 返回的数据为 JSON，返回后会对返回的数据进行一次 JSON.parse           
| arraybuffer          | 返回的数据为 ArrayBuffer         
| string          | 返回的数据为 String     

##### success 回调函数：

参数 Object ret

| 属性      | 类型     | 说明                                                         |
| ------------ | -------- | ---- | ------------------------------------------------------------ |
| data          | string/Object/Arraybuffer   | 返回的数据
| header          | Object   | 返回的 HTTP Response Header
| statusCode          | number   | 开发者服务器返回的 HTTP 状态码

##### fail 回调函数：

| 参数名      | 类型     | 说明                                                         |
| ------------ | -------- | ---- | ------------------------------------------------------------ |
| error          | string   | 返回的数据
| code          | number   | 返回的错误码



#### 返回值
RequestTask

网络请求任务对象

DownloadTask.abort()

中断请求任务

#### 示例：

```javascript
var requestTask = qg.request({
    url: "http://api.vivo.xyz/mockApi/mock/api/user/isLogin.do",
    dataType: 'text', // dataType可取值：string, json, arraybuffer, 表示success的回调参数对象ret的data属性是分别是：String 、Object 、ArrayBuffer类型
    success: function(ret) {
        qg.showToast({
            message: " request success " + ret.data
        });
    },
    fail: function(error, code) {
        qg.showToast({
            message: " request fail, errMsg =" + error
        });
    }
});

requestTask.abort();
```