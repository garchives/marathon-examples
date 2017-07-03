# HDFS

## 部署

```bash
$ curl -XPOST 'http://marathon.mesos:8080/v2/groups' -H 'Content-Type:application/json' -d@hdfs.json
```

## 注意

通过 rexray 插件创建的卷默认大小为 16GB, 所以一个 datanode 的默认大小为 16GB， 实际需求中感觉容量太小了。

有没有办法自动配额？

dockerd 中 --storage-driver 设置为 aufs 和 overlay/2 的话是不支持自动配额的（devicemapper可以）。

可以通过这种方法尝试: 

```bash
$ docker run -it --name web -p 8000:80 --volume-driver=rexray -v nginx_data:/usr/share/nginx --storage-opt=size=17 -d nginx:1.11.9-alpine # aufs 和 overlay/2 会报错
```

但是，

可以先创建卷再使用，并且创建卷的时候是支持配额的(总感觉是个 bug)。

例如，

```bash
$ docker volume create --driver rexray --opt=size=17 --name nginx_data
$ docker run -it --name web -p 8000:80 --volume-driver=rexray -v nginx_data:/usr/share/nginx -d nginx:1.11.9-alpine
```

所以，

如果要为 datanode 设置大小需要先创建卷，不过总感觉有些多余，我也在考虑是否要使用 devicemapper

例如，

```bash
$ docker volume create --driver rexray --opt=size=16 --name hdfs-namenode
$ docker volume create --driver rexray --opt=size=256 --name hdfs-datanode-1
$ docker volume create --driver rexray --opt=size=256 --name hdfs-datanode-2
$ docker volume create --driver rexray --opt=size=256 --name hdfs-datanode-3
$ docker volume create --driver rexray --opt=size=256 --name hdfs-datanode-4
$ docker volume create --driver rexray --opt=size=256 --name hdfs-datanode-5
$ curl -XPOST 'http://marathon.mesos:8080/v2/groups' -H 'Content-Type:application/json' -d@hdfs.json
```

## 疑问

到底该启几个 datanode？

可以一个 datanode 应用多个实例吗?
