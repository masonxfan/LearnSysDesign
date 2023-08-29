service discovery这个是什么？
早就听过zookeeper，需要详解
主要功能保证事物顺序

比如，一个新任务开始了，dicom transfer用好久才结束
其实并没有涉及异步
都是dicom transfer
上一个步骤全结束了trigger
trigger开始lambda
lambda读db，此时db里一定有信息
读完更新lambda

目前看，没发现任何尿点

突然间发现，聊天室可以用redis去排个序诶，sortset真是解锁了人类的认知

