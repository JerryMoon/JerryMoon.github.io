# 软键盘

---

## 接口定义

### qg.showKeyboard\(Object object\)

显示键盘

#### 参数：

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| defaultValue | String | 是 | 键盘输入框显示的默认值 |
| maxLength | Number | 是 | 键盘中文本的最大长度 |
| multiple | Boolean | 是 | 是否为多行输入 |
| confirmHold | Boolean | 是 | 当点击完成时键盘是否收起 |
| confirmType | String | 是 | 键盘右下角confirm按钮类型，只影响按钮的文本内容 |
| success | Function | 否 | 成功回调 |
| cancel | Function | 否 | 失败回调 |
| complete | Function | 否 | 执行结束后的回调 |

##### **confirmType 的合法值**

| 值 | 说明 |
| :--- | :--- |
| done | 完成 |
| next | 下一个 |
| search | 搜索 |
| go | 前往 |
| send | 发送 |

#### 示例：

```js
qg.showKeyboard({
    defaultValue:"快游戏",
    maxLength : 500,
    multiple:true,
    confirmHold:false,
    confirmType :"done"
})
```

### qg.onKeyboardInput\(function callback\)

监听键盘输入

#### 参数

function callback  
监听事件的回调函数

##### 返回值：

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| value | String | 键盘输入的当前值 |

#### 示例：

```js
var func = function () {
  // do something
};
// 开始监听
qg.onKeyboardInput(func);
```

## qg.offKeyboardInput\(function callback\)

取消监听键盘输入

#### 参数

function callback  
监听事件的回调函数

#### 示例

```js
var func = function () {
  // do something
};
// 开始监听
qg.onKeyboardInput(func);
// 取消监听
qg.offKeyboardInput(func);
```

### qg.onKeyboardConfirm\(function callback\)

监听用户点击键盘 Confirm 按钮

#### 参数

function callback  
监听事件的回调函数

##### 返回值：

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| value | String | 键盘输入的当前值 |

#### 示例：

```js
var func = function () {
  // do something
};
// 开始监听
qg.onKeyboardConfirm(func);
```

## qg.offKeyboardConfirm\(function callback\)

取消监听用户点击键盘 Confirm 按钮

#### 参数

function callback  
监听事件的回调函数

#### 示例

```js
var func = function () {
  // do something
};
// 开始监听
qg.onKeyboardConfirm(func);
// 取消监听
qg.offKeyboardConfirm(func);
```

### qg.onKeyboardComplete\(function callback\)

监听键盘收起

#### 参数

function callback  
监听事件的回调函数

##### 返回值：

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| value | String | 键盘输入的当前值 |

#### 示例：

```js
var func = function () {
  // do something
};
// 开始监听
qg.onKeyboardComplete(func);
```

## qg.offKeyboardComplete\(function callback\)

取消监听键盘收起

#### 参数

function callback  
监听事件的回调函数

#### 示例

```js
var func = function () {
  // do something
};
// 开始监听
qg.onKeyboardComplete(func);
// 取消监听
qg.offKeyboardComplete(func);
```

### qg.hideKeyboard\(\)

隐藏键盘

#### 参数：

无

#### 示例：

```js
qg.hideKeyboard()
```



