# docker_setup_prometheus
Prometheus（普罗米修斯）是一套开源的监控&报警&时间序列数据库的组合.由SoundCloud公司开发。

Prometheus基本原理是通过HTTP协议周期性抓取被监控组件的状态，这样做的好处是任意组件只要提供HTTP接口就可以接入监控系统，不需要任何SDK或者其他的集成过程。这样做非常适合虚拟化环境比如VM或者Docker 。

Prometheus应该是为数不多的适合Docker、Mesos、Kubernetes环境的监控系统之一。

环境 Environment : 
Mac OS, Git 

### 安装node-exporter
下载镜像
```
docker pull prom/node-exporter
```
### 运行
```
docker run -d -p 9100:9100 quay.io/prometheus/node-exporter
```

### 安装redis_exporter
下载镜像
```
docker pull oliver006/redis_exporter
```
### 运行
```
docker run -d --name redis_exporter -p 9121:9121 oliver006/redis_exporter
```

### 安装grafana
下载镜像
```
docker pull grafana/grafana
```
### 运行
```
docker run -d --name=grafana -p 3000:3000 grafana/grafana
```

### 安装prometheus

有个prometheus.yml需要自己创建位置是/usr/local/src/file/ 这个文件放哪里都可以 到时候指定下就行了

下载镜像
```
docker pull prom/prometheus
```

### 运行
```
docker run -d -p 9090:9090 -v /Users/kevincai/Desktop/Development/prometheus/prometheus.yml:/Users/kevincai/Desktop/Development/prometheus/prometheus.yml quay.io/prometheus/prometheus --config.file=/Users/kevincai/Desktop/Development/prometheus/prometheus.yml
```

都运行成功后看下 docker

```
docker ps 
```
### 然后打开127.0.0.1:9090 看到图下的up证明都启动好了没啥问题 
localhost

```
http://192.168.1.229:9100/metrics

http://192.168.1.229:3000/login

http://localhost:9090/targets

```

#### Reference
https://www.jianshu.com/p/339db34e4afe 

https://zhuanlan.zhihu.com/p/101184971

https://www.jianshu.com/p/1cb66d48920b
 
https://www.cnblogs.com/xiao987334176/p/9930517.html 

### GitBook 
https://songjiayang.gitbooks.io/prometheus/content/