从小到大：
首先先搞定单一server的key-value store
用hash table就行，然后全存在内存里
增加效率可以用如下方法
数据压缩
lfu在内存里，其他的在硬盘里

好了，该分布式了
复习CAP theorem：
都有啥呢，consistency，availability，partition tolerance
分布式不能妥协P，于是就在C与A之间做取舍

CP，你得等，有的时候数据就用不了了。
AP，你得等，有的时候你看的东西是脏的

复习脏写，脏读、不可重复读、幻读和MVCC
脏读：读取未提交数据
在事务中间去读，但是实际事务回滚了
解决办法，没提交之前上锁

不可重复读：读了update的老行
行锁
幻读：读了insert的新行
表锁

悲观锁和乐观锁
悲观：
读写全锁，每个事务不commit，其他人就没法操作数据库
乐观：
基于版本记录实现，更新时有版本变化。乐观锁不能解决脏读

MVCC：多版本控制，隐藏增加两列，创建版本和删除版本

一个数据库的需求：
• Data partition
把数据分成小块丢到不同的数据node去
面临两个问题：
怎么均匀分布
当node增加或者减少的时候，数据移动量最小
可以用一致性哈希来解决
但是问题来了，怎么做倒是简单，但我数据除了数据本身，还需要一些header，这样我才能知道哪个是数据吧。涉及到编码知识。

复习hadoop是咋存的数据,假设有10份数据，3个node，需要保证的是什么？保证掉了一个node数据还没丢
举例：
n1:0123456
n2:7890123
n3:4567890

• Data replication
这个和刚刚的hadoop思想是一样的
• Consistency
W+R>N就可以保证一致性
强一致，没有过时信息
弱一致，可能看见没被更新的信息
最终一致，时间够长，就会看到全部更新的信息

• Inconsistency resolution
如何解决不一致问题
思考：刚刚都已经有保证一致了，现在解决啥呢？同时更新俩node
vector clock，解决不了啥问题，就是一个二维版本号，ny读的是ny，nz读的是nz，nx更新还是照着nx更新的，conflict还是手动解决的
拓展Paxos算法，主打就是一个难，需要好好学习学习，三个角色，propose，accept和learn，需要主从关系，不然容易死锁，主打一个半数接受2f+1
俩阶段，prepare和accept，实在实在理解不了的话，把论文打印出来看看

• Handling failures
Gossip protocol维持白名单，偶尔聊天
sloppy quorum维持coordinator，然后coordinator去跟大家说话
暂时failure coordinator就行
永久failure an anti-entropy protocol，用A Merkle tree其实是哈希树，可以在node死掉之后去填充
data center炸了，multi region

• System architecture diagram 
• Write path
从coordinator到内存到硬盘，记录commit log
• Read path
从内存读，读不出来读硬盘，然后更新内存

