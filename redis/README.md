# Redis cluster

## Deployment

* 单节点

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@redis.json
```

* 高可用集群

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/groups' -H 'Content-Type:application/json' -d@redis-cluster.json
```

* 带有持久化存储

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/groups' -H 'Content-Type:application/json' -d@redis-cluster-with-storage.json
```