# KubeSphere

## yml 安装或者下载下 这两个 yaml 安装

```yml
kubectl apply -f https://github.com/kubesphere/ks-installer/releases/download/v3.3.1/kubesphere-installer.yaml

kubectl apply -f https://github.com/kubesphere/ks-installer/releases/download/v3.3.1/cluster-configuration.yaml
```

### 查看安装进度及日志

```yml
kubectl logs -n kubesphere-system $(kubectl get pod -n kubesphere-system -l 'app in (ks-install, ks-installer)' -o jsonpath='{.items[0].metadata.name}') -f
```

### 访问

http://127.0.0.1:30880

## 账号密码

```
admin
P@88w0rd
```

# 部署一个简单的 Nginx 应用到 k8s

```
kubectl apply -f deployment.yml
```

# 把 k8s 里面的 80 端口暴露出来（在正式环境中不需要，80 直接可以访问，因为是在本地部署的）

执行该命令会需要权限

```
kubectl port-forward service/app-release -n release 80:80
```

#### 请注意

在生产环境中，直接在 Kubernetes YAML 文件中包含 kubectl port-forward 命令是不推荐的，因为它违反了最佳实践和基于声明式配置的思想。端口转发通常用于开发和调试阶段，在生产环境中应采用适当的负载均衡和服务发现机制。
