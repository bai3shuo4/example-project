# Kubernetes 示例项目

这是一个使用 Kubernetes 部署 Nginx 应用的示例项目。该项目包含了完整的 Kubernetes 资源配置，用于演示如何部署和管理一个简单的 Web 应用。

## 项目结构

- `deployment.yaml`: 定义应用的部署配置
- `service.yaml`: 定义 Kubernetes Service
- `ingress.yaml`: 配置 Ingress 规则
- `config.yaml`: 应用配置
- `secret.yaml`: 敏感信息配置

## 部署说明

### 前置条件

- Kubernetes 集群
- kubectl 命令行工具
- 集群中已安装 Ingress Controller

### 部署步骤

1. 创建配置和密钥：
```bash
kubectl apply -f config.yaml
kubectl apply -f secret.yaml
```

2. 部署应用：
```bash
kubectl apply -f deployment.yaml
```

3. 创建服务：
```bash
kubectl apply -f service.yaml
```

4. 配置 Ingress：
```bash
kubectl apply -f ingress.yaml
```

## 配置说明

- 应用使用 Nginx 最新版本
- 默认部署 2 个副本
- 服务类型为 ClusterIP
- Ingress 配置为 example.local 域名
- 应用配置通过 ConfigMap 和 Secret 注入

## 访问应用

配置本地 hosts 文件，添加以下记录：
```
ClusterIP example.local
```

然后可以通过浏览器访问：http://example.local

## 注意事项

- 确保 Kubernetes 集群正常运行
- 检查 Ingress Controller 是否正确配置
- 根据实际需求修改配置参数 