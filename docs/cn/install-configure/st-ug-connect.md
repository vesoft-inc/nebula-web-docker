# 连接数据库

安装并启动 Studio 后，您需要连接 Nebula Graph 数据库。本文主要描述如何在本地连接 Nebula Graph 数据库。

使用云服务时，参考[《Nebula Graph Cloud Service 用户手册》](https://cloud-docs.nebula-graph.com.cn/cn/posts/manage-instances/dbaas-ug-connect-nebulastudio/ "点击进入 Nebula Graph Cloud Service 用户手册")。

## 前提条件

在连接数据库前，您需要确认以下信息：

- 部署了 Nebula Graph 查询引擎的服务器 IP 地址以及服务所用端口。

- Nebula Graph 数据库登录账号信息，包括用户名和密码。
  > **说明**：如果在部署 Nebula Graph 时已经启用了身份验证，并且已经创建了不同角色的用户，您只能使用被分配到的账号和密码登录数据库。如果未启用身份验证，您可以使用默认用户名（`user`）和默认密码（`password`）登录数据库。关于启用身份验证，参考 [Nebula Graph 用户手册](https://docs.nebula-graph.com.cn/ "点击进入 Nebula Graph 用户手册")。

## 操作步骤

按以下步骤连接 Nebula Graph 数据库：

1. 在 Studio 的 **配置数据库** 页面上，输入以下信息：
   - **Host**：填写 Nebula Graph 查询引擎的服务器 IP 地址及端口。格式为 `IP地址:3699`。
     > **说明**：如果 Nebula Graph 数据库与 Studio 部署在同一台服务器上，您必须在 **Host** 字段填写这台服务器的真实 IPv4 地址。
   - **用户名** 和 **密码**：根据 Nebula Graph 的身份验证设置填写登录账号和密码。
     - 如果未启用身份验证，可以填写默认用户名 `user` 和默认密码 `password`。
     - 如果已启用身份验证，但是未创建账号信息，您只能以 GOD 角色登录，必须填写 `root` 及对应的密码 `nebula`。
     - 如果已启用身份验证，同时又创建了不同的用户并分配了角色，不同角色的用户使用自己的账号和密码登录。

      ![显示 Nebula Graph Studio 界面，表示连接成功](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-002.png "Nebula Graph Studio 连接成功")
2. 完成设置后，点击 **连接** 按钮。  
   如果您能看到如下图所示界面，表示您已经成功连接到 Nebula Graph 数据库。

    ![显示 Nebula Graph Studio 界面，表示连接成功](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-003.png "Nebula Graph Studio 连接成功")

一次连接会话持续 30 分钟。如果您超过 30 分钟没有操作，会话会断开，您需要重新登录数据库。

## 后续操作

成功连接 Nebula Graph 数据库后，根据账号的权限，您可以选择执行以下操作：

- 如果您以拥有 GOD 或者 ADMIN 权限的账号登录，可以使用 **控制台** [创建 Schema](../quick-start/st-ug-create-schema.md) 或者 [使用 Schema 管理](../use-studio/manage-schema/st-ug-crud-space.md)。
- 如果您以拥有 GOD、ADMIN、DBA 或者 USER 权限的账号登录，可以 [导入数据](../quick-start/st-ug-import-data.md) 或者使用 **控制台** 写入数据。
- 如果您以拥有 GOD、ADMIN、DBA、USER 或者 GUEST 权限的账号登录，可以使用 **控制台** 完成查询操作或者使用 **图探索** 完成图探索或数据分析。
