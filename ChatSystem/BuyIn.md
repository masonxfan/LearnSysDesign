这个系统很复杂，大致得知道分成几个service

先从点对点来看：
client
可以send message
可以receive message

server
client把message发过来之后，server要把这个message发到另一个client上去
用http没啥问题，websocket反正也可以
然后长时间没有通信的话自动关闭

polling
network costy

long polling
一直把connection open
可能在load balancing的时候收到不消息

最后还是用的websocket
websocket是双向的
websocket还是得链接在server 和 client之间，不能client互联

需要很多services
service discovery
authentication
group
profile

数据存储用什么？
聊天记录这玩意一看就是nosql ，包含userid，用datatime当sortkey，短期的拿个cache存一下，redis就可以
profile用rdb

