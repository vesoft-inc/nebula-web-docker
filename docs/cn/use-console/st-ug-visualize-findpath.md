# 查看子图

在 Studio 里，您可以在 **控制台** 上运行 `FIND SHORTEST | ALL PATH` 语句查询得到指定点之间的所有路径或最短路径，然后再通过 **查看子图** 功能将查询得到的路径导入 **图探索** 进行可视化展示。

关于 `FIND SHORTEST | ALL PATH` 语句的详细信息，参考 [nGQL 用户手册](https://docs.nebula-graph.com.cn/manual-CN/2.query-language/4.statement-syntax/4.graph-algorithms/find-path-syntax/ "点击前往 Nebula Graph 网站")。

## 支持版本

Studio v1.2.1-beta 及以后版本。请更新版本，详细操作参考 [版本更新](../about-studio/st-ug-check-updates.md)。

## 前提条件

在 **控制台** 上运行 `FIND PATH` 语句并查看子图之前，您需要确认以下信息：

- Studio 版本为 v1.2.1-beta 及以后版本。
- Studio 已经连接到 Nebula Graph 数据库。详细信息参考 [连接数据库](../install-configure/st-ug-connect.md)。
- 已经导入数据集。详细操作参考 [导入数据](../quick-start/st-ug-import-data.md)。

## 操作步骤

按以下步骤在 **控制台** 运行 `FIND PATH` 语句并将结果导入 **图探索**：

1. 在工具栏里，点击 **控制台** 页签。
2. 在 **当前Space** 中选择一个图空间。在本示例中，选择 **mooc_actions**。
3. 在命令行中，输入 `FIND SHORTEST PATH` 或者 `FIND ALL PATH` 语句，并点击 ![表示运行的图标](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-008.png "Run 图标") 图标。

   查询语句示例如下：

    ```nGQL
    nebula> FIND ALL PATH FROM 1,2,4,6,42 to hash("History of Ecology"),hash("Neurobiology") OVER action; -- 对于本手册中所用数据集，course 类点的 VID 由 courseName 经 Hash() 函数处理得到
    ```

    查询得到如下图所示路径信息。

    ![结果窗口显示返回的路径信息](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-045.png "返回的路径结果")

4. 点击 **查看子图** 按钮。
5. （可选）如果 **图探索** 上画板上已有数据，则选择一种数据插入方式：
   - **增量插入**：在画图板原来的数据基础上插入新的数据。
   - **清除插入**：清除画图板上原来的数据后，再插入新的数据。

数据插入成功后，您可以看到查询结果的可视化表现。

![在画板上显示返回的路径结果](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-046.png "路径结果的可视化表现")

## 后续操作

数据导入图探索后，您可以对数据进行拓展分析。
