# Spark standalone

## Doployment

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/groups' -H 'Content-Type:application/json' -d@spark.json
```

## Image

```
{"forcePullImage": true}
```

## Network

calico 网络：dev-net

此处，也可以使用 BRIDGE 网络, 用 marathon-lb 作服务发现，但实测发现跑任务会出现中断的问题，无法连接到 BRIDGE 子网。

## 注意

worker 节点的环境变量很重要。如果不指定下面两个环境变量，spark worker 容器默认使用的是主机的 mem 和 cpu, 从而导致总的 mem 和 cpu 不正确，当提交超额任务的时候也不会报错，从而造成 spark 任务分配完全不合理。

```
"SPARK_WORKER_CORES": "{{cpus}}",
"SPARK_WORKER_MEMORY": "{{mem}}"
```

其他环境变量还不确定是否有效。

```
"SPARK_CORES_MAX": "{{spark.cores_max}}",
"SPARK_EXECUTOR_MEMORY": "{{spark.executor_memory}}",
```

## Spark Notebook

> http://blog.csdn.net/u012948976/article/details/52951141