# linux 下的常用命令

## 文件传输

### scp命令

1、上传文件格式

scp 本地文件路径 服务器主机名@主机IP:存放路径

例如：

```shell
scp ./test.md root@192.168.10.132:/tmp/
```

2、下载文件格式

scp 服务器主机名@主机IP:下载文件存放路径  本地文件路径

例如：

```shell
scp root@192.168.10.132:/tem/test.md /usr/local/tmp/
```
