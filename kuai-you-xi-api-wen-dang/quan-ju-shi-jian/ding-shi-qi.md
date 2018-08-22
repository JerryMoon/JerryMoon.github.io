# 定时器

------

## setTimeout(function callback, number delay, any rest)
设定一个定时器，在定时到期以后执行注册的回调函数

触发较短时间震动，持续15ms

#### 参数
function callback
回调函数

number delay
延迟的时间，函数的调用会在该延迟之后发生，单位 ms。

any rest
param1, param2, ..., paramN 等附加参数，它们会作为参数传递给回调函数。

#### 返回值
number
定时器的编号。这个值可以传递给 clearTimeout 来取消该定时。


#### 示例

```js
setTimeout(function (){
    // do something
},1000);
```

### clearTimeout(number timeoutID)

可取消由 setTimeout() 方法设置的定时器。

#### 参数

number timeoutID
要取消的定时器的 ID

### setInterval(function callback, number delay, any rest)
设定一个定时器，按照指定的周期（以毫秒计）来执行注册的回调函数

#### 参数
function callback
回调函数

number delay
执行回调函数之间的时间间隔，单位 ms。

any rest
param1, param2, ..., paramN 等附加参数，它们会作为参数传递给回调函数。

#### 返回值
number
定时器的编号。这个值可以传递给 clearInterval 来取消该定时。


### clearInterval(number intervalID)
可取消由 setInterval() 方法设置的定时器。

#### 参数
number intervalID
要取消的定时器的 ID





