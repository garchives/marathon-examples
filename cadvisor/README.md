# Cadvisor

## Deployment

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@cadvisor-to-prometheus.json
```