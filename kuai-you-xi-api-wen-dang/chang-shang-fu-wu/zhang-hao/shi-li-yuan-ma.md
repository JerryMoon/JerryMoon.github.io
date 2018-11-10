```javascript

var res = require("resource");
var uiUtil = require("ui_util");

module.exports = cc.Class({
    extends: require("ui_base"),

    properties: {
        sv_tests: cc.ScrollView,
        authorize_code_btn: cc.Button,
        authorize_token_btn: cc.Button,
        authorize_info_btn: cc.Button,
    },

    onLoad() {
        this._super();
        this.authorize_code_btn.node.on('click', this.authorize_code, this);
        this.authorize_token_btn.node.on('click', this.authorize_token, this);
        this.authorize_info_btn.node.on('click', this.getProfile, this);
    },

    authorize_code() {
        console.log("authorize_code");
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
    },

    authorize_token() {
        console.log("authorize_token");
        var that = this
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
    },

    getProfile() {
        if (!this.token) {
            qg.showToast({
            message: "请先使用简化模式获取token"
          })
          return;
        }
  
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
      }

});

```