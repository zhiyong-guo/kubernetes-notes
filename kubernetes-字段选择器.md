![Static Badge](https://img.shields.io/badge/kubernetes-blue) ![Static Badge](https://img.shields.io/badge/output-green)

## 字段选择器

使用字段选择器（Field selectors）可以根据一个或多个资源字段的值筛选 Kubernetes 对象。不同类型的资源支持不同的字段，但都会支持 `metadata.name` 和 `metadata.namespace` 两个字段。支持的操作符有：`=`，`==` 和 `!=`。

```
kubectl get pods --field-selector metadata.name=my-service
kubectl get pdos --field-selector metadata.name=my-service,metadata.namespace=default
```

## 参考资料

- Kubernetes Version: v1.27
- [https://kubernetes.io/zh-cn/docs/concepts/overview/working-with-objects/field-selectors/](https://kubernetes.io/zh-cn/docs/concepts/overview/working-with-objects/field-selectors/)