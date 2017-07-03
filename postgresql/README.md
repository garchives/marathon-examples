# PostgreSQL

## Deployment

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@postgresql.json
```

## 客户端连接

```bash
$ psql -h postgresql.sql.marathon.mesos -p 5432 -U root # 密码: root123456
```
