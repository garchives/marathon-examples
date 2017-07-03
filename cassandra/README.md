# Deployment

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/groups' -H 'Content-Type:application/json' -d@cassandra-cluster.json
```

# Connection

```bash
$ docker run -it --rm --dns 192.168.111.203 cassandra:3.9 nodetool -host c1.cassandra.database.marathon.mesos -p 7199 status  
```

```bash
$ docker run -it --rm --dns 192.168.111.203 cassandra:3.9 cqlsh c1.cassandra.database.marathon.mesos
```
