

## 第二部分. Spring Cloud 配置

* 默认客户端使用服务端的8888监听配置, 如果要该默认端口, 需要在服务端的`bootstrap.properties`文件修改(在`application.properties`无效). 

* 刷新配置需要使用`@RefreshScope`注解. 在调用/refresh方法时会从服务器刷新.
