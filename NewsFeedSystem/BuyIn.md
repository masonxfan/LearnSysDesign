一共两步
publish
receive

先publish
来设计api：
HTTP req
post
v1/me/feed
context和token

get/me/feed

load balancer来了之后，到post service，fanoutservice，notification service

整体是有瑕疵的，瑕疵还挺大，要保留朋友关系，要不然的话谁知道怎么trigger pub

news feed 就更糙了，一个news feed service，怎么就神奇的能把news feed 给用户呢

接下来看deep dive吧，看看能不能把问题挖明白，挖不明白的话还得闹心自己找



