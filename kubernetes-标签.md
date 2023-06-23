![Static Badge](https://img.shields.io/badge/kubernetes-blue) ![Static Badge](https://img.shields.io/badge/output-green)

## 标签是什么？

> 标签（Labels）是附加到 Kubernetes 对象（比如 Pod）上的键值对。标签旨在用于指定对用户有意义且相关的对象的标识属性，但不直接对核心系统有语义含义。标签可以用于组织和选择对象的子集。标签可以在创建时附加到对象，随后可以随时添加和修改。每个对象都可以定义一组键/值标签。每个键对于给定对象必须是唯一的。

理解：标签是附加到 Kubernetes 对象上对用户有意义的健值对信息，常用于对象的选择和分组。

## 语法和字符集

标签（Labels）是键/值对结构。

### 标签键

有效的标签键有两个段：可选的前缀和名称，用斜杠（/）分隔。 

前缀是可选的。如果指定，前缀必须是 DNS 子域：由点（.）分隔的一系列 DNS 标签，总共不超过 253 个字符，后跟斜杠（/）。`kubernetes.io/` 和 `k8s.io/` 前缀是为 Kubernetes 核心组件保留的。

名称是必需的，必须小于等于 63 个字符。以字母数字字符（`[a-zA-Z0-9]`）开头和结尾， 带有破折号（`-`），下划线（`_`），点（`.`）和之间的字母数字。

### 标签值

- 必须为 63 个字符或更少（可以为空）
- 除非标签值为空，必须以字母数字字符（`[a-zA-Z0-9]`）开头和结尾
- 可以包含破折号（`-`），下划线（`_`），点（`.`）和之间的字母数字。

## 示例

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: label-demo
  labels:
    environment: production
    app: nginx
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