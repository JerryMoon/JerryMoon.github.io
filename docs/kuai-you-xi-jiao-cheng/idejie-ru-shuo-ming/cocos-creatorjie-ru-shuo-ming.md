## cocos creator接入说明

### creator集成快游戏开发插件

[下载cocos creator快游戏插件runtime-packer](/kuai-you-xi-jiao-cheng/xia-zai-yu-geng-xin.md)，将解压后的runtime-packer文件夹放到cocos creator(需要2.0.2之上的版本，[点击下载](/kuai-you-xi-jiao-cheng/xia-zai-yu-geng-xin.md))编辑器安装路径下的 Resources/builtin 目录，重启creator即可。

### creator中添加release签名

在快游戏工程根目录中，添加build-templates/jsb-link目录，并在该目录中放置sign目录，在sign目录中放置release目录，在release目录中放置你的私钥文件private.pem和证书文件certificate.pem。
最终的目录结构如：build-templates/jsb-link/sign/release/certificate.pem，如下图：
![](/assets/g1M01DF38wKgcQlt-H6WALG1dAAG-8C1NA74174.png)


### creator导出快游戏项目

使用creator构建项目时，在构建UI界面，发布平台选择`VIVO 快游戏`，填写应用包名、应用名称、应用图标、应用版本名称、应用版本号、支持的最小引擎平台版本号（注意：请填写**1020**），这些信息为必填项。
构建完成后，点击发布路径后的"打开"按钮，发布路径下的qgame目录就是导出快游戏工程目录，如：默认发布路径是build，快游戏工程目录则为build/qgame。

#### 应用图标

在构建时，应用图标将会导出到快游戏的工程里，请确保填写的应用图标路径下的图片真实存在。如：填写的应用图标路径为/assets/image/logo.png，则在creator的资源管理器assets目录下需要存在image目录和logo.png图片。

#### 本地npm安装路径

本地npm安装路径是非必填项。填写的npm安装路径的目的是在creator构建导出可运行的快游戏rpk包，rpk包位于快游戏工程qgame下的dist目录里。如果不填写，则creator只会导出快游戏工程目录。

获取本地的npm的安装路径的命令：

```
which npm
```

在mac系统下，如果输出结果：/Users/yourname/.nvm/versions/node/v8.1.4/bin/npm，则本地npm安装路径需要填写为/Users/yourname/.nvm/versions/node/v8.1.4/bin

在windows系统下，如果输出结果：/c/Program Files/nodejs/npm，则本地npm安装路径需要填写为c:\Program Files\nodejs

#### 构建发布程序包

勾选构建发布程序包表示在creator导出可以直接发布的rpk包，但前提是需要填写本地npm安装路径和在creator中添加release签名。如果不勾选，则构建出用于测试的rpk包。