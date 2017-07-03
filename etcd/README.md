# ETCD cluster

## Deployment

`2ecbfdfea67e0094b451e2a72f3bea22` 是我用 node.js 控制台随机生成的 UUID (token), 也可以自定义.　目前没有办法动态调整　IP, 但是在 marathon 可以直接指定域名从而不用关心具体的 IP.

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/groups' -H 'Content-Type:application/json' -d@etcd-cluster.json
```

## Test

```bash
$ docker run -it --rm --dns 192.168.111.203 etcd:2.3.7 etcdctl --endpoints=http://e1.etcd.marathon.mesos:2379 cluster-health
```

```bash
$ docker run -it --rm --dns 192.168.111.203 etcd:2.3.7 etcdctl --endpoints=http://e1.etcd.marathon.mesos:2379 set foo "bar"
$ docker run -it --rm --dns 192.168.111.203 etcd:2.3.7 etcdctl --endpoints=http://e1.etcd.marathon.mesos:2379 get foo
```