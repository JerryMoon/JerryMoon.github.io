# vivo小游戏打包工具说明
---

## vivo小游戏开发者工具[qgame-toolkit](https://www.npmjs.com/package/qgame-toolkit)

1.全局安装qgame-toolkit

```
npm install -g qgame-toolkit
```

2.新建示例工程，方便开发者快速上手

```
qgame init <project-name>
```

3.安装npm依赖

```
cd <project-name>

npm install
```

4.构建项目

```
npm run build
```

或者

```
npm run watch
```

5.起本地服务

```
npm run server
```

6.构建发布版本的rpk包

```
npm run release
```

## 如何生成release签名

通过openssl命令等工具生成签名文件private.pem、certificate.pem，例如：

```
openssl req -newkey rsa:2048 -nodes -keyout private.pem -x509 -days 3650 -out certificate.pem
```

在vivo小游戏工程的sign目录下创建release目录，将私钥文件private.pem和证书文件certificate.pem拷贝进去。