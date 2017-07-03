# 部署

```bash
curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@mysql.json
```

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@phpmyadmin.json
```

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/groups' -H 'Content-Type:application/json' -d@mysql-phpmyadmin.json
```

（phpmyadmin.json 没有指定要连接具体的 MySQL， mysql-phpmyadmin.json 绑定了依赖）

# 注意

```
1. mysql 内存不能太小否则启动不了，我试过 64MB 不行。
2. 环境变量 MYSQL_ROOT_HOST 很重要，决定着是否可以在容器外访问。
```
