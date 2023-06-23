![Static Badge](https://img.shields.io/badge/kubernetes-blue) ![Static Badge](https://img.shields.io/badge/output-green)

## 注解是什么？

> 你可以使用 Kubernetes 注解为对象附加任意的非标识的元数据。客户端程序（例如工具和库）能够获取这些元数据信息。

理解：注解是附加到 Kubernetes 对象上的元数据。客户端程序（例如工具和库）能够获取这些元数据信息，实现自定义的逻辑和功能。注解和[标签](./kubernetes-标签.md)的区别是：注解用来存储客户端程序需要的数据信息，而标签仅用于对象的选择（筛选）和分组。

## 语法和字符集

注解（Annotations） 存储的形式是键/值对（和标签一样）。

### 注解键

有效的注解键有两个段：可选的前缀和名称，用斜杠（/）分隔。 

前缀是可选的。如果指定，前缀必须是 DNS 子域：由点（.）分隔的一系列 DNS 标签，总共不超过 253 个字符，后跟斜杠（/）。`kubernetes.io/` 和 `k8s.io/` 前缀是为 Kubernetes 核心组件保留的。

名称是必需的，必须小于等于 63 个字符。以字母数字字符（`[a-zA-Z0-9]`）开头和结尾， 带有破折号（`-`），下划线（`_`），点（`.`）和之间的字母数字。

### 注解值

注解中的键和值必须是字符串。

## 示例

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: annotations-demo
  annotations:
    imageregistry: "https://hub.docker.com/"
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
```

## 参考资料

- Kubernetes Version: v1.27
- [https://kubernetes.io/zh-cn/docs/concepts/overview/working-with-objects/labels/](https://kubernetes.io/zh-cn/docs/concepts/overview/working-with-objects/labels/)