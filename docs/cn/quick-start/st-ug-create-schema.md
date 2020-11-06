# 创建 Schema

在 Nebula Graph 中，您必须先有 Schema，再向其中写入点数据和边数据。本文描述如何使用 Nebula Graph 的 **控制台** 或 **Schema** 功能创建 Schema。

> **说明**：您也可以使用 nebula-console 创建 Schema。详细信息，参考 [使用 Docker Compose 部署 Nebula Graph
](https://github.com/vesoft-inc/nebula-docker-compose/blob/master/README_zh-CN.md) 和 [Nebula Graph 快速开始](https://docs.nebula-graph.com.cn/manual-CN/1.overview/2.quick-start/1.get-started/)。

## 前提条件

在 Studio 上创建 Schema 之前，您需要确认以下信息：

- Studio 已经连接到 Nebula Graph 数据库。
- 您的账号拥有 GOD、ADMIN 或 DBA 权限。详细信息，参考 [Nebula Graph 内置角色](https://docs.nebula-graph.com.cn/manual-CN/3.build-develop-and-administration/4.account-management-statements/built-in-roles/)。
- 您已经规划好了 Schema 的要素。
- 已经创建了图空间。
  > **说明**：本示例假设已经创建了图空间。如果您的账号拥有 GOD 权限，也可以在 **控制台** 或 **Schema** 上创建一个图空间。

## 使用 Schema 管理功能创建 Schema

按以下步骤使用 **Schema** 创建 Schema：

1. 创建标签。详细信息，参考 [操作标签](../use-studio/manage-schema/st-ug-crud-tag.md)。
2. 创建边类型。详细信息，参考 [操作边类型](../use-studio/manage-schema/st-ug-crud-edge-type.md)。

## 使用控制台创建 Schema

按以下步骤使用 **控制台** 创建 Schema：

1. 在工具栏里，点击 **控制台** 页签。
2. 在 **当前Space** 中选择一个图空间。在本示例中，选择 **mooc_actions**。

   ![在 当前Space 中选择一个图空间](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-007.png "选择图空间")
3. 在命令行中，依次输入以下语句，并点击 ![表示运行的图标](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-008.png "Run 图标") 图标。

   ```nGQL
    CREATE TAG user (userId int); -- 创建标签 user，带有 1 个属性
    CREATE TAG course (courseId int, courseName string); -- 创建标签 course，带有两个属性
    CREATE EDGE action (actionId int, duration double, label bool, feature0 double, feature1 double, feature2 double, feature3 double); -- 创建边类型，带有 7 个属性
    ```

至此，您已经完成了 Schema 创建。您可以运行以下语句查看标签与边类型的定义是否正确、完整。

```nGQL
SHOW TAGS; -- 列出当前图空间中所有标签
SHOW EDGES; -- 列出当前图空间中所有边类型
DESCRIBE TAG user;
DESCRIBE TAG course;
DESCRIBE EDGE action; -- 查看每种标签和边类型的结构是否正确
```

## 后续操作

创建 Schema 后，您可以开始 [导入数据](st-ug-import-data.md)。
