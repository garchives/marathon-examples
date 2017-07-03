# Kafka

wurstmeister/kafka:0.10.0.1-2

## Doployment

* Kafka

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/groups' -H 'Content-Type:application/json' -d@kafka.json
```

* Kafka manager

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@kafka-manager.json
```