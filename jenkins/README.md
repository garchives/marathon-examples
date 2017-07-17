# Jenkins

jenkins:2.32.3-alpine

## Doployment

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@jenkins.json
```