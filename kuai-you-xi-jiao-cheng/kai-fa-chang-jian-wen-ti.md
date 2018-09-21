# vivo快游戏常见问题汇总
---

###Q1：快游戏如何基于h5游戏开发?
游戏如果是按照h5标准开发的适配难度不大，通过cocos creator导出vivo快游戏
理论上，没有其他功能，只需要接账号和支付，相关api可参看-快游戏API文档


###Q2：有没有游戏引擎导出快游戏的插件？
我们这边有导出快游戏的插件，请参考快游戏教程-IDE接入说明-cocos creator接入说明


###Q3：目前有支持哪些游戏引擎？
目前支持cocos creator引擎开发
后续考虑接入其他引擎服务商


###Q4：快游戏运行不起来，调试有问题，怎么办？
**首先确认环境问题：**
1.是否vivo手机，如果不是vivo手机，可能会不支持
2.是否安装最新的调试器apk和快游戏引擎apk，注意是要安装两个app到vivo手机上
3.是否调试时，手机和电脑处于同一个wifi网络情况下，如果网络问题解决不了，可以使用调试器的本地打开功能，把打包好的游戏rpk文件导入到sd卡进行打开

**最新的工具和调试器下载地址：**
https://jerrymoon.github.io/kuai-you-xi-jiao-cheng/xia-zai-yu-geng-xin.html 


###Q5：如果使用非推荐的creator版本（2.0及以下），可以正常运行么？
包可能无法正常运行，要评估下，当前低版本的creator的代码，升级到creator2.0+要做的改动
以下是官方的迁移指南：
http://docs.cocos.com/creator/manual/zh/release-notes/upgrade-guide-v2.0.html 


###Q6：账号和支付如何接入“
首先评估，是否需要接入账号、支付（**如果不需要直接跳过以下内容**）
CP厂商接入vivo账号、支付系统流程
 ####1.开发者平台地址注册
 https://dev.vivo.com.cn/home 如果有营业执照等，则用对应的信息注册。如果暂时不能提供，则临时先用微信沟通截图作为凭证代替营业执照法人信息等，后续补充相关正式的证件信息。
 ####2.对接账号支付系统
 https://dev.vivo.com.cn/distribute/quickGame 申请添加快游戏
 
快游戏账号服务器对接文档：
https://dev.vivo.com.cn/documentCenter/doc/143
快游戏支付服务器对接文档：
https://dev.vivo.com.cn/documentCenter/doc/144

PS：如果接入账号，需要提供账号服务器的回调地址
（code复杂模式需要，token简化模式登录不需要服务器对接）


###Q7：cocos2d-js开发的游戏 能转成快游戏么？
http://docs.cocos.com/creator/manual/zh/getting-started/cocos2d-x-guide.html 这里是相关的文档

cocos2d-js 在三年前已经进入维护阶段了，不再添加新功能，所以 runtime 是不支持 cocos2d-js 的。


###Q8.目前不能使用的功能或者不支持的写法有哪些？
在调试中发现，平台由于安全原因把new Function 和eval 禁用了，js里不要使用这两个api，否则会报错；
其他的报错，根据调试器报错弹框，查看详细就能定位到具体报错行数。

###Q9.接入评估，是否要仔细评估快游戏API文档?
快游戏的API文档，可以暂时不需要仔细研读，如果您现在是用了creator开发的纯h5游戏，直接按照操作指导里面的教程，接入插件，就可以直接导出了，然后进行一些适配的调试，就能跑起来。 
开发者如果用cocos creator引擎开发的话，应该只需要关注账号支付这些需要对接的功能API。
如果单纯用快游戏API，从零开始进行开发，那就要仔细阅读我们的开发文档了。
建议使用游戏引擎进行开发，可以相对快速的开发出游戏产品。

###Q10.如何支持屏幕适配？异形屏？
建议开发者使用vivo相关型号手机进行自检自测，保证各个页面能够全屏展示；

如果设备是异形屏，根据刘海高度改善布局，总体原则是背景充满屏幕，游戏内容避开刘海区域。
参考api接口（qg.getNotchHeight）
https://jerrymoon.github.io/kuai-you-xi-api-wen-dang/xi-tong-neng-li/she-bei-xin-xi.html

 

