[TOC]
# 介绍
nginx负载在30000-50000，基于linux内核2.6。
查看主机负载用top命令：
load avorage 1天 5天 10天 表示负载量
ni表示空闲率
tree命令查看文件树
# 安装
## 配置
详情见配置文件
nginx -t 检测配置
pkill命令杀死进程，加参数 -HUP平滑重启，-URS1重新初始化日志
# 虚拟主机
配置中的server
```
server{
       listen 80;
       server_name www.baidu.com;
       access_log logs/test.access.log main;
       location / {
           root /usr/share/nginx/html;
           index index.html;
       }
        location /status{
                stub_status on;
        }
    }

```
# 自身监控
stub_status on;
# 目录页列表
autoindex on;
# 日志切割
见脚本
```
#!/bin/bash
#nginx_log_cut.sh
t=`date +%Y_%m_%d`
mkdir -p /home/nginx/logs/$t &>/dev/null
mv /etc/nginx/logs/*.log /home/nginx/logs/$t/
pkill -USR1 nginx
```
# rewrite
# 反向代理
