![Static Badge](https://img.shields.io/badge/kubernetes-blue) ![Static Badge](https://img.shields.io/badge/output-green)

## Pod 是什么？

>Pod 是可以在 Kubernetes 中创建和管理的、最小的可部署的计算单元。Pod（就像在鲸鱼荚或者豌豆荚中）是一组（一个或多个）容器；这些容器共享存储、网络、以及怎样运行这些容器的声明。Pod 中的内容总是并置（colocated）的并且一同调度，在共享的上下文中运行。Pod 所建模的是特定于应用的 “逻辑主机”，其中包含一个或多个应用容器，这些容器相对紧密地耦合在一起。

理解：Pod 是 Kubernetes 中创建和管理的最小可部署的计算单元。Pod 就像一个“逻辑主机”，其中包含一个或多个应用容器，这些容器共享一组 Linux 名字空间、控制组（cgroup）和其他隔离的资源。

## 参考资料

- Kubernetes Version: v1.27
- [https://kubernetes.io/zh-cn/docs/concepts/workloads/pods/](https://kubernetes.io/zh-cn/docs/concepts/workloads/pods/)