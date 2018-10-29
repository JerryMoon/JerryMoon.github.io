# 录音

## 接口定义

### qg.startRecord(OBJECT)

开始录音

#### 参数：

| 参数名                   | 类型     | 必填 | 说明                                                         |
| ------------------------ | -------- | ---- | ------------------------------------------------------------ |
| duration        | Number   | 否   | 录音时长，单位为ms。如果duration为有效值将在达到指定值时停止录音 |
| sampleRate        | Number   | 否   | 采样率。不同的音频格式所支持的采样率范围不同。对于aac格式，默认设置为8000，建议使用 8000/16000/44100 |
| numberOfChannels  | Number   | 否   | 录音通道数，有效值 1/2                                       |
| encodeBitRate     | Number   | 否   | 编码码率。编码码率的取值与采样率和音频格式有关。对aac格式，建议按照下表中取值范围来选择编码码率 |
| format            | String   | 否   | 音频格式，有效值 3gpp/amr_nb/aac。缺省为3gpp                 |
| success                  | Function | 否   | 成功回调                                                     |
| fail                     | Function | 否   | 失败回调                                                     |
| complete                 | Function | 否   | 执行结束后的回调                                             |

##### aac格式采样率及码率建议值对应表：

| 采样率 | 编码码率       |
| ------ | -------------- |
| 8000   | 16000 ~ 48000  |
| 16000  | 24000 ~ 96000  |
| 44100  | 64000 ~ 320000 |

##### success返回值：

| 参数名 | 类型   | 说明                                   |
| ------ | ------ | -------------------------------------- |
| uri    | String | 录音文件的存储路径，在应用的缓存目录中 |

##### fail返回错误代码

| 错误码 | 说明                           |
| ------ | ------------------------------ |
| 201    | 用户拒绝授权，获取录音权限失败 |

#### 示例：

```javascript
qg.startRecord({
  duration: 10000,
  sampleRate: 8000,
  numberOfChannels: 1,
  encodeBitRate: 16000,
  format: 'aac',
  success: function (data) {
    console.log(`handling success: ${data.uri}`)
  },
  fail: function (data, code) {
    console.log(`handling fail, code = ${code}`)
  }
})
```

### qg.stopRecord(OBJECT)

停止录音

#### 参数：

无

#### 示例：

```javascript
qg.stopRecord()
```