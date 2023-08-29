从简单入手，先做single server design，中心化解决方案

storage，metadata db，upload server，download server

把文件放到http的body里
http协议本身对文件大小没有限制，但是默认值为44gb

download function - presigned url

distributed：
shard based on userID
hot user？

上传时候加loadbalancer

syncdata
加一个block server
这个server的作用是把文件拆成小块的block

还可以加个cache层




