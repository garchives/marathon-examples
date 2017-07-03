# Registry on ceph

`http://192.168.111.204:7480` 为 ceph rados-gw 地址.

## Deployment

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@registry-on-ceph.json
```

## 镜像

registry-ceph:2.6.0

该镜像基于官方镜像 `registry` 重构，允许修改端口和/或使用 ceph 对象存储, 并在使用 dcos-centos 安装集群的时候自动加载到了该节点。

> 注： `{"forcePullImage": false}`, 不需要强制下载了。


## 需要修改的参数

- `HTTP_PORT`: 任意端口
- `STORAGE_SWIFT_AUTHURL`: ceph对象网关地址（见ceph章节）
- `STORAGE_SWIFT_USERNAME`， `STORAGE_SWIFT_PASSWORD`： 用户名和密码（radosgw-admin user info --uid=registry）
```