# Maven repository

sonatype/nexus3:3.2.1


## Deployment

```bash
$ curl -XPOST "http://marathon.mesos:8080/v2/apps" -H "Content-Type:application/json" -d@maven-repository.json
```

## Test

```bash
$ curl -u admin:admin123 http://maven.repo.marathon.mesos:8081/service/metrics/ping
```

