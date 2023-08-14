好多方法，一个一个看

Multi-master replication
每个node发出一个新id
但是会有很大的问题，有可能一个server不行了，但是第二天又活过来了，第二天的话，这个server给的id就少了

UUID
128-bit
uuid的生成包含了很多硬件信息，还有随机数，并不是完全不会重复，只是很难重复
uuid有很多种
基于时间
DCE安全，也同样可以基于时间
基于名字，物理机器的id
随机uuid

ticket server：
ticket server是一个单点的中心式server，然后给所有的其他server分发id

snowflake方法
先给一个时间戳，然后加数据中心了，然后加机器编码，然后加sequence

