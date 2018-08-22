# 账号
---

### 账号服务

## 接口定义

### qg.authorize(Object object)

账号授权登录

#### 参数：

| 参数名      | 类型       | 必填   | 说明       |
| -------- | -------- | ---- | -------- |
| type | string | 是    | 授权码模式为code，简化模式为token。|
| redirectUri | Uri | 否    | 重定向URI。 |
| scope | string | 否    | 申请的权限范围，目前只支持一种scope，假如不填则getProfile只返回openId。scope.baseProfile：获取用户基本信息。 |
| state | string | 否    | 可以指定任意值，认证服务器会原封不动地返回这个值。 |
| success | Function | 否    | 成功回调。 |
| fail | Function | 否    | 失败回调。 |
| complete | Function | 否    | 执行结束后的回调。 |

#### success返回值：
| 参数名      | 类型      | 说明       |
| -------- | -------- | -------- |
| state | string  | 请求时同字段指定的任意值。 |
| code | string  | 授权码模式下可用，返回的授权码。 |
| accessToken | string  | 简化模式下可用，返回的访问令牌。 |
| tokenType | string  | 简化模式下可用，访问令牌类型。 |
| expiresIn | number  | 简化模式下可用，访问令牌过期时间，单位为秒，如果通过其他方式设置，则此处可能为空。 |
| scope | string  | 简化模式下可用，实际权限范围，如果与申请一致，则此处可能为空。 |

#### fail返回错误代码：
| 错误码  | 说明       |
| -------- | -------- |
| 201 | 用户拒绝，获取帐号权限失败  |

#### 示例：

```javascript
        qg.authorize({
            type: "code",
            success: function (data) {
                qg.showToast({
                    message: "handling success, code: " + data.code
                })
            },
            fail: function (data, code) {
                qg.showToast({
                    message: "handling fail, fail code: " + code
                })
            }
        })
```

```javascript
        qg.authorize({
            type: "token",
            success: function (data) {
                that.token = data.accessToken
                qg.showToast({
                    message: "handling success, code: " + data.accessToken
                })
            },
            fail: function (data, code) {
                qg.showToast({
                    message: "handling fail, fail code: " + code
                })
            }
        })
```

### qg.getAccountProfile(Object object)

获得用户基本信息。

#### 参数：

| 参数名      | 类型       | 必填   | 说明       |
| -------- | -------- | ---- | -------- |
| token | string | 是    | 访问令牌。|
| success | Function | 否    | 成功回调。 |
| fail | Function | 否    | 失败回调。 |
| complete | Function | 否    | 执行结束后的回调。 |

#### success返回值：
| 参数名      | 类型      | 说明       |
| -------- | -------- | -------- |
| openid | string  | 用户的openid，可能为空。 |
| id | string  | 用户的user id，可能为空。 |
| unionid | string  | 用户在开放平台上的唯一标示符。 |
| nickname | string  | 用户的昵称，可能为空。 |
| avatar | object  | 用户的头像图片地址，可能为空，按照分辨率组织，当只有一个分辨率时，可以使用default对应的图片地址。 |

#### 示例：

```javascript
        qg.getProfile({
          token: this.token,
          success: function(data){
            qg.showToast({
              message: "nickname: " + data.nickname
            })
          },
          fail: function(data, code) {
            qg.showToast({
              message: "handling fail, code=" + code
            })
          }
        })
```





