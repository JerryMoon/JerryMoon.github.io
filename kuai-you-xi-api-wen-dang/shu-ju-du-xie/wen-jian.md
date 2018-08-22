# 文件存储

---

## 接口定义

### qg.accessFile\(OBJECT\)

判断文件/目录是否存在，同步方法，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | String | 是 | 文件的uri，不能是tmp类型的uri |

##### 同步返回值：

| 含义 | 类型 | 内容 |
| --- | --- | --- |
| 文件/目录存在 | String | true |
| 文件/目录不存在 | String | false |
| 参数错误 | int | 202 |
| I/O错误 | int | 300 |

#### 示例：

```javascript
var res = qg.accessFile({
    uri: 'internal://cache/path/to/file'
})
console.log(`handling result： ${res}`)
```

### qg.copyFile\(OBJECT\)

将源文件复制一份并存储到指定位置，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcUri | String | 是 | 源文件的uri |
| dstUri | String | 是 | 目标文件的uri，不能是应用资源路径和tmp类型的uri |
| success | Function | 否 | 成功回调，返回目标文件的uri |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### fail返回错误代码：

| 错误码 | 说明 |
| --- | --- |
| 202 | 参数错误 |
| 300 | I/O错误 |

#### 示例：

```javascript
qg.copyFile({
    srcUri: 'internal://cache/path/to/file',
    dstUri: 'internal://files/path/to/file',
    success: function (uri) {
        console.log(`copy success: ${uri}`)
    },
    fail: function (data, code) {
        console.log(`handling fail, code = ${code}`)
    }
})
```

### qg.moveFile\(OBJECT\)

将源文件移动到指定位置，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcUri | String | 是 | 源文件的uri，不能是应用资源路径和tmp类型的uri |
| dstUri | String | 是 | 目标文件的uri，不能是应用资源路径和tmp类型的uri |
| success | Function | 否 | 成功回调，返回目标文件的uri |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### fail返回错误代码：

| 错误码 | 说明 |
| --- | --- |
| 202 | 参数错误 |
| 300 | I/O错误 |

#### 示例：

```javascript
qg.moveFile({
    srcUri: 'internal://cache/path/to/file',
    dstUri: 'internal://files/path/to/file',
    success: function (uri) {
        console.log(`move success: ${uri}`)
    },
    fail: function (data, code) {
        console.log(`handling fail, code = ${code}`)
    }
})
```

### qg.getFileInfo\(OBJECT\)

获取本地文件的文件信息，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | String | 是 | 文件的uri，不能是tmp类型的uri |
| success | Function | 否 | 成功回调，返回{uri:'file1', length:123456, lastModifiedTime:1233456} |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### success返回值：

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| uri | String | 文件的uri，该uri可以被其他api |
| length | Number | 文件大小，单位B |
| lastModifiedTime | Number | 文件的保存是的时间戳，从1970/01/01 08:00:00 到当前时间的秒数 |

##### fail返回错误代码：

| 错误码 | 说明 |
| --- | --- |
| 202 | 参数错误 |
| 300 | I/O错误 |

#### 示例：

```javascript
qg.getFileInfo({
    uri: 'internal://files/path/to/file',
    success: function (data) {
        console.log(data.uri);
        console.log(data.length);
        console.log(data.lastModifiedTime);
    },
    fail: function (data, code) {
        console.log(`handling fail, code = ${code}`)
    }
})
```

### qg.listDir\(OBJECT\)

获取指定目录下的文件列表，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | String | 是 | 目录uri，不能是文件的uri，也不能是tmp类型的uri |
| success | Function | 否 | 成功回调，返回{fileList:\[{uri:'file1',lastModifiedTime:1234456, length:123456} ...\]} |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### success返回值：

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| fileList | Array | 文件列表，每个文件的格式为{uri:'file1',lastModifiedTime:1234456, length:123456} |

###### 每个文件的元信息：

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| uri | String | 文件的uri，该uri可以被其他api访问 |
| length | Number | 文件大小，单位B |
| lastModifiedTime | Number | 文件的保存是的时间戳，从 1970/01/01 00:00:00 GMT 到当前时间的毫秒数 |

##### fail返回错误代码：

| 错误码 | 说明 |
| --- | --- |
| 202 | 参数错误 |
| 300 | I/O错误 |

#### 示例：

```javascript
qg.listDir({
    uri: 'internal://files/movies/',
    success: function (data) {
        console.log(data.fileList)
    },
    fail: function (data, code) {
        console.log(`handling fail, code = ${code}`)
    }
})
```

### qg.deleteFile\(OBJECT\)

删除本地存储的文件，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | String | 是 | 需要删除的文件uri，不能是应用资源路径和tmp类型的uri |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### fail返回错误代码：

| 错误码 | 说明 |
| --- | --- |
| 202 | 参数错误 |
| 300 | I/O错误 |

#### 示例：

```javascript
qg.deleteFile({
    uri: 'internal://files/path/to/file',
    success: function (data) {
        console.log('handling success')
    },
    fail: function (data, code) {
        console.log(`handling fail, code = ${code}`)
    }
})
```

### qg.readFile\(OBJECT\)

读取本地文件内容，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | String | 是 | 需要读取的本地文件uri，不能是tmp类型的uri |
| encoding | String | 否 | 编码格式，默认UTF-8 |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### success返回值：

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| text | String | 读取的文本 |

##### fail返回错误代码：

| 错误码 | 说明 |
| --- | --- |
| 202 | 参数错误 |
| 300 | I/O错误 |
| 301 | 文件不存在 |

#### 示例：

```javascript
qg.readFile({
    uri: 'internal://files/work/demo.txt',
    success: function (data) {
        console.log('text: '+ data.text)
    },
    fail: function (data, code) {
        console.log(`handling fail, code = ${code}`)
    }
})
```

### qg.writeFile\(OBJECT\)

写文本到本地文件，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | String | 是 | 需要写入的文件uri，不能是应用资源路径和tmp类型的uri |
| text | String | 是 | 需要写入的字符串 |
| encoding | String | 否 | 编码格式，默认UTF-8 |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### fail返回错误代码：

| 错误码 | 说明 |
| --- | --- |
| 202 | 参数错误 |
| 300 | I/O错误 |

#### 示例：

```javascript
qg.writeFile({
    uri: 'internal://files/path/to/file',
    success: function (uri) {
        console.log('handling success: ${uri}')
    },
    fail: function (data, code) {
        console.log(`handling fail, code = ${code}`)
    }
})
```

### qg.appendFile\(OBJECT\)

在文件结尾追加内容，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | String | 是 | 需要追加的文件uri，不能是应用资源路径和tmp类型的uri |
| text | String | 是 | 需要写入的字符串 |
| encoding | String | 否 | 编码格式，默认UTF-8 |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### fail返回错误代码：

| 错误码 | 说明 |
| --- | --- |
| 202 | 参数错误 |
| 300 | I/O错误 |

#### 示例：

```javascript
qg.appendFile({
    uri: 'internal://files/path/to/file',
    success: function (uri) {
        console.log('handling success: ${uri}')
    },
    fail: function (data, code) {
        console.log(`handling fail, code = ${code}`)
    }
})
```

### qg.mkdir\(OBJECT\)

创建目录，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | String | 是 | 需要创建的目录uri，不能是应用资源路径和tmp类型的uri |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### fail返回错误代码：

| 错误码 | 说明 |
| --- | --- |
| 202 | 参数错误 |
| 300 | I/O错误 |

#### 示例：

```javascript
qg.mkdir({
    uri: 'internal://files/path/',
    success: function (uri) {
        console.log('handling success: ${uri}')
    },
    fail: function (data, code) {
        console.log(`handling fail, code = ${code}`)
    }
})
```

### qg.rmdir\(OBJECT\)

删除目录，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | String | 是 | 需要删除的目录uri，不能是应用资源路径和tmp类型的uri |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### fail返回错误代码：

| 错误码 | 说明 |
| --- | --- |
| 202 | 参数错误 |
| 300 | I/O错误 |

#### 示例：

```javascript
qg.rmdir({
    uri: 'internal://files/path/',
    success: function (uri) {
        console.log('handling success: ${uri}')
    },
    fail: function (data, code) {
        console.log(`handling fail, code = ${code}`)
    }
})
```

### qg.isDirectory\(OBJECT\)

判断是否为目录，同步接口，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | String | 是 | 需要检查的uri，不能是tmp类型的uri |

##### 同步返回值：

| 含义 | 类型 | 内容 |
| --- | --- | --- |
| 是目录 | String | true |
| 不是目录 | String | false |
| 参数错误 | int | 202 |
| I/O错误 | int | 300 |

#### 示例：

```javascript
var res = qg.isDirectory({
    uri: 'internal://files/path/'
})
console.log(`handling result： ${res}`)
```

### qg.isFile\(OBJECT\)

判断是否为文件，同步接口，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | String | 是 | 需要检查的uri，不能是tmp类型的uri |

##### 同步返回值：

| 含义 | 类型 | 内容 |
| --- | --- | --- |
| 是目录 | String | true |
| 不是目录 | String | false |
| 参数错误 | int | 202 |
| I/O错误 | int | 300 |

#### 示例：

```javascript
var res = qg.isFile({
    uri: 'internal://files/path/'
})
console.log(`handling result： ${res}`)
```

### qg.renameFile\(OBJECT\)

重命名文件文件，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcUri | String | 是 | 源文件的uri，不能是应用资源路径和tmp类型的uri |
| dstUri | String | 是 | 目标文件的uri，不能是应用资源路径和tmp类型的uri |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### fail返回错误代码：

| 错误码 | 说明 |
| --- | --- |
| 202 | 参数错误 |
| 300 | I/O错误 |

#### 示例：

```javascript
qg.renameFile({
    srcUri: 'internal://cache/path/to/file',
    dstUri: 'internal://files/path/to/file',
    success: function (uri) {
        console.log('handling success: ${uri}')
    },
    fail: function (data, code) {
        console.log(`handling fail, code = ${code}`)
    }
})
```

### qg.unzipFile\(OBJECT\)

文件解压，接口中使用的URI描述请参考[文件组织](./wen-jian-zu-zhi.md)

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcUri | String | 是 | 源文件的uri，不能是tmp类型的uri |
| dstUri | String | 是 | 目标文件的uri，不能是应用资源路径和tmp类型的uri |
| success | Function | 否 | 成功回调 |
| fail | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### fail返回错误代码：

| 错误码 | 说明 |
| --- | --- |
| 202 | 参数错误 |
| 300 | I/O错误 |

#### 示例：

```javascript
qg.unzipFile({
    srcUri: 'internal://cache/path/to/file',
    dstUri: 'internal://files/path/to/',
    success: function (uri) {
        console.log('handling success: ${uri}')
    },
    fail: function (data, code) {
        console.log(`handling fail, code = ${code}`)
    }
})
```



