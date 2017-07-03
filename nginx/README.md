# Nginx

nginx:1.11.9-alpine

## Dockerfile

https://github.com/nginxinc/docker-nginx/blob/master/stable/alpine/Dockerfile

# 部署

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@nginx.json
```