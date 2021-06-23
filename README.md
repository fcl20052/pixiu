# Pixiu(貔貅) Overview

`Pixiu` 旨在对 `kubernetes` 原生功能的补充和强化

- 提供 `kubernetes` 层面的镜像管理能力
  - 可通过 `kubectl` 或 `client-go` 对集群中的 `images` 进行管理
  ```
  # kubectl get imgs
  NAME         AGE   IMAGE
  image-test   33h   nginx:1.9.2
  ```
  - 通过注释，在创建 `deployment` 等资源的时候，开启镜像拉取功能，自动在指定 `node` 完成镜像准备

- 无状态应用的分批发布
  ```
  # kubectl get advancedDeployment
  NAME         READY   UP-TO-DATE   AVAILABLE   AGE
  example-ad   3       3            3           4d2h
  ```

- 通过注释的方式，新增 `deployment` 和 `statefulset` 的自动扩缩容能力

### Installing (demo版)

`pixiu` 安装非常简单，通过 `kubectl` 执行 `apply` 如下文件即可完成安装，真正做到猩猩都能使用.

```
kubectl apply -f config/deploy/install.yaml
```

然后通过 `kubectl get pod -n pixiu-system` 能看到 `pixiu` 已经启动成功.
```
# kubectl get all -n pixiu-system
NAME                                            READY   STATUS    RESTARTS   AGE
pod/pixiu-controller-manager-859c8b94f6-9f8bh   1/1     Running   0          10m
pod/pixiu-daemon-7qf27                          1/1     Running   0          4m40s
```
