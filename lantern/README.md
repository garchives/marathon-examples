# Lantern

lantern, 默认端口 8787。

ENTRYPOINT
```
/lantern -addr 0.0.0.0:8787
```

## Deployment

* calico network

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@lantern.json
```

* host network

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@lantern-host.json
```