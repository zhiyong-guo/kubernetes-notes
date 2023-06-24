![Static Badge](https://img.shields.io/badge/kubernetes-blue) ![Static Badge](https://img.shields.io/badge/output-green)

## 标签选择器

- 通过标签选择器（Label Selectors），客户端/用户可以识别对象并进行分组。
- 标签选择器的类型有两种：基于等值的选择器和基于集合的选择器。
- 标签选择器可以由逗号分隔的多个选择需求组成。
- 逗号表示与（AND）逻辑运算符，标签选择器不支持或（OR）逻辑运算符。

## 基于等值的选择器

支持的运算符有 `=`、`==` 和 `!=` 三种，前两个同义表示相等，而后者表示不相等。

- `env=prod`：选择标签键 `env` 值为 `prod` 的资源。
- `tier!=frontend`：选择标签键 `tier` 值不为 `frontend` 的资源。
- `env=prod,tier!=frontend`：选择标签 `env` 值为 `prod` 且 `tier` 不为 `frontend` 的资源。

## 基于集合的选择器

基于集合的标签需求允许你通过一组值来过滤键。支持三种操作符：`in`、`notin` 和 `exists`。

- `env in (prod, dev)`：标签 `env` 等于 `prod` 或 `dev` 的资源。
- `tier notin (frontend, backend)`：标签 `tier` 值不等于 `frontend` 或 `backend` 的资源。
- `partition`：有 `partition` 标签的资源，没有校验标签值。
- `!partition`：没有 `partition` 标签的资源。

## 使用标签选择器

### REST API
 
在 REST API 中，可以把标签选择器附加在 URL 查询字符串中。

- `?labelSelector=env%3Dprod,tier%3Dfrontend`
- `labelSelector=env+in+%28prod%2Cdev%29%2Ctier+in+%28frontend%29`

### Kubectl

```shell
kubectl get pods -l env=prod,tier=frontend
kubectl get pods -l 'env in (prod, dev)'
kubectl get pdos -l 'env in (prod, dev),tier in (frontend)'
```

### API 对象

```yaml
selector:
  env: prod
```

```yaml
selector:
  matchLabels:
    env: prod
  matchExpressions:
    - { key: tier, operator: In, values: [frontend, backend] }
```

## 参考资料

- Kubernetes Version: v1.27
- [https://kubernetes.io/zh-cn/docs/concepts/overview/working-with-objects/labels/#label-selectors](https://kubernetes.io/zh-cn/docs/concepts/overview/working-with-objects/labels/#label-selectors)