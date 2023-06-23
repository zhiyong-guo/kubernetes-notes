![Static Badge](https://img.shields.io/badge/kubernetes-blue) ![Static Badge](https://img.shields.io/badge/output-green)

## 如何理解 Kubernetes 对象？

> 在 Kubernetes 系统中，Kubernetes 对象是持久化的实体。 Kubernetes 使用这些实体去表示整个集群的状态。

理解：Kubernetes 对象描述了集群中节点、容器、资源、策略等相关信息。这些信息数据并持久化到数据库中（etcd）。

Kubernetes 对象是一种“意向表达（Record of Intent）”。通过创建对象，你本质上是在告知 Kubernetes 系统，你想要的集群状态看起来应是什么样子的。一旦创建该对象， Kubernetes 系统将不断工作以确保该对象存在，并使之达到期望的状态。

几乎每个 Kubernetes 对象都有两个字段，分别是：对象规约（Spec）和对象状态（Status）。

- **对象规约（Spec）**：创建对象时，用来描述对象应该具有的状态，也称为**期望状态（Desired State）**。
- **对象状态（Status）**：描述对象的**当前状态（Current State）**。集群会实时更新和设置对象状态，以使之达到期望状态。

## 如何创建和描述 Kubernetes 对象？

### 创建和描述对象

创建 Kubernetes 对象时，必须提供对象的 spec，用来描述该对象的期望状态，以及关于对象的一些基本信息（例如名称）。 当使用 Kubernetes API 创建对象时（直接创建或经由 kubectl 创建），API 请求必须在请求主体中包含 JSON 格式的信息。 大多数情况下，你需要提供 .yaml 文件为 kubectl 提供这些信息。 kubectl 在发起 API 请求时，将这些信息转换成 JSON 格式。

### 必需字段

- `apiVersion` - 创建该对象所使用的 Kubernetes API 的版本
- `kind` - 想要创建的对象的类别
- `metadata` - 帮助唯一标识对象的一些数据，包括一个 name 字符串、UID 和可选的 namespace
- `spec` - 你所期望的该对象的状态

### 示例

使用 .yaml 文件描述对象。

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  selector:
    matchLabels:
      app: nginx
  replicas: 2 # 告知 Deployment 运行 2 个与该模板匹配的 Pod
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

使用 kubectl 命令创建对象。

```shell
kubectl apply -f https://k8s.io/examples/application/deployment.yaml

# output：deployment.apps/nginx-deployment created
```

## 参考资料

- Kubernetes Version: v1.27
- [https://kubernetes.io/zh-cn/docs/concepts/overview/working-with-objects/](https://kubernetes.io/zh-cn/docs/concepts/overview/working-with-objects/)