# Tomcat

tomcat:8.0-jre8-alpine

## Dockerfile

https://github.com/docker-library/tomcat/blob/master/8.0/jre8-alpine/Dockerfile

# 部署

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@tomcat.json
```