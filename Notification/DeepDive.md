甚至还可以更复杂一些
比如加rate limiter
比如分析notification请求
比如notification请求缓存
比如client side缓存去重

复习event driven
一个event，先做动作，后commit
可能在commit之前回滚，所以需要加行锁（乐观锁）

如果是表之间的动作，可以锁表
