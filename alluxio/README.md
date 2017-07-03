# Alluxio

## Deployment

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/groups' -H 'Content-Type:application/json' -d@alluxio-ha.json
```


## 命令

```bash
$ alluxio fs -Dalluxio.master.hostname=master.alluxio.marathon.mesos copyFromLocal README.md /
$ alluxio fs copyFromLocal README.md alluxio://master.alluxio.marathon.mesos/ # 不管用，只认 conf/alluxio-site.properties
```

## 注意

```
Alluxio master 使用主机名（不是 ip）注册到 zookeeper，所有需要设置 `hostname`，并且确保 dns 可以解析到。
另外，worker 也要指定主机名，否则无法传输数据到　worker 节点上，也就是 master 节点需要访问到 worker　节点。
对于 master 而言，只有 leader 才会有　19999　端口。
```

```
当在容错模式下运行 Alluxio, worker 的默认心跳超时时间可能太短。 为了能在 master 进行故障转移时正确处理 master 的状态，建议将 worker 的默认心跳超时时间设置的长点。 增加 worker 上的默认超时时间，可以通过修改 conf/alluxio-site.properties 下的配置参数 alluxio.worker.block.heartbeat.timeout.ms 至一个大些的值（至少几分钟）。
```