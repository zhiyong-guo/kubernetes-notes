![Static Badge](https://img.shields.io/badge/kubernetes-blue) ![Static Badge](https://img.shields.io/badge/output-green)

## Namespace 是什么？ 

在 Kubernetes 中，命名空间（Namespace）提供一种机制，将同一集群中的资源划分为相互隔离的组。同一名字空间内的资源名称要唯一，但跨名字空间时没有这个要求。名字空间作用域仅针对带有名字空间的对象（例如 Deployment、Service 等），这种作用域对集群范围的对象（例如 StorageClass、Node、PersistentVolume 等）不适用。

理解：把对象（资源）进行分组，方便管理。

## 初始 namespace

Kubernetes 集群启动时会创建四个初始名字空间：

- default：Kubernetes 包含这个名字空间，以便于你无需创建新的名字空间即可开始使用新集群。
- kube-system：该名字空间用于 Kubernetes 系统创建的对象。
- kube-node-lease：该名字空间包含用于与各个节点关联的 Lease（租约）对象。 节点租约允许 kubelet 发送心跳， 由此控制面能够检测到节点故障。
- kube-public：所有的客户端（包括未经身份验证的客户端）都可以读取该名字空间。 该名字空间主要预留为集群使用，以便某些资源需要在整个集群中可见可读。 该名字空间的公共属性只是一种约定而非要求。

## 操作 Namespace

[Namespace 管理指南文档](https://kubernetes.io/zh-cn/docs/tasks/administer-cluster/namespaces/)

```shell
# 列出集群命名空间
kubectl get namespace

# 执行命令时设置命名空间
kubectl get pods --namespace=<命名空间名称>

# 设置命令默认命名空间
kubectl config set-context --current --namespace=<命名空间名称>

# 查看位于命名空间的资源
kubectl api-resources --namespaced=true

# 查看不在命名空间的资源
kubectl api-resources --namespaced=false
```

## 参考资料

- Kubernetes Version: v1.27
- [https://kubernetes.io/zh-cn/docs/concepts/overview/working-with-objects/namespaces/](https://kubernetes.io/zh-cn/docs/concepts/overview/working-with-objects/namespaces/)