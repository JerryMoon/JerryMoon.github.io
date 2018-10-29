# 定时器

------

## qg.onAudioInterruptionBegin(function callback)
监听音频因为受到系统占用而被中断开始，以下场景会触发此事件：闹钟、电话、FaceTime 通话、微信语音聊天、微信视频聊天。此事件触发后，快游戏内所有音频会暂停。

#### 参数
function callback
监听事件的回调函数

#### 示例
```javascript
var func = function () {
  // do something
};
// 开始监听
qg.onAudioInterruptionBegin(func);
```

## qg.offAudioInterruptionBegin(function callback)
取消监听音频因为受到系统占用而被中断开始。

#### 参数
function callback
监听事件的回调函数

#### 示例
```javascript
var func = function () {
  // do something
};
// 开始监听
qg.onAudioInterruptionBegin(func);
// 取消监听
qg.offAudioInterruptionBegin(func);
```

## qg.onAudioInterruptionEnd(function callback)
监听音频中断结束，在收到 onAudioInterruptionBegin 事件之后，快游戏内所有音频会暂停，收到此事件之后才可再次播放成功

#### 参数
function callback
监听事件的回调函数

#### 示例
```javascript
var func = function () {
  // do something
};
// 开始监听
qg.onAudioInterruptionEnd(func);
```
## qg.offAudioInterruptionEnd(function callback)
监听音频中断结束，在收到 onAudioInterruptionBegin 事件之后，快游戏内所有音频会暂停，收到此事件之后才可再次播放成功

#### 参数
function callback
监听事件的回调函数

#### 示例
```javascript
var func = function () {
  // do something
};
// 开始监听
qg.onAudioInterruptionEnd(func);

// 取消监听
qg.offAudioInterruptionEnd(func);
```








