http://www.cnblogs.com/hahp/p/5614285.html

7. 附：mesos metrics 和 statics 地址
http://master1:5050/metrics/snapshot

http://slave4:5051/metrics/snapshot

http://master1:5050/master/state.json

http://slave4:5051/monitor/statistics.json


## Deployment 

* node-exporter

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@node-exporter.json
```

* mesos-exporter

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@mesos-exporter.json
```