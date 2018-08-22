# 音频

## 接口定义

### 方法

#### qg.createInnerAudioContext()

创建一个 InnerAudioContext 实例

##### 参数

无

##### 返回值

InnerAudioContext

##### 属性
string src
音频资源的地址

boolean loop
是否循环播放

number duration
当前音频的长度，单位 s。只有在当前有合法的 src 时返回

number currentTime
当前音频的播放位置，单位 s。只有在当前有合法的 src 时返回，时间不取整，保留小数点后 6 位

boolean paused
当前是是否暂停或停止状态，true 表示暂停或停止，false 表示正在播放

number volume
音量。范围 0~1。


##### 示例：

```javascript
var audioContext = qg.createInnerAudioContext()
```
#### InnerAudioContext.play()

播放音频

##### 参数

无

##### 示例：

```javascript
audioContext.play()
```

#### InnerAudioContext.seek(number position)

跳转到指定位置，单位 s

##### 参数

number position
跳转的时间

##### 示例：

```javascript
audioContext.seek(10)
```

#### InnerAudioContext.pause()

暂停播放音频

##### 参数

无

##### 示例：

```javascript
audioContext.pause()
```

#### InnerAudioContext.stop()

停止播放音频

##### 参数

无

##### 示例：

```javascript
audioContext.stop()
```

### 事件

| 名称           | 描述                                   |
| -------------- | -------------------------------------- |
| onEnded          | 监听播放结束时的回调                   |
| offEnded          | 取消监听播放结束时的回调                   |



#### 示例：

```javascript
var func = function () {
  console.log(`audio current time: ${audio.currentTime}`)
};
audioContext.onEnded(func);
audioContext.offEnded(func);
```