# Calico

如果使用 marathon 来同时部署 etcd 和 calico, 存在一个矛盾： etcd 需要依赖 calico 网络, calico 又需要依赖 etcd 存储，那该怎么办呢？

事实上，考虑到要快速解决故障，我直接在主机上部署了 calico，并不打算在 marathon 中部署 calico。另一方面，我尝试着部署 calico 没能成功，因为没法动态设置主机 IP。

因为 calico 部署在了主机上，而 calico 又依赖 etcd，所以 etcd 也随 zk 直接部署在了主机上。主机上部署 etcd 和 zk 是为了保障整个 mesos 集群（含 calico 网络）的高可用。

因此，为了避免主机上的 etcd 和 zk 集群受其他应用的影响导致 mesos 集群不可用，我又在 marathon 上部署了 etcd 和 zk 集群，供其他应用（如 kafka）使用。