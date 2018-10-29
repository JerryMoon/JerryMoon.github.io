# 字体
---
## 接口定义

### string qg.loadFont(string familyName, string path)

加载自定义字体文件

#### 参数：

| 参数名      | 类型       | 必填   | 说明       |
| -------- | -------- | ---- | -------- |
| familyName | String | 是    | family name     |
| path | String | 是    | 字体文件路径     |

#### 返回值：
如果加载字体成功，则返回字体 family 值，否则返回 null。

#### 示例：

```javascript
const filePath = '/WanYongBoWenTi-2.ttf'
const fn = qg.loadFont('familyName', "url('" + filePath + "')")
console.log('---fn=', fn);
```



