设计api
一个post short
一个get，直接get那个key

正好复习一下所有的http error code
1** 服务器收到请求，要求者需要继续执行操作
100 继续
101 改协议

2** 成功，接受，并处理
200 成功，get post
201 creatd
202 accepted，接受了，有可能没处理
203 非授权信息，请求成功，返回metadata副本
204 no content
205 reset content 可通过这个返回码清空浏览器的表单阈
206 处理部分get请求
3** 重定向，进一步操作完成请求
300 多种选择，你选一个先
301 永久移动，换到新的url了
302 临时移动，原有url还能用
303 查看其他地址，和选一个差不多
304 未修改
305 用代理
306 unused 废弃了
307 临时重定向

4** 客户端错误，req的错误语法导致无法完成请求
400 语法错误，不认识这种请求
401 无身份验证
402 payment required
403 验证了，但是失败了
404 您请求的资源无法找到
405 客户端请求的方法被禁止
406 not acceptable 不接受这种请求
407 请求代理
408 time out
409 conflict
410 资源不存在， gone
411 需要长度
412 precondition failed
413 请求实体过大
414 url过长
415 无法处理媒体格式
416 请求范围无效
417 expectations failed

5** 服务器错误，服务器处理的时候没处理明白
500 内部请求错误
501 不支持请求功能
502 bad gateway，代理有毛病
503 系统维护或过载
504 gateway timeout
505 不支持协议版本


这里边就可以通过url shortener知道，到底是url的server出问题了，还是服务出问题了
搞个hash，lambda function都可以