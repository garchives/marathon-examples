[Marathon-lb](./marathon-lb.png)

# 部署

	curl -XPOST 'http://marathon.mesos:8080/v2/apps' -H 'Content-Type:application/json' -d@marathon-lb.json

	curl -XPOST 'http://marathon.mesos:8080/v2/groups' -H 'Content-Type:application/json' -d@hdfs.json

# 镜像

	registry.marathon.mesos/images/marathon-lb:v1.5.0

	{"forcePullImage": true}，需要强拉。

# 网络

	网络模式: "HOST" (external group)

	此处，如果是internal group也可以考虑使用calico网络，但是从性能的角度看还是建议都使用HOST网络。