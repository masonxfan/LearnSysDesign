post service
给个cache，再给个db，暂时先用个dynamo，别堵死自己的路子

用graph db去管理朋友id
再那个db去管理user信息，再来个dynamo也没毛病，可以把post id串成字符串扔给user db
还是人家想问题全面呐，不愧是写书的人

fanout service还有tradeoff呢
可以fanout on write
可以fanout on read

feed的话就涉及cdn了，基本上就很高级了

还深挖了cache，这是我完全不了解的地方：
5层cache，cache可以设层级，但是还是浅

值得深挖的地方：
graphdb详解
首先得听说过Neo4J和JanusGraph
主要存储：节点和关系
算法的话需要图算法，深搜广搜这些，内部存储是一堆指针指来指去，劣势是不利于分布式存储
搜索以来内部的图搜索引擎

Neo4J支持ACID，集群，备份和故障转移

JanusGraph只是一个引擎，其后端的数据存储方式不固定，比如可以通过cassandra来存
还可以通过ES进行全文搜索

节点里可以有属性，key value形式，有标签，描述表中作用

关系也有属性，keyvalue形式

属性，就是attribute，可以创建索引

标签，加速节点中的查找

想深挖，还是自己部署一个本地的neo4j，然后把命令都跑一下试试

去neo4j自己建立一个集群，用cypher做一下query
graphdb里边存：node，relationship，给label，每个node和relationship都可以做lable
csv，relationaldb，都可以往neo4j里导入。
100，000rps一个instance，可以做read replica去承载更多的访问
优势，不用锁表，防throttle就行



cdn详解

cache详解
redis 常见用例：
缓存cache，罩在mysql外边，防止mysql的数据访问量太大被击穿

chat，messaging and queues，因为redis里边有个list，list里边就可以放string，然后把list给pub出去就好了
chat room用websocket，pubsub
chatroom还可以把聊天记录分段
还有websocket怎么开，怎么关，设置定时关，给用户一个notice，你再不操作，我就关了。
突然间发现，chatroom有好多种解决方案，还可以把所有消息发到中心系统，然后再pub出来。

gaming leaderboards
sorted sets

session store
会话信息，可以做personalization

rich media streaming
主要是存metadata，为cdn做准备

geospatial real-time data
主要是记录实时信息

redis帮助机器学习
主要是存短期数据，学完就可以扔的那种

还有实时分析


