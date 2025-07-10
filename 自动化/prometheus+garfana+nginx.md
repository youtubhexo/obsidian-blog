
### 0 nginx 安装
```
  location /nginx_status {
    stub_status;
    allow 127.0.0.1;
    deny all;
    }
```

```Shell
/usr/local/nginx/sbin/nginx -s reload
```

### 1安装 Telegraf

vi /etc/yum.repos.d/influxdata.repo

```
[influxdata]
name = InfluxData Repository - RHEL $releasever
baseurl = https://repos.influxdata.com/centos/$releasever/$basearch/stable
enabled = 1
gpgcheck = 1
gpgkey = https://repos.influxdata.com/influxdata-archive_compat.key
```

```bash
 yum install telegraf
```

```

 vim /etc/telegraf/telegraf.conf  追击以下内容

[[inputs.nginx]]
  urls = ["http://127.0.0.1:81/nginx_status"]
  response_timeout = "5s"

[[inputs.tail]]
  name_override = "nginxlog"
  files = ["/usr/local/nginx/logs/access.log"]
  initial_read_offset = "beginning"
  pipe = false
  data_format = "grok"
  grok_patterns = ["%{COMBINED_LOG_FORMAT}"]

[[inputs.cpu]]
  percpu = true

[[inputs.disk]]

[[inputs.diskio]]

[[inputs.net]]

[[inputs.mem]]

[[inputs.system]]
[[outputs.prometheus_client]]
  listen = "0.0.0.0:9273"
  path = "/metrics"
  expiration_interval = "60s"


```

### 2 修改nginx 目录权限(log)
```bash
chmod 644 /usr/local/nginx/logs/access.log

chmod  -R 777 /usr/local/nginx
```

### 3 启动服务
```bash
systemctl start telegraf
systemctl enable telegraf
systemctl staus telegraf
```

### 4 添加到Prometheus
`  - targets: ["192.168.88.102:9273"]`


