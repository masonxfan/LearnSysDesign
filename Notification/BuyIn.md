notification type

设计一下req和response的json格式？
req:
{
"type": string,
"service": [string, string, string]
}

response
{
"code": string,
"alert": string
}

拓展，apn是什么
Access Point Name，是手机接入网络的方式

FCM云消息传递
firebase cloud messaging
这么一看，firebase真的是好早啊
可以把消息发到设备上去

SMS这个是aws的服务
也是往外发短信的

Email可以直接用email service往外发

user从load balencer进来，注册这一步是通过load balancer完成的
好的，这就是一个profile service，或者是user service，这个东西可以很复杂
复习锁：user之间要是没有interaction的话，几乎不用锁
但是如果user之间的信息互相转的话，就要加锁了，乐观锁，能解决问题，但是不能避免脏读幻读，悲观锁，能解决，但是造成死锁，速度慢
