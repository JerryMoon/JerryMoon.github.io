```javascript

var uiUtil = require("ui_util");
let ui = require("ui");

let pageName = "ui_storage_data"
let global_tag = "feature_test  " + pageName + " ==>";


function LogI(content) {
    console.log(global_tag + content);
}

function makeToast (content) {
    qg.showToast({
        message : content,
    });
}

let keyA = 'keyA'
let keyB = 'keyB'

module.exports = cc.Class({

    extends: require("ui_base"),

    properties: {
        sv_tests: cc.ScrollView,
    },

    writeData() {       
        let fName = " setStorage ";
        LogI(fName);
        qg.setStorage({
            key: keyA,
            value: 'V1',
            success: function (data) {
                LogI(fName + `handling success: ${JSON.stringify(data)}`)
                makeToast(keyA + '写入成功');
            },
            fail: function (data, code) {
                LogI(fName + `handling fail, code = ${code}`)
                makeToast(keyA + '写入成功');
            }
          });
    },

    readData() {
        let fName = " getStorage ";
        LogI(fName);
        qg.getStorage({
            key: keyA,
            success: function (data) {
                LogI(fName + `handling success: ${JSON.stringify(data)}`)
                makeToast(`${keyA}=${data}`);
            },
            fail: function (data, code) {
                LogI(fName + `handling fail, code = ${code}`)
                makeToast(`${keyA}读取失败，code = ${code}`);
            }
          });
    },

    deleteData() {
        let fName = " deleteStorage ";
        LogI(fName);
        qg.deleteStorage({
            key: keyA,
            success: function (data) {
                LogI(fName + `handling success: ${JSON.stringify(data)}`)
                makeToast(`删除${keyA}, ${data}`);
            },
            fail: function (data, code) {
                LogI(fName +`handling fail, code = ${code}`)
                makeToast(`删除${keyA}失败，code = ${code}`);
            }
          });
    },

    clearAllData() {
        let fName = " clearStorage ";
        LogI(fName);
        qg.clearStorage({
            success: function (data) {
                LogI(fName + `handling success: ${JSON.stringify(data)}`)
                makeToast(`所有数据删除成功`);
            },
            fail: function (data, code) {
                LogI(fName + `handling fail, code = ${code}`)
                makeToast(`删除失败，code = ${code}`);
            }
          });
    },

    writeDataSync() {
        let fName = " setStorageSync ";
        LogI(fName);
        var result = qg.setStorageSync({
            key: keyB,
            value: 'V2'
        });
        LogI(fName + " result:" + result);
        makeToast(`${keyB}写入成功`);
    },

    getSync() {
        let fName = " getStorageSync ";
        LogI(fName);
        var result = qg.getStorageSync({
            key: keyB
        });
        LogI(fName + "result:" + result);
        makeToast(keyB + '=' + result);
    },

    deleteSync() {
        let fName = " deleteStorageSync ";
        LogI(fName);
        var result = qg.deleteStorageSync({
            key: keyB
        });
        LogI(fName + "result:" + result);
        makeToast('删除'+ keyB + " "+ result);
    },

    clearSync() {
        let fName = " clearStorageSync ";
        LogI(fName);
        var result = qg.clearStorageSync();
        LogI(fName + "result:" + result);
        makeToast('删除数据' + result);
    },



});

```
