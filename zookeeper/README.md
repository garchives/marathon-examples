# Zookeeper

## Deployment

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/groups' -H 'Content-Type:application/json' -d@zookeeper-cluster.json
```

## Connection

```bash
$ docker run -it --rm zookeeper:3.4.9 zkCli.sh -server zk1.zookeeper.marathon.mesos:2181
```