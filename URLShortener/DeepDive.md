最一开始，所有东西存在hashmap里
确定一共有多少位，62^n要大于365b，所以7位就够用

具体hash function都有什么，比如CRC32 MD5 SHA 1

还可以随着id增长随着加

最终是有数据库作为支持
既然是string，那搞个redis，好又快

再搞个load balancer

重点还是在hash算法上