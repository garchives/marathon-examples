# Portainer

portainer/portainer:1.13.0

用于管理 docker 主机上的 volume、image、network 等。


## Deployment

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@portainer.json
```