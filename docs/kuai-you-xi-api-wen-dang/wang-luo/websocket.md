

# WebSocket


## 接口定义

### 方法

### qg.createWebSocket(OBJECT)

创建websocket实例

#### 参数：

| 参数名      | 类型       | 必填   | 说明                                       |
| -------- | -------- | ---- | ---------------------------------------- |
| url  | String     | 是    | 请求url， 必须是wss或ws协议 |
| protocols | StringArray | 否    | 子协议组                    |

#### 示例：

```javascript
this.ws =qg.createWebSocket({
  url:'wss://echo.websocket.org',
  protocols:['protocols1']
})
```
### ws.send(String)

使用ws对象发送消息

#### 示例：

```javascript
this.ws.send('message');
```

### ws.close()

关闭连接

#### 示例：

```javascript
this.ws.close()
```
### 事件

### ws.onopen(OBJECT)

监听websocket连接打开的状态。

#### 参数：

| 参数名   | 类型     | 必填 | 说明         |
| -------- | -------- | ---- | ------------ |
| callback | Function | 否   | 打开连接回调 |


#### 示例：

```javascript
this.ws.onopen = function(evt){
  log('Network onopen...');
};
```

### ws.onmessage(OBJECT)

消息事件的监听，用于接收服务端发来的message 。

#### OBJECT参数：

| 参数名   | 类型     | 必填 | 说明                   |
| -------- | -------- | ---- | ---------------------- |
| callback | Function | 否   | 服务器返回消息事件回调 |

#### callback参数：

| 参数名 | 类型   | 说明               |
| ------ | ------ | ------------------ |
| data   | String | 监听器接收到的消息 |


#### 示例：

```javascript
ws.onmessage = function (data) {
  console.log(`message is ${data.data}`)
}
```

### ws.onclose(OBJECT)

关闭连接的监听。

#### OBJECT参数：

| 参数名   | 类型     | 必填 | 说明               |
| -------- | -------- | ---- | ------------------ |
| callback | Function | 否   | 关闭连接事件回调。 |

#### callback参数：

| 参数名   | 类型    | 说明                     |
| -------- | ------- | ------------------------ |
| code     | Number  | 服务器返回关闭的状态码。 |
| reason   | String  | 服务器返回的关闭原因。   |
| wasClean | Boolean | 是否正常关闭。           |

#### 示例：

```javascript
ws.onclose = function (data) {
  console.log(`onclose:data.code = ${data.code}, data.reason = ${data.reason}, data.wasClean = ${data.wasClean}`)
}
```

### ws.onerror(OBJECT)

错误事件的监听器。

#### OBJECT参数：

| 参数名   | 类型     | 必填 | 说明         |
| -------- | -------- | ---- | ------------ |
| callback | Function | 否   | 连接错误回调 |
#### callback参数：

| 参数名 | 类型   | 说明                 |
| ------ | ------ | -------------------- |
| data   | String | 监听器接收到的消息。 |


#### 示例：

```javascript
ws.onerror = function (data) {
  console.log(`onerror data.data = ${data.data}`)
}
```