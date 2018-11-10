```javascript

import md5 from 'md5'
var res = require("resource");
var uiUtil = require("ui_util");

module.exports = cc.Class({
    extends: require("ui_base"),

    properties: {
        sv_tests: cc.ScrollView,
        pay_btn: cc.Button,
        pay_text: cc.Label,
    },

    onLoad() {
        this._super();
        this.pay_text.enableWrapText = true;
        this.pay_btn.node.on('click', this.useXm, this);
    },

    getSign: function(params) {
        var signStr = '';
        var signKey = '0396bc43e7e6cd77524f55d657d676c1';
        var keys = Object.keys(params).sort();
        keys.forEach(function (k) {
            signStr += k + '=' + params[k] + '&';
        });
  
        signStr += md5(signKey).toLowerCase();
        return md5(signStr).toLowerCase();
      },

    getOrderInfo(callback) {
        function leftpad(num) {
          return ("00" + num).substr(("" + num).length);
        }
  
        function currentTime() {
          var now = new Date();
          return now.getFullYear() + leftpad(now.getMonth() + 1) + leftpad(now.getDate()) + leftpad(now.getHours()) + leftpad(now.getMinutes()) + leftpad(now.getSeconds())
        }
  
        function getOrderNo(len) {
            var no = '';
            for(var i = 0; i < len; i++) {
                no += Math.floor(Math.random() * 10);
            }
            return no;
        }
  
        var params = {
          packageName: 'com.hybrid.demo.sample',
          cpOrderNumber: getOrderNo(16),
          notifyUrl: 'http://113.98.231.125:8051/vcoin/notifyStubAction',
          orderTime: currentTime(),
          orderAmount: '0.01',
          orderDesc: 'test',
          orderTitle: 'test',
          version: '1.0.0'
        }
        params.signature = this.getSign(params);
        params.signMethod = 'MD5';
  
        this.signature = JSON.stringify(params)
        this.pay_text.string = this.signature;
        console.log("this.signature = " + this.signature);
  
        qg.request({
          method: 'POST',
          url: 'https://pay.vivo.com.cn/vivopay/order/request',
          data: params,
          responseType: 'json',
          success: function(res) {
              callback(res.data);
          },
          fail: function() {
          }
        })
      },

    useXm() {
          this.getOrderInfo(function(res) {
            qg.showToast({
                message: "orderInfo： " + JSON.stringify(res)
              })
      
              qg.pay({
                orderInfo: res,
                success: function(ret) {
                    qg.showToast({
                    message: "支付成功：" + JSON.stringify(ret)
                  })
                },
                fail: function (erromsg, errocode) {
                    qg.showToast({
                    message: "支付失败：" + errocode + ': ' + erromsg
                  })
                },
                cancel: function(){
                  qg.showToast({
                    message: "用户取消"
                  })
                }
              })  
          });
      }

});

```