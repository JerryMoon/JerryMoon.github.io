# vivo快游戏常见问题汇总
---

###Q1：快游戏如何基于h5游戏开发?
游戏如果是按照h5标准开发的适配难度不大，通过cocos creator导出vivo快游戏
理论上，没有其他功能，只需要接账号和支付，具体可参加快游戏API文档


###Q2：有没有游戏引擎导出快游戏的插件？
我们这边有导出快游戏的插件，请参考快游戏教程-IDE接入说明-cocos creator接入说明


###Q3：目前有支持哪些游戏引擎？
目前支持cocos creator引擎开发
后续考虑接入其他引擎服务商


###Q4：快游戏支持的creator版本是多少？
**creator 2.0.2版本：
**http://47.98.62.68/cocos-runtime-demo/creator/CocosCreator_v2.0.2-alpha.1.7z 


###Q5：如果使用非推荐的creator版本，可以正常运行么？
包可能无法正常运行，要评估下，当前低版本的creator的代码，升级到creator2.0+要做的改动
以下是官方的迁移指南：
http://docs.cocos.com/creator/manual/zh/release-notes/upgrade-guide-v2.0.html 


###Q6：账号和支付如何接入“
首先评估，是否需要接入账号、支付（**如果不需要直接调过以下内容**）
CP厂商接入vivo账号、支付系统流程
 ####1.开发者平台地址注册：
 https://dev.vivo.com.cn/home 如果有营业执照等，则用对应的信息注册。如果暂时不能提供，则临时先用微信沟通截图作为凭证代替营业执照法人信息等，后续补充相关正式的证件信息。
 ####2.对接账号系统走内部流程，内部申请。
 （开发者目前只需要把vivo开发者账号注册好，提供以下材料即可，剩余工作vivo内部处理，完成后，拿到client_id等信息进行联调）
 
 开发者需要提供以下材料：
 快游戏名称，快游戏包名，开发者平台账号，游戏icon（icon标准参见下图），是否接入账号，是否接入支付
 ![](/assets/8c8a47af-da25-46b9-bc98-db26ae5c1a2f.png)
 
 PS：如果接入账号，需要提供账号服务器的回调地址（code复杂模式需要，token简化模式登录不需要服务器对接）
授权成功vivo服务器会把返回code加在回调地址，开发者服务器后台获取这个code去请求accesstoken，然后根据accesstoken获取账户信息

#### 3.核对后给开发者发送快游戏分配的client_id和client_secret
 ####4.开发者完善注册信息
 ####5.核对client_id和client_secret是否同步成功，是否可用并分配静默授权


###Q7：cocos2d-js开发的游戏 能转成快游戏么？
http://docs.cocos.com/creator/manual/zh/getting-started/cocos2d-x-guide.html 这里是相关的文档

cocos2d-js 在三年前已经进入维护阶段了，不再添加新功能，所以 runtime 是不支持 cocos2d-js 的。


###Q8.目前不能使用的功能或者不支持的写法有哪些？
在调试中发现，平台由于安全原因把new Function 和eval 禁用了，js里不要使用这两个api，否则会报错

###Q9.接入评估，是否要仔细评估快游戏API文档?
快游戏的API文档，可以暂时不需要仔细研读，如果你们现有是用了creator开发的纯h5游戏，直接按照操作指导里面的教程，接入插件，就可以直接导出了，然后进行一些适配的调试，就能跑起来。 
开发者如果用cocos creator引擎开发的话，应该只需要关注账号支付这些需要对接的功能API。
如果单纯用快游戏API，从零开始进行开发，那就要仔细阅读我们的开发文档了。
建议使用游戏引擎进行开发，可以相对快速的开发出游戏产品。

 

