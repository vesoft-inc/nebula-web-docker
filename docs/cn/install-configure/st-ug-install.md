# 安装 Studio

Studio 支持本地访问和云服务访问。本文主要描述如何在本地安装 Studio。

使用云服务访问时，您不需要安装 Studio，详细信息，参考[《Nebula Graph Cloud Service 用户手册》](https://cloud-docs.nebula-graph.com.cn/cn/posts/manage-instances/dbaas-ug-connect-nebulastudio/ "点击前往 Nebula Graph Cloud Service 用户手册")。

## 前提条件

在安装 Studio 之前，您需要确认以下信息：

- Nebula Graph 服务已经部署并启动。详细信息，参考[《Nebula Graph 用户手册》](https://docs.nebula-graph.io/manual-EN/3.build-develop-and-administration/2.install/1.install-with-rpm-deb/ "点击前往 Nebula Graph 用户手册")。
  > **说明**：您可以使用多种方式部署并启动 Nebula Graph 服务。如果您刚开始使用 Nebula Graph，建议您使用 Docker Compose 部署 Nebula Graph。详细信息，参考 [使用 Docker Compose 部署 Nebula Graph](https://github.com/vesoft-inc/nebula-docker-compose/blob/master/README_zh-CN.md "点击前往 GitHub 网站")。
  >

- 在即将运行 Studio 的机器上安装并启动 Docker Compose。详细信息，参考 [Docker Compose 文档](https://docs.docker.com/compose/install/ "点击即进入 Docker 文档中心")。

## 操作步骤

按以下步骤安装并运行 Studio：

1. 下载 Studio 安装包。

    ```bash
    git clone https://github.com/vesoft-inc/nebula-web-docker
    ```

2. 切换到 `nebula-web-docker` 路径。

    ```bash
    cd path/to/nebula-web-docker
    ```

3. 安装并启动 Studio。

    ```bash
    docker-compose pull && docker-compose up
    ```

    当屏幕返回以下信息时，表示 Studio 已经成功启动。

    ```bash
    Creating docker_importer_1 ... done
    Creating docker_client_1   ... done
    Creating docker_web_1      ... done
    Creating docker_nginx_1    ... done
    ```

4. 启动成功后，在浏览器地址栏输入 `http://localhost:7001`。

    如果您在浏览器窗口中能看到以下登录界面，表示您已经成功安装并启动 Studio。

    ![Nebula Graph Studio 登录界面](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-001.png "Nebula Graph Studio 登录界面")

## 后续操作

进入 Studio 登录界面后，您需要连接 Nebula Graph 数据库。详细信息，参考 [连接数据库](st-ug-connect.md)。
