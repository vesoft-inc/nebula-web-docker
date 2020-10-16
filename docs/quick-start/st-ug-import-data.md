# 导入数据

准备好 CSV 文件，创建了 Schema 后，您可以使用 **导入** 功能将所有点和边数据上传到 Studio，用于数据查询、图探索和数据分析。

## 前提条件

导入数据之前，需要确认以下信息：

- Studio 已经连接到 Nebula Graph 数据库。
- Nebula Graph 数据库里已经创建了 Schema。
- CSV 文件符合 Schema 要求。
- 您的账号拥有 GOD、ADMIN、DBA 或者 USER 的权限，能往图空间中写入数据。

## 操作步骤

按以下步骤导入数据：

1. 在工具栏里，点击 **导入** 页签。
2. 在 **选择Space** 页面，选择一个图空间，再点击 **下一步** 按钮。
3. 在 **上传文件** 页面，点击 **上传文件** 按钮，并选择需要的 CSV 文件。本示例中，选择 `user.csv`、`course.csv` 和 `actions.csv` 文件。
   > **说明**：您可以一次选择多个 CSV 文件。
   >
4. 在文件列表的 **操作** 列，点击 **预览** 或 **删除**，保证文件信息正确，之后，再点击 **下一步** 按钮。
5. 在 **关联点** 页面，点击 **+ 绑定数据源** 按钮，在对话框中选择点数据文件，并点击 **确认** 按钮。如本示例中的 `user.csv` 或 `course.csv` 文件。
6. 在 **数据源 X** 页签下，点击 **+ Tag** 按钮。
7. 在 **vertexId** 部分，完成以下操作：  
   a. 在 **对应列标** 列，点击 **选择**。  
   ![在数据源中点击“选择”](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-009.png "为 vertexId 选择数据源")  
   b. 在弹出对话框中，选择数据列。在本示例中，`user.csv` 中仅有一列数据用于生成代表用户的 VID，`course.csv` 中选择表示 `courseName` 信息的 **Column 1** 用于生成代表课程的 VID。  
   > **说明**：在同一个图空间中，VID 始终唯一，不可重复。关于 VID 的信息，参考 [Nebula Graph 的点标识符和分区](https://docs.nebula-graph.com.cn/manual-CN/5.appendix/vid-partition/ "点击进入 Nebula Graph 用户手册")。  
   c. 在 **ID Hash** 列，选择 VID 预处理方式：如果源数据是 `int` 类型数据，选择 **保持原值**；如果源数据是 `string`、`double` 或者 `bool` 类型数据，选择 **Hash**。
8. 在 **TAG 1** 部分，完成以下操作：  
   a. 在 **TAG** 下拉列表中，选择数据源对应的标签名称。在本示例中，`user.csv` 文件对应选择 **user**；`course.csv` 文件对应选择 **course**。  
   b. 在显示的属性列表中，点击 **选择**，为标签属性绑定源数据。在本示例中，`user` 标签没有属性，不需要选择数据源；`course` 标签的 `courseId` 属性对应 `course.csv` 文件中的 **Column 0** 列，**类型** 为 **int**，`courseName` 属性对应文件中的 **Column 1** 列，**类型** 为 **string**。  
   ![course类点对应的属性数据源](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-010.png "为点属性选择数据源")  
9. (可选) 如果您有多个标签数据文件，重复步骤 5 到步骤 8。
10. 完成配置后，点击 **下一步**。  
    界面提示 **配置验证成功**，表示标签数据源绑定成功。
11. 在 **关联边** 页面，点击 **+ 绑定数据源** 按钮，在对话框中选择边数据文件，并点击 **确认** 按钮。如本示例中的 `actions.csv` 文件。
12. 在 **Edge X** 页签的 **类型** 下拉列表中，选择边类型名称。本示例中，选择 **action**。
13. 根据边类型的属性，从 `actions.csv` 文件中选择相应的数据列。其中，**srcId** 和 **dstId** 分别表示边的起点与终点，所选择的数据及处理方式必须与相应的 VID 保持一致。本示例中，**srcId** 对应的是表示用户的 VID，**dstId** 对应的是表示课程的 VID。**rank** 为选填项，可以忽略。  
![actions 边对应的属性数据源](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-011.png "为边属性选择数据源")
14. 完成设置后，点击 **下一步** 按钮。
15. 在 **导入** 页面，点击 **导入** 按钮开始导入数据。在 **log** 页面上，您可以看到数据导入进度。导入所需时间因数据量而异。导入过程中，您可以点击 **终止导入** 停止数据导入。当 **log** 页面显示如图所示信息时，表示数据导入完成。  
![log 里最后显示导入操作完成的时间、导入的行数以及操作的行数](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-005.png "导入结束时的 log 信息")

## 后续操作

完成数据导入后，您可以开始 [图探索](st-ug-explore.md)。
