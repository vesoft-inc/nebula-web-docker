# 什么是 Nebula Graph&reg; Studio

Nebula Graph&reg; Studio（简称 Studio）是由欧若数网开发的一款图数据库可视化工具，搭配 Nebula Graph DBMS 使用。您可以使用它导入图数据集、执行 nGQL&trade; 语句查询、探索图数据等。即使没有图数据库操作经验，您也可以快速成为图专家。

## 产品特点

【TODO】

## 适用场景

如果您有以下任一需求，都可以使用 Studio：

- 您有一份数据集，想进行可视化图探索或者数据分析。您可以使用 Docker Compose 或者得 Nebula Graph Cloud Service 部署 Nebula Graph 数据库，再使用 Studio 完成可视化操作。
- 您已经安装部署了 Nebula Graph 数据库，并且已经导入数据集，想使用 GUI 工具执行 nGQL 语句查询、可视化图探索或者数据分析。
- 您刚开始学习 nGQL&trade;（Nebula Graph Query Language），但是不习惯用命令行工具，更希望使用 GUI 工具查看语句输出的结果。

## 身份验证

Nebula Graph 默认不启动身份验证，此时，您可以使用默认账号和密码（`user` 和 `password`）登录 Studio。

如果 Nebula Graph 启用了身份验证，您只能使用指定的账号和密码登录 Studio。

关于 Nebula Graph 的身份验证功能，参考[《Nebula Graph 用户手册》](https://docs.nebula-graph.com.cn/manual-CN/3.build-develop-and-administration/4.account-management-statements/authentication/ "点击前往 Nebula Graph 用户手册")。
