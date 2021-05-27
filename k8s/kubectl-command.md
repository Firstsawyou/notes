# kubectl 命令

```shell
$ kubectl help
kubectl controls the Kubernetes cluster manager.

 Find more information at: https://kubernetes.io/docs/reference/kubectl/overview/

Basic Commands (Beginner):
  create        Create a resource from a file or from stdin.
  expose        使用 replication controller, service, deployment 或者 pod 并暴露它作为一个 新的 Kubernetes
Service
  run           在集群中运行一个指定的镜像
  set           为 objects 设置一个指定的特征

Basic Commands (Intermediate):
  explain       查看资源的文档
  get           显示一个或更多 resources
  edit          在服务器上编辑一个资源
  delete        Delete resources by filenames, stdin, resources and names, or by resources and label selector

Deploy Commands:
  rollout       Manage the rollout of a resource
  scale         Set a new size for a Deployment, ReplicaSet or Replication Controller
  autoscale     自动调整一个 Deployment, ReplicaSet, 或者 ReplicationController 的副本数量

Cluster Management Commands:
  certificate   修改 certificate 资源.
  cluster-info  显示集群信息
  top           Display Resource (CPU/Memory/Storage) usage.
  cordon        标记 node 为 unschedulable
  uncordon      标记 node 为 schedulable
  drain         Drain node in preparation for maintenance
  taint         更新一个或者多个 node 上的 taints

Troubleshooting and Debugging Commands:
  describe      显示一个指定 resource 或者 group 的 resources 详情
  logs          输出容器在 pod 中的日志
  attach        Attach 到一个运行中的 container
  exec          在一个 container 中执行一个命令
  port-forward  Forward one or more local ports to a pod
  proxy         运行一个 proxy 到 Kubernetes API server
  cp            复制 files 和 directories 到 containers 和从容器中复制 files 和 directories.
  auth          Inspect authorization

Advanced Commands:
  diff          Diff live version against would-be applied version
  apply         通过文件名或标准输入流(stdin)对资源进行配置
  patch         使用 strategic merge patch 更新一个资源的 field(s)
  replace       通过 filename 或者 stdin替换一个资源
  wait          Experimental: Wait for a specific condition on one or many resources.
  convert       在不同的 API versions 转换配置文件
  kustomize     Build a kustomization target from a directory or a remote url.

Settings Commands:
  label         更新在这个资源上的 labels
  annotate      更新一个资源的注解
  completion    Output shell completion code for the specified shell (bash or zsh)

Other Commands:
  alpha         Commands for features in alpha
  api-resources Print the supported API resources on the server
  api-versions  Print the supported API versions on the server, in the form of "group/version"
  config        修改 kubeconfig 文件
  plugin        Provides utilities for interacting with plugins.
  version       输出 client 和 server 的版本信息

Usage:
  kubectl [flags] [options]

Use "kubectl <command> --help" for more information about a given command.
Use "kubectl options" for a list of global command-line options (applies to all commands).
```

## 常用命令

1、删除 pod

kubectl delete pod apisix-dashboard-6c57c84f65-8kgxl -n default (不能真正删除，还是存在，需要删除对应的 deployment)

kubectl get deployment -n default
kubectl delete deployment apisix-dashboard -n default

2、查看yaml 配置

kubectl get pod api7-etcd-0 -o yaml

3、显示一个指定 resource 或者 group 的 resources 详情

kubectl describe pod apisix-695dddb5f8-n6qh6
kubectl describe svc apisix-gateway

4、删除 namespace 下面所有的资源（慎重）

kubectl delete all --all -n {namespace}

5、删除指定的 namespace

kubectl delete ns(namespace)  {namespaceName}

6、本地端口映射到应用服务

kubectl port-forward apisix-64476dd584-xkbdp 9080:9080 9180:9180

kubectl port-forward svc/apisix-gateway 9080:80

7、进入 pod 副本

kubectl exec -ti <your-pod-name>  -n <your-namespace>  -- /bin/sh

8、kind 删除集群

kind delete cluster --name apisix

9、进入 docker 容器

docker exec -it 97a0390f1b32 bash

docker exec -ti  <your-container-name>   /bin/sh

10、k8s 节点查看

vi /etc/containerd/config.toml

cat /etc/containerd/config.toml

11、Linux 中命令起别名

alias k=kubectl

12、 watch 一个命令

watch -n 0.5 kubectl get pods

更多使用信息可以通过： `watch` 查看
