```javascript

var uiUtil = require("ui_util");
let ui = require("ui");

let pageName = "ui_storage_file"
let global_tag = "feature_test  " + pageName + " ==> ";

let text_uri = 'internal://files/demo.txt';
let game_js_path = "/game.js";
let dst_copy_file = 'internal://files/copy/game.js';
let dst_move_file = 'internal://files/move/game.js';

let dst_dir ='internal://cache/dir'
let dst_list_dir ='internal://files/'
let dst_rename_file = 'internal://files/copy/game.js.copy';

let dst_read_write_file = 'internal://files/r_w/test.txt';

let src_zip_file = '/image/volley.zip'
let dst_zip_path = 'internal://files/zip'

function LogI(content) {
    console.log(global_tag + content);
}

function ab2str(buf) {
    var encodedString = String.fromCharCode.apply(null,  new Uint8Array(buf)),
    decodedString = decodeURIComponent(escape(encodedString));
    return decodedString;
  }

function makeToast (content) {
    qg.showToast({
        message : content,
    });
}

module.exports = cc.Class({
    extends: require("ui_base"),

    properties: {
        sv_tests: cc.ScrollView,
    },

    accessSync() {
        let fname = " accessFile ";
        LogI(fname);
        var result = qg.accessFile({
            uri: text_uri
        }); 
        LogI(fname + " result: " + result);
        makeToast("文件存在:" + result);

    },

    isDirSync() {
        let fname = " isDirSync ";
        LogI(fname);
        var result = qg.isDirectory({
            uri: game_js_path
        }); 
        LogI(fname + " result: " + result);
        makeToast("是目录:" + result);
    },

    isFileSync() {
        let fname = " isFileSync ";
        LogI(fname);
        var result = qg.isFile({
            uri: game_js_path
        }); 
        LogI(fname + " result: " + result);
        makeToast("是文件:" + result);
    },

    copy() {
        let fname = " copyFile ";
        LogI(fname);
        qg.copyFile({
            srcUri: game_js_path,
            dstUri: dst_copy_file,
            success: function (uri) {
                LogI(fname + `handling success: ${uri}`)
                makeToast("拷贝成功");
            },
            fail: function (data, code) {
                LogI(fname + `handling fail, code = ${code}, data = ${data}`)
                makeToast("拷贝失败");
            }
        })
    },

    move() {
        let fname = " moveFile ";
        LogI(fname);
        let src_file = dst_copy_file;        
        qg.moveFile({
            srcUri: src_file,
            dstUri: dst_move_file,
            success: function (uri) {
                LogI(fname + `handling success: ${uri}`)
                makeToast("move成功");
            },
            fail: function (data, code) {
                LogI(fname + `handling fail, code = ${code}, data = ${data}`)
                if ("false" === qg.accessFile({uri: src_file})) {
                    makeToast("move失败\n" + src_file + "不存在\n    先执行拷贝");
                    return
                }
                makeToast("move失败");
            }
        })
    },

    mkdir() {
        let fname = " mkdir ";
        LogI(fname);
        qg.mkdir({
            uri: dst_dir,
            success: function (uri) {
                LogI(fname + `handling success: ${uri}`)
                makeToast("目录创建成功");
            },
            fail: function (data, code) {
                LogI(fname + `handling fail, code = ${code}, data = ${data}`)
                makeToast("目录创建失败");
            }
        })
    },

    rmdir() {
        let fname = " rmdir ";
        LogI(fname);
        qg.rmdir({
            uri: dst_dir,
            success: function (uri) {
                LogI(fname + `handling success: ${uri}`)
                makeToast("目录删除成功");
            },
            fail: function (data, code) {
                LogI(fname + `handling fail, code = ${code}, data = ${data}`)
                if ("false" === qg.accessFile({uri: dst_dir})) {
                    makeToast("目录删除失败\n" + dst_dir + "不存在\n    先执行创建目录");
                    return
                }
                makeToast("目录删除失败");
            }
        })
    },

    list () {
        let fname = " listDir ";
        LogI(fname);
        qg.listDir({
            uri: dst_list_dir,
            success: function (data) {
                LogI(fname + `handling success: ${JSON.stringify(data)}`)
                makeToast("目录列举成功：" + JSON.stringify(data));
            },
            fail: function (data, code) {
                LogI(fname + `handling fail, code = ${code}, data = ${data}`)
                makeToast("目录列举失败");
            }
        })
    },

    rename () {
        let fname = " renameFile ";
        LogI(fname);

        qg.renameFile({
            srcUri: dst_copy_file,
            dstUri: dst_rename_file,
            success: function (uri) {
                LogI(fname + `handling success: ${uri}`)
                makeToast("文件重命名成功");
            },
            fail: function (data, code) {
                LogI(fname + `handling fail, code = ${code} , data = ${data}`)

                if ("false" === qg.accessFile({uri: dst_copy_file})) {
                    makeToast("文件重命名失败\n" + dst_copy_file + "不存在\n    先执行拷贝");
                    return
                }

                makeToast("文件重命名失败");
            }
        })
    },

    get () {
        let fname = " getFileInfo ";
        LogI(fname);

        qg.getFileInfo({
            uri: dst_copy_file,
            success: function (data) {
                LogI(fname + `handling success: ${JSON.stringify(data)}`)
                makeToast("文件信息：" + JSON.stringify(data));
            },
            fail: function (data, code) {
                LogI(fname + `handling fail, code = ${code}, data = ${data}`)

                if ("false" === qg.accessFile({uri: dst_copy_file})) {
                    makeToast("文件信息获取失败\n" + dst_copy_file + "不存在\n    先执行拷贝");
                    return
                }

                makeToast("文件信息获取失败");
            }
        })
    },

    delete () {
        let fname = " deleteFile ";
        LogI(fname);

        qg.deleteFile({
            uri: dst_copy_file,
            success: function (data) {
                LogI(fname + `handling success: ${JSON.stringify(data)}`)
                makeToast("文件删除成功");
            },
            fail: function (data, code) {
                LogI(fname + `handling fail, code = ${code}, data = ${data}`)

                if ("false" === qg.accessFile({uri: dst_copy_file})) {
                    makeToast("文件删除失败\n" + dst_copy_file + "不存在\n    先执行拷贝");
                    return
                }

                makeToast("文件删除失败");
            }
        })
    },

    writeText () {
        let fname = " writeFile ";
        LogI(fname);
        qg.writeFile({
            uri: dst_read_write_file,
            text: "123\n456\n567\n这是测试数据\n",
            success: function (data) {
                LogI(fname + `handling success: ${JSON.stringify(data)}`)
                makeToast("文件写入成功");
            },
            fail: function (data, code) {
                LogI(fname + `handling fail, code = ${code}, data = ${data}`)
                makeToast("文件写入失败");
            }
        })
    },

    readText () {
        let fname = " readFile ";
        LogI(fname);
        qg.readFile({
            uri: dst_read_write_file,
            success: function (data) {
                LogI(fname + `handling success: ${JSON.stringify(data)}`)
                makeToast("内容：" + data.text);
            },
            fail: function (data, code) {
                LogI(fname + `handling fail, code = ${code}, data = ${data}`)

                if ("false" === qg.accessFile({uri: dst_read_write_file})) {
                    makeToast("文件读取失败\n" + dst_read_write_file + "不存在\n    先执行写文件");
                    return
                }

                makeToast("文件读取失败");
            }
        })
    },

    readBinaryText () {
        let fname = " readFile ";
        LogI(fname);
        qg.readFile({
            uri: dst_read_write_file,
            encoding: "binary",
            success: function (data) {
                LogI(fname + `handling success: ${JSON.stringify(data)}`)
                makeToast("内容：" +  ab2str(data.text));
            },
            fail: function (data, code) {
                LogI(fname + `handling fail, code = ${code}, data = ${data}`)

                if ("false" === qg.accessFile({uri: dst_read_write_file})) {
                    makeToast("文件读取失败\n" + dst_read_write_file + "不存在\n    先执行写文件");
                    return
                }

                makeToast("文件读取失败");
            }
        })
    },

    unzip () {
        let fname = " unzipFile ";
        LogI(fname);

        qg.unzipFile({
            srcUri: src_zip_file,
            dstUri: dst_zip_path,
            success: function (uri) {
                LogI(fname + `handling success: ${uri}`)
                makeToast("解压成功");
            },
            fail: function (data, code) {
                LogI(fname + `handling fail, code = ${code} , data = ${data}`)

                if ("false" === qg.accessFile({uri: src_zip_file})) {
                    makeToast("解压失败\n" + src_zip_file + "未打包，解压失败");
                    return
                }

                makeToast("解压失败");
            }
        })
    },

    appendFile () {
        let fname = " appendFile ";
        LogI(fname);

        qg.appendFile({
            uri: dst_read_write_file,
            data: "\n我是追加的数据\n",
            success: function (uri) {
                LogI(fname + `handling success: ${uri}`)
                makeToast("追加写入成功");
            },
            fail: function (data, code) {
                LogI(fname + `handling fail, code = ${code} , data = ${data}`)
                if ("false" === qg.accessFile({uri: dst_read_write_file})) {
                    makeToast("追加写入失败\n" + dst_read_write_file + "不存在\n    先执行写文件");
                    return
                }
                makeToast("追加写入失败");
            }
        })
    },

});

```
