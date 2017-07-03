# HBase

高可用 HBase 集群

## Deployment

- 使用 hostname 注册服务到 zookeeper（测试发现存在 bug）

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/groups' -H 'Content-Type:application/json' -d@hbase-ha.json
```

- 使用 ip 注册服务到 zookeeper （推荐）

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/groups' -H 'Content-Type:application/json' -d@myhbase-ha.json
```
