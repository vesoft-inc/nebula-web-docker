# 导入图探索

您可以在 **控制台** 上使用 nGQL 语句查询得到点或边的信息，再借助 **导入图探索** 功能实现查询结果的可视化。

## 支持版本

Studio v1.2.1-beta 及以后版本。请更新版本，详细操作参考 [版本更新](../about-studio/st-ug-check-updates.md)。

## 前提条件

使用导入图探索前，您需要确认以下信息：

- Studio 已经连接到 Nebula Graph 数据库。详细信息参考 [连接数据库](../install-configure/st-ug-connect.md)。
- 已经导入数据集。详细操作参考 [导入数据](../quick-start/st-ug-import-data.md)。

## 导入边数据

按以下步骤将 **控制台** 查询得到的边数据结果导入 **图探索**：

1. 在工具栏里，点击 **控制台** 页签。
2. 在 **当前Space** 中选择一个图空间。在本示例中，选择 **mooc_actions**。
3. 在命令行中，输入查询语句，并点击 ![表示运行的图标](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-008.png "Run 图标") 图标。
   > **说明**：查询结果中必须包括边起点和终点 VID 信息。

   查询语句示例如下：

    ```nGQL
    nebula> GO FROM 56 OVER action YIELD action._src, action._dst;
    ```

    查询结果可以看到 `userId` 为 56 的用户参加了哪些课程。如下图所示。

    ![控制台里查询语句返回的边数据，包括边的起点 VID 和终点 VID](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-040.png "边数据")

4. 点击 **导入图探索** 按钮。
5. 在弹出对话框中，配置如下：
   a. 点击 **边类型**。  
   b. 在 **Edge Type** 字段，填写边类型名称。在本示例中，填写 `action`。  
   c. 在 **Src ID** 字段，选择查询结果中代表边起点 VID 的列名。在本示例中，选择 `action._src`。  
   d. 在 **Dst ID** 字段，选择查询结果中代表边终点 VID 的列名。在本示例中，选择 `action._dst`。  
   e. （可选）如果返回的边数据中有边权重（`rank`）信息，则在 **Rank** 字段，选择代表边权重的列名。如果 **Rank** 字段未设置，默认为 0。  
   f. 完成配置后，点击 **导入** 按钮。  

      ![填写边类型名称，选择代表边起点和终点 VID 的列名](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-041.png "配置边类型信息")
6. 在 **图探索** 页面的弹出窗口中，选择数据插入方式：
   - **增量插入**：在画图板原来的数据基础上插入新的数据。
   - **清除插入**：清除画图板上原来的数据后，再插入新的数据。

数据插入成功后，您可以看到查询得到的边数据的可视化表现。

![在图探索中可视化显示边数据查询结果](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-044.png "可视化边数据查询结果")

## 导入点数据结果

按以下步骤将 **控制台** 查询得到的点数据结果导入 **图探索**：

1. 在工具栏里，点击 **控制台** 页签。
2. 在 **当前Space** 中选择一个图空间。在本示例中，选择 **mooc_actions**。
3. 在命令行中，输入查询语句，并点击 ![表示运行的图标](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-008.png "Run 图标") 图标。
   > **说明**：查询结果中必须包括点的 VID 信息。

   查询语句示例如下：

    ```nGQL
    nebula> FETCH PROP ON * hash("Media History and Theory"); -- 对于本手册中所用数据集，course 类点的 VID 由 courseName 经 Hash() 函数处理得到
    ```

    查询得到 `courseId` 为 `8` 的课程信息。如下图所示。

    ![控制台里查询语句返回的点数据](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-043.png "点数据")

4. 点击 **导入图探索** 按钮。
5. 在弹出对话框中，配置如下：
   a. 点击 **点**。  
   b. 在 **Vertex ID** 字段，选择查询结果中代表点 VID 的列名。在本示例中，选择 `VertexID`。  
   c. 完成配置后，点击 **导入** 按钮。  

      ![选择代表点 VID 的列名](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-042.png "配置点信息")
6. 在 **图探索** 上的弹出窗口中选择数据插入方式：
   - **增量插入**：在画图板原来的数据基础上插入新的数据。
   - **清除插入**：清除画图板上原来的数据后，再插入新的数据。

数据插入成功后，您可以看到查询得到的点数据的可视化表现。

## 后续操作

数据导入图探索后，您可以对数据进行拓展分析。
