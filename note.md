### **客户端登录**
服务器启动的时候会注册好客户端接入的回调函数。客户端接入是 AE_READABLE 类型事件。
```
if (aeCreateFileEvent(server.el, server.fd, AE_READABLE,
        acceptHandler, NULL, NULL) == AE_ERR)
```

在事件循环中进行事件检测
```
aeMain(server.el);  ->  aeProcessEvents(eventLoop, AE_ALL_EVENTS);
```
在 acceptHandler 中接受客户端连接，设置后续通信的回调函数 readQueryFromClient .
```
if (aeCreateFileEvent(server.el, c->fd, AE_READABLE,
        readQueryFromClient, c, NULL) == AE_ERR)
```


### **客户端登出**
现在的客户端连接都是在连接的同时携带了命令信息，服务端回复之后客户端会主动断开。


### **收到请求**


### **发送回复**