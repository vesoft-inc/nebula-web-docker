# 操作图空间

Studio 连接到 Nebula Graph 数据库后，您可以创建或删除图空间。您可以使用 **控制台** 或者 **Schema** 操作图空间。本文仅说明如何使用 **Schema** 操作图空间。

## 支持版本

Studio v1.2.0-beta 及以后版本。请更新版本，详细操作参考 [版本更新](../about-studio/st-ug-check-updates.md)。

## 前提条件

操作图空间之前，您需要确保以下信息：

- Studio 已经连接到 Nebula Graph 数据库。
- 您当前登录的账号拥有创建或删除图空间的权限，即：
  - 如果 Nebula Graph 未开启身份验证，您以默认用户名 `user` 账号和默认密码 `password` 登录。
  - 如果 Nebula Graph 已开启身份验证，您以 `root` 账号及其密码登录。

## 创建图空间

按以下步骤使用 **Schema** 创建图空间：

1. 在工具栏里，点击 **Schema** 页签。
2. 在图空间列表上方，点击 **+ 创建** 按钮。
3. 在 **创建** 页面，完成以下配置：

   a. **名称**：指定图空间名称，本示例中设置为 `mooc_actions`。不可与已有的图空间名称重复。名称命名规则，参考[《nGQL 用户手册》](https://docs.nebula-graph.com.cn/manual-CN/2.query-language/3.language-structure/schema-object-names/ "点击前往 Nebula Graph 网站")。

   b. **选填参数**：分别设置 `partition_num`、`replica_factor`、`charset` 或者 `collate` 的值。在本示例中，四个参数分别设置为 `10`、`1`、`utf8` 和 `utf8_bin`。详细信息，参考 [`CREATE SPACE` 语法](https://docs.nebula-graph.com.cn/manual-CN/2.query-language/4.statement-syntax/1.data-definition-statements/create-space-syntax/ "点击前往 Nebula Graph 网站")。

   在 **对应的nGQL语句** 面板上，您能看到上述设置对应的 nGQL 语句。如下所示：

      ```ngql
      CREATE SPACE mooc_actions (partition_num = 10, replica_factor = 1, charset = utf8, collate = utf8_bin)
      ```

4. 配置确认无误后，点击 **创建** 按钮。
   如果页面回到 **图空间列表**，而且列表中显示刚创建的图空间信息，表示图空间创建成功。

![带有示例配置信息的图空间创建页面](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-015.png "图空间创建页面")

## 删除图空间

按以下步骤使用 **Schema** 删除图空间：

1. 在工具栏里，点击 **Schema** 页签。
2. 在图空间列表里，找到需要删除的图空间，并在 **操作** 列中，点击 ![表示删除的图标](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-017.png "删除") 图标。

   ![在图空间列表中删除指定的图空间](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-016.png "删除图空间")
3. 在弹出对话框中，确认信息，并点击 **确认** 按钮。  
   删除成功后，页面回到 **图空间列表**。

## 后续操作

图空间创建成功后，您可以开始创建或修改 Schema，包括：

- [操作标签](st-ug-crud-tag.md)
- [操作边类型](st-ug-crud-edge-type.md)
- [操作索引](st-ug-crud-index.md)
