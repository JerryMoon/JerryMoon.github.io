## 文件存储

在应用平台中是按分区来存储文件的，目前支持以下分区

1. Cache，一般用于存储缓存文件，下载后的数据存在于该分区中，该分区中的文件可能因存储空间不够被系统删除
2. Files，一般用于存储永久文件，该分区中的文件由应用自己管理
3. Temp，表示从外部映射过来的临时文件，出于安全性考虑，临时文件是只读的，并且只能通过调用特定的API获取，比如qg.pickImage方法。另外临时文件的访问是临时的，应用重启后无法访问到临时文件，需要通过特定API重新获取。

另外应用资源也作为一个特殊的只读分区进行处理。

## URI

URI用于标识应用资源和文件，通过URI来访问应用资源和文件。

| 资源类型  | URI                   | 只读   | 示例                                | 说明      |
| ----- | --------------------- | ---- | --------------------------------- | ------- |
| 应用资源  | /path                 | 是    | /Image/logo.png                | -       |
| Cache | internal://cache/path | 否    | internal://cache/fetch-123456.png | -       |
| Files | internal://files/path | 否    | internal://files/image/demo.png   | -       |
| Temp  | internal://tmp/path   | 是    | internal://tmp/xxxxx              | 由系统动态生成 |

URI允许的字符是`0-9a-zA-Z_-./%:`(不包含引号)，URI中不能出现`..`，URI支持目录结构，目录由斜线'/'分隔。

internal URI表示的是应用私有文件，即在指定internal URI时，无需指定应用标识，同一个internal URI对于不同的应用会指向不同的文件。

