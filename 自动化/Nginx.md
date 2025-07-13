### 简述什么是Nginx

Nginx是一款轻量级的Web服务器 反向代理服务器  及电子邮件代理服务器

特点:

高并发:  可以同时响应更多的请求  事件  epoll模型 几万
响应快: 尤其在处理静态文件上,响应速度很快  sendfiel
热部署: (1)**平滑升级**   (2) **可以快速重载配置**
高可靠:稳定性 master 进程管理调度请求分发到哪一个worker=>worker进程  响应请求  一master多worker
分布式支持：反向代理 七层负载均衡，新版本也支持四层负载均衡
低消耗：cpu和内存 1w个请求 内存2~3MB


应用场景:
1) web服务器软件 httpd(apache) 同类型web服务器软件：apache、nginx(俄罗斯)、iis(微软)、lighttpd(德国) 
2) 提供了IMAP/POP3/SMTP服务 
3) 充当反向代理服务器，实现负载均衡功能。LB=>Load Blance
![](https://raw.githubusercontent.com/youtubhexo/obsition-images-zhangwangyan/main/20250713082626.png)



