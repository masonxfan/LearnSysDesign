看见问题，先想市面上成型的产品，比如datadog
实时，还是near real time
triggered by client，那就像是datadog的agent

这里边涉及数据传输协议，复习一下websocket
websocket是一个持久的链接
http不支持持久链接
http的话是，一个req，一个resp就结束了
虽然最新的有多个req，多个resp，但是req和resp的数量一一对应，resp是被动的，不能主动发起

websocket也是先握手
？http吗，我看更像是tcp，果然是基于tcp，回答者给改过来了

复习一下脱水的概念：
只留存需要的数据，且不做mapping

继续回到websocket
建立了websocket协议之后，就变成，resp主动出击


继续回到notification
客户端能做什么，服务端要做什么

万能问题，数据量