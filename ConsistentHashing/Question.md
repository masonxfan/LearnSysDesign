理解一致性哈希是啥
画个圈圈，如果有server down掉了，那就按着环形往下一个走，好处是不用重新组织安全稳定的service，不用从健康的server里往外拿东西

virtual node：
server影分身之术，一个server在环上有三四个位置，这样的话node就往后找就行，不一定能遇见哪个server的哪个影身份

居然没有讲一致性哈希的雪崩问题：
形容一下雪崩问题是什么：
一开始有4个server，每个server host 25个node，大家其乐融融
但server a突然开始不稳定，然后崩掉了，这样的话，server a的node就顺着hash环往后走，一路全都加到server b上
server b要说帮a分担个百分之30-40的，也没啥问题。但是把a的任务全拿过来的话，那心态就炸了。于是b也崩了。
a和b的node顺着hash环往c走，c看见这个情况，当时就慌了，于是也炸了，全部的load就都扔到d身上。那d也炸了。
于是本来一个node的崩溃，最后变成了全部系统的炸。

virtual node正好就可以解决这个问题，a炸了的话，他的nodes不一定全都转嫁给b，而是顺着影分身去找别的server
有vn的哈希环是这样的：假设影分身是随机的
abbcbddabac
那a爆炸的时候会发生什么呢顺着hash环
a1的node转嫁给了b1
a2的node转嫁给了b3
a3的node转嫁给了c2
虽然还是给了b很多，但是不至于全部都给b
如果整个环足够的零散，那么a的node实际上是均匀分给bcd的，这样就避免了雪崩


