先如何理解key value db
知道哪些是key value db

dynamo就是，memcached和redis也是

这个时候复习redis的知识，redis主要支持string，内存，特别快，有硬盘，所以可以做存储。每秒10万次读写，单线程读写，sort hash关联一个double，增删查都是复杂度为1。但是看见没，这块有个坑，大家都不说redis的改是怎么改的。
redis不能改，他的增加方式是，有hash就不增，没有hash才增。
那更新redis的逻辑应该是这样：
1. 查
2. 删
3. 增
通过消息队列保持原子性，防止有的消息被删掉了，但是没有增。
排行榜确实是个好题，能扩展的地方很多，但是对redis知识依赖性太高了

从performance的角度来看，key越小，效率越高

那么问问题的时候，需要考虑的点：
1. 建这个东西的目的是啥，高存储，稳定存储，便宜？
alex提到自动scaling，还有tunable consistency，需要再看看，并不太了解是什么意思。
