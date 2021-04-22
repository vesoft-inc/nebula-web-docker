# 欢迎使用 Nebula Graph Studio

Nebula Graph Studio（简称 Studio）是一款可以通过 Web 访问的图数据库可视化工具，搭配 Nebula Graph DBMS 使用，为您提供构图、数据导入、编写 nGQL 查询、图探索等一站式服务。

![Studio 界面截图](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-024.png "Studio 界面一览")

## 部署

### docker-compose

[安装部署视频教程](https://nebula-website-cn.oss-cn-hangzhou.aliyuncs.com/nebula-blog/deploy-nebula-graph-and-nebula-graph-studio-with-docker.mp4)

运行以下命令部署适用于 Nebula Graph 1.x 或者 2.x 的 Docker 版 Studio：

1. 克隆 `nebula-web-docker` 库。

    ```bash
    git clone https://github.com/vesoft-inc/nebula-web-docker.git
    ```

2. 选择合适的 Studio 版本：
   
| 分支 | 对应 nebula 版本 |
| --- | --- |
| master | latest |
| v2 | 2.0 GA |
| v2-rc | 2.0-rc |
| v1 |  1.x |
```
// 以 nebula 2.0 GA 为例
git checkout v2
```
1. 拉取 Studio 的 Docker 镜像。

```bash
docker-compose pull
```

2. 启动 Studio。其中，`-d` 表示在后台运行容器。

    ```bash
    docker-compose up -d
    ```
  
    如果界面返回以下信息，说明 Studio 已经完成部署并启动。

    ```bash
    Creating docker_importer_1 ... done
    Creating docker_client_1   ... done
    Creating docker_web_1      ... done
    Creating docker_nginx_1    ... done
    ```

在 Chrome 浏览器中，输入 `localhost:7001` 访问 Studio。如果在浏览器窗口中看到以下登录界面，表示您已经成功部署并启动 Studio。

![Nebula Graph Studio 登录界面](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-001.png "Nebula Graph Studio 登录界面")

3. 停止服务
```
// 当docker-compose是-d模式运行时
$ docker-compose down
```

### RPM
| 安装包 | nebula版本 |
| ----- | ----- |
| [nebula-graph-studio-2.1.9-1.x86_64.rpm](https://oss-cdn.nebula-graph.com.cn/nebula-graph-studio/nebula-graph-studio-2.1.9-1.x86_64.rpm) |  2.0 GA |
| [nebula-graph-studio-1.2.7-1.x86_64.rpm](https://oss-cdn.nebula-graph.com.cn/nebula-graph-studio/nebula-graph-studio-1.2.7-1.x86_64.rpm) |  1.x |

#### 环境依赖
- Node.js (v10.16.0 +)
- lsof

#### 安装
以 Nebula 2.0GA 版本为例
```
$ sudo rpm -i nebula-graph-studio-2.1.9-1.x86_64.rpm
```
#### 删除
```
$ sudo rpm -e nebula-graph-studio-2.1.9-1.x86_64.rpm
```

#### 配套脚本
```
// 手动启动服务
$ bash /usr/local/nebula-graph-studio/scripts/start.sh

// 手动停止服务
$ bash /usr/local/nebula-graph-studio/scripts/stop.sh
```

## 连接 Nebula Graph

按以下说明连接 Nebula Graph v2.x：

1. 确认 Nebula Graph 2.x 已经完成部署。详细信息参考 [Deploy Nebula Graph with Docker Compose](https://docs.nebula-graph.io/2.0/2.quick-start/2.deploy-nebula-graph-with-docker-compose/ "Click to go to Nebula Graph website") 或者 [Install Nebula Graph by compiling the source code](https://docs.nebula-graph.io/2.0/4.deployment-and-installation/2.compile-and-install-nebula-graph/1.install-nebula-graph-by-compiling-the-source-code/ "Click to go to Nebula Graph website")。
   > **说明**：如果您使用 Docker Compose 部署 Nebula Graph v2.0.0-alpha，则必须重新克隆 nebula-docker-compose 仓库以更新 Docker 配置文件。
2. 连接 Nebula Graph v2.x。详细信息参考 [Nebula Graph Studio 用户手册](https://github.com/vesoft-inc/nebula-docs-cn/blob/master/nebula-studio/deploy-connect/st-ug-connect.md "点击前往 GitHub")。

按以下说明连接 Nebula Graph v1.x：

1. 确认 Nebula Graph v1.x 已经完成部署。详细信息参考 [Nebula Graph 用户手册](https://docs.nebula-graph.com.cn/manual-CN/3.build-develop-and-administration/1.build/1.build-source-code/ "点击前往 Nebula Graph 网站")。
2. 连接 Nebula Graph v1.x。详细信息参考 [Nebula Graph Studio 用户手册](https://docs.nebula-graph.com.cn/nebula-studio/deploy-connect/st-ug-connect/ "点击前往 Nebula Graph 网站")。

## 用户手册

观看 [两分钟 Studio 操作介绍视频](https://www.bilibili.com/video/BV1h54y1C7bf "点击前往 bilibili 网站") 迅速了解 Studio 操作。

关于 Studio 的详细信息，参考：

- [用户手册](https://docs.nebula-graph.com.cn/nebula-studio/about-studio/st-ug-what-is-graph-studio/ "点击前往 Nebula Graph 网站")
- [User Manual](https://docs.nebula-graph.io/1.1/nebula-studio/about-studio/st-ug-what-is-graph-studio/ "Click to go to Nebula Graph website")

## 最新更新

查看以下文件确认 Studio 最新功能：

- [更新日志](docs/CHANGELOG-zh.md)
- [Changelog](docs/CHANGELOG-en.md)

## 问题反馈

如果您在使用 Studio 时碰到任何问题，欢迎前往 [Nebula Graph 官方论坛](https://discuss.nebula-graph.com.cn/ "点击前往 Nebula Graph 官方论坛") 提问。

## 联系方式

- 访问官网 [Home Page](http://nebula-graph.io/)
- [![WeiXin](https://img.shields.io/badge/WeChat-%E5%BE%AE%E4%BF%A1-brightgreen)](https://user-images.githubusercontent.com/38887077/67449282-4362b300-f64c-11e9-878f-7efc373e5e55.jpg)
- [![Sina Weibo](https://img.shields.io/badge/Weibo-%E5%BE%AE%E5%8D%9A-red)](https://weibo.com/p/1006067122684542/home?from=page_100606&mod=TAB#place)
- email: info@vesoft.com
