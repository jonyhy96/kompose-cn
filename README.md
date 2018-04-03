# Kompose (Kubernetes + Compose)

[![Build Status Widget]][Build Status] [![Coverage Status Widget]][Coverage Status] [![GoDoc Widget]][GoDoc]  [![GoReportCard Widget]][GoReportCardResult]

`kompose` 是一个方便熟悉 `docker-compose`工具的开发者向 [Kubernetes](http://kubernetes.io)迁移的工具. `kompose` 将一个dockercompose.yml文件解析成kubernetes的资源。

`kompose` 是一个让你十分方便的把本地的Docker应用部署到kubernetes上管理的工具. 将dockercompose.yml中的对象转换成kubernetes资源的结果可能并不准确，但是对于熟悉在kubernetes上部署应用有着很大的帮助。

## 使用方法

将[`docker-compose.yaml`](https://raw.githubusercontent.com/kubernetes/kompose/master/examples/docker-compose.yaml) 对象转换成kubernetes资源只需一行命令:

```sh
$ kompose convert -f docker-compose.yaml
INFO Kubernetes file "frontend-service.yaml" created         
INFO Kubernetes file "redis-master-service.yaml" created     
INFO Kubernetes file "redis-slave-service.yaml" created      
INFO Kubernetes file "frontend-deployment.yaml" created      
INFO Kubernetes file "redis-master-deployment.yaml" created  
INFO Kubernetes file "redis-slave-deployment.yaml" created 
```

其他例子包含在 _examples_ [文件](./examples)内。

## 安装

我们有许多种方法安装Kompose.我们更倾向与从GitHub release中下载打包好的二进制执行程序。

所有安装Kompose的方法列在 [installation.md](/docs/installation.md) 文件内。

下载方法:
  - [Binary (推荐)](/docs/installation.md#github-release)
  - [Go](/docs/installation.md#go)
  - [CentOS](/docs/installation.md#centos)
  - [Fedora](/docs/installation.md#fedora)
  - [macOS (Homebrew)](/docs/installation.md#macos)
  - [Windows](/docs/installation.md#windows)

#### 安装二进制执行文件

Kompose 迭代周期为三个星期,你可以在这里找到现有的发行版本 [GitHub release page](https://github.com/kubernetes/kompose/releases).

__Linux and macOS:__

```sh
# Linux
curl -L https://github.com/kubernetes/kompose/releases/download/v1.11.0/kompose-linux-amd64 -o kompose

# macOS
curl -L https://github.com/kubernetes/kompose/releases/download/v1.11.0/kompose-darwin-amd64 -o kompose

chmod +x kompose
sudo mv ./kompose /usr/local/bin/kompose
```

__Windows:__

从[GitHub](https://github.com/kubernetes/kompose/releases/download/v1.11.0/kompose-windows-amd64.exe)下载打包好的二进制执行程序并添加到你的环境变量中。

## Shell 自动化安装

我们支持使用Bash和Zsh自动化安装。

```sh
# Bash (add to .bashrc for persistence)
source <(kompose completion bash)

# Zsh (add to .zshrc for persistence)
source <(kompose completion zsh)
```

## 编译部署Kompose

### 使用 `go` 语言编译
__环境需求:__
1. [make](https://www.gnu.org/software/make/)
2. [Golang](https://golang.org/) v1.6 或更高版本
3. 正确设置 `GOPATH` ，详情可见 [SettingGOPATH](https://github.com/golang/go/wiki/SettingGOPATH) 

__步骤:__
1. 克隆源码
```console
$ git clone https://github.com/kubernetes/kompose.git $GOPATH/src/github.com/kubernetes/kompose
```
2. 使用`make`构建
```console
$ make bin
```
3. 或者使用`go`构建
```console
$ go build -o kompose main.go
```
4. 测试你的结果
```console
$ make test
```

## 文档

文档可以在 [kompose.io](http://kompose.io) 和 [docs](https://github.com/kubernetes/kompose/tree/master/docs) 找到。

以下列表包含所有可用文档:

- [快速开始](docs/getting-started.md)
- [安装](docs/installation.md)
- [用户指引](docs/user-guide.md)
- [转换](docs/conversion.md)
- [体系结构](docs/architecture.md)
- [研发](docs/development.md)

## 社区、讨论、贡献和支持

__Issues:__ 如果你发现了一个问题，请[提交它](https://github.com/kubernetes/kompose/issues)。

__Kubernetes 社区:__ 作为Kubernetes系统的一部分，我们遵循了Kubernetes的社区原则。详见 [社区](http://kubernetes.io/community/)。

__交流(Slack):__ 我们一直活跃在 [Slack](http://slack.kubernetes.io#kompose)上你可以通过 #kompose 频道联系我们。

## 发展路线

你可以在 [ROADMAP.md](/ROADMAP.md) 找到我们最新版本的发展路线。

### 准则

作为Kubernetes 社区成员，受到[Kubernetes 行为准则的约束](code-of-conduct.md).

[Build Status]: https://travis-ci.org/kubernetes/kompose
[Build Status Widget]: https://travis-ci.org/kubernetes/kompose.svg?branch=master
[GoDoc]: https://godoc.org/github.com/kubernetes/kompose
[GoDoc Widget]: https://godoc.org/github.com/kubernetes/kompose?status.svg
[Coverage Status Widget]: https://coveralls.io/repos/github/kubernetes/kompose/badge.svg?branch=master
[Coverage Status]: https://coveralls.io/github/kubernetes/kompose?branch=master
[GoReportCard Widget]: https://goreportcard.com/badge/github.com/kubernetes/kompose
[GoReportCardResult]: https://goreportcard.com/report/github.com/kubernetes/kompose
