# 操作索引

您可以为标签和边类型创建索引，使得图查询时可以从拥有共同属性的同一类型的点或边开始遍历，使大型图的查询更为高效。Nebula Graph 支持两种类型的索引：标签索引和边类型索引。您可以选择使用 **控制台** 或者 **Schema** 操作索引。本文仅说明如何使用 **Schema** 操作索引。

> **说明**：一般在创建了标签或者边类型之后即可创建索引，但是，索引会影响写性能，所以，建议您先导入数据，再批量重建索引。关于索引的详细信息，参考[《nGQL 用户手册》](https://docs.nebula-graph.com.cn/manual-CN/2.query-language/4.statement-syntax/1.data-definition-statements/ "点击前往 Nebula Graph 网站")。

## 支持版本

Studio v1.2.0-beta 及以后版本。请更新版本，详细操作参考 [版本更新](../about-studio/st-ug-check-updates.md)。

## 前提条件

在 Studio 上操作索引之前，您必须确认以下信息：

- Studio 已经连接到 Nebula Graph 数据库。
- 图空间、标签和边类型已经创建。
- 您当前登录的账号拥有 GOD、ADMIN 或者 DBA 的权限。

## 创建索引

按以下步骤使用 **Schema** 创建索引：

1. 在工具栏中，点击 **Schema** 页签。
2. 在 **图空间列表** 中，找到图空间，点击图空间名称或者在 **操作** 列中点击 ![表示设置的图标](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-018.png "设置") 图标。
3. 在 **当前图空间** 里确认图空间名称。您也可以通过选择图空间名称切换图空间。
4. 点击 **索引** 页签，再点击 **创建** 按钮。
5. 在 **创建** 页面上，完成以下设置：

   a. **索引类型**：确认或修改索引类型，即 **标签** 或者 **边类型**。本示例中选择 **边类型**。

   b. **名称**：选择要创建索引的标签或边类型名称。本示例中选择 **action**。

   c. **索引名称**：按规定指定索引名称。本示例中输入 **action_index**。

   d. **索引属性**：点击 **添加**，在 **选择关联的属性** 列表里选择需要索引的属性，并点击 **确定** 按钮。如果需要关联多个属性，重复这一步操作。您可以按界面提示重排索引属性的顺序。本示例中选择 `label` 和 `actionId`。
   > **说明**：索引属性的顺序会影响 `LOOKUP` 语句的查询结果。详细信息，参考 [《nGQL 用户手册》](https://docs.nebula-graph.com.cn/manual-CN/2.query-language/4.statement-syntax/2.data-query-and-manipulation-statements/lookup-syntax/#faq "点击前往 Nebula Graph 网站")。
6. 完成设置后，在 **对应的 nGQL**面板，您能看到与上述配置等价的 nGQL 语句。  
![为边类型 action 创建索引](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-023.png "创建索引")

1. 确认无误后，点击 **+ 创建** 按钮。
   如果索引创建成功，**定义属性**面板会显示这个索引的属性列表。

## 查看索引

按以下步骤使用 **Schema** 查看索引：

1. 在工具栏中，点击 **Schema** 页签。
2. 在 **图空间列表** 中，找到图空间，点击图空间名称或者在 **操作** 列中点击 ![表示设置的图标](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-018.png "设置") 图标。
3. 在 **当前图空间** 里确认图空间名称。您也可以通过选择图空间名称切换图空间。
4. 点击 **索引** 页签，在列表左上方，选择需要查看的索引类型。
5. 在列表中，找到需要查看的索引，点击索引所在行。界面上即列出索引相关的所有属性。

## 删除索引

按以下步骤使用 **Schema** 删除索引：

1. 在工具栏中，点击 **Schema** 页签。
2. 在 **图空间列表** 中，找到图空间，点击图空间名称或者在 **操作** 列中点击 ![表示设置的图标](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-018.png "设置") 图标。
3. 在 **当前图空间** 里确认图空间名称。您也可以通过选择图空间名称切换图空间。
4. 点击 **索引** 页签，找到需要修改的索引，并在 **操作** 列中，点击 ![表示删除的图标](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-017.png "删除") 图标。
