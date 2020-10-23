# 什么是 Nebula Graph Studio

Nebula Graph Studio（简称 Studio）是一款可以通过 Web 访问的图数据库可视化工具，搭配 Nebula Graph DBMS 使用，为您提供构图、数据导入、编写 nGQL 查询、图探索等一站式服务。即使没有图数据库操作经验，您也可以快速成为图专家。

## 发行版本

Studio 目前有两个发行版本：

- 本地版本：您可以在本地部署 Studio，并连接到部署在本地的 Nebula Graph 数据库。详细信息，参考 [安装部署 Studio](../install-configure/st-ug-install.md)。
- 云服务版本：您可以在 Nebula Graph Cloud Service 上创建 Nebula Graph 数据库实例，并一键直连 Studio。详细信息，参考[《Nebula Graph Cloud Service 用户手册》](https://cloud-docs.nebula-graph.com.cn/cn/posts/manage-instances/dbaas-ug-connect-nebulastudio/ "点击前往 Nebula Graph Cloud Service 用户手册")。

两个发行版本功能基本相同。但是，因为部署方式不同，会有不同的使用限制。详细信息，参考 [使用限制](st-ug-limitations.md)。

## 产品功能

Studio 提供以下功能：

- 灵活的部署方式，满足您的不同需求。您可以在本地部署 Studio 连接 Nebula Graph 数据库，或者在 Nebula Graph Cloud Service 上一键直连云端 Nebula Graph 数据库实例。
- GUI 设计，方便您管理 Nebula Graph 图数据：
  - 借助 **Schema** 管理功能，您可以使用图形界面完成 Schema（模式）创建，使您能快速上手 Nebula Graph 数据库。
  - 借助 **控制台** 功能，您可以使用 nGQL 语句创建 Schema，并对数据执行增删改查操作。
  - 借助 **导入** 功能，通过简单的配置，您即能完成批量点和边数据导入，并能实时查看数据导入日志。
- 图探索，支持可视化展示图数据，使您更容易发现数据之间的关联性，提高数据分析和解读的效率。

## 适用场景

如果您有以下任一需求，都可以使用 Studio：

- 您有一份数据集，想进行可视化图探索或者数据分析。您可以使用 Docker Compose 或者得 Nebula Graph Cloud Service 部署 Nebula Graph 数据库，再使用 Studio 完成可视化操作。
- 您已经安装部署了 Nebula Graph 数据库，并且已经导入数据集，想使用 GUI 工具执行 nGQL 语句查询、可视化图探索或者数据分析。
- 您刚开始学习 nGQL（Nebula Graph Query Language），但是不习惯用命令行工具，更希望使用 GUI 工具查看语句输出的结果。

## 身份验证

Nebula Graph 默认不启动身份验证，此时，您可以使用默认账号和密码（`user` 和 `password`）登录 Studio。如果 Nebula Graph 启用了身份验证，您只能使用指定的账号和密码登录 Studio。

关于 Nebula Graph 的身份验证功能，参考[《Nebula Graph 用户手册》](https://docs.nebula-graph.com.cn/manual-CN/3.build-develop-and-administration/4.account-management-statements/authentication/ "点击前往 Nebula Graph 用户手册")。
