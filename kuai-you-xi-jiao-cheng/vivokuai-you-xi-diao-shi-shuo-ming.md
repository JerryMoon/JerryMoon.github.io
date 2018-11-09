# vivo小游戏调试说明
---

## 安装vivo小游戏调试器

在手机上安装vivo小游戏调试器：[下载](/kuai-you-xi-jiao-cheng/xia-zai-yu-geng-xin.md)

## 安装vivo小游戏引擎
在手机上安装vivo小游戏引擎：[下载](/kuai-you-xi-jiao-cheng/xia-zai-yu-geng-xin.md)

## 使用说明
###方法一
* 点击桌面“快应用调试器”
* 点击“扫码安装按钮”
* 利用[vivo小游戏打包工具](/kuai-you-xi-jiao-cheng/vivokuai-you-xi-da-bao-gong-ju-shuo-ming.md)命令“npm run server“生成二维码
* 扫描二维码，即可打开编译好的vivo小游戏

###方法二
* 将编译好的vivo小游戏rpk文件拷入手机SD卡中
* 点击桌面“快应用调试器”
* 点击“本地安装”
* 从手机SD中找到rpk文件，选择打开。

## chrome浏览器真机调试
具体参见：[chrome调试vivo小游戏代码说明](/kuai-you-xi-jiao-cheng/chromediao-shi-kuai-you-xi-dai-ma-shuo-ming.md)

## Q&A
1. 使用adb logcat -s jswrapper过滤js中的console.log（修改manifest里的log级别改为log）