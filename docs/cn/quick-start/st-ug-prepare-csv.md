# 准备 CSV 文件

Studio 支持通过 CSV 文件批量导入点和边数据。目前仅支持上传 CSV 文件，而且每个 CSV 文件应分别表示点数据或边数据，同时，每个 CSV 文件中不能包含表头行。所以，您需要对源数据集作如下处理：

1. 分别生成 CSV 文件：

   - user.csv：仅包括源数据中的 `userId` 数据。
   - course.csv：仅包括 `courseId` 和 `courseName` 数据。
   - actions.csv：包括 `action` 边类型所有属性对应的数据（`actionId`、`label`、`duration`、`feature0`、`feature1`、`feature2`、`feature3`），并加入边起始点 VID 和终点 VID 的来源（`userId` 和 `courseName`）。其中，因为 `label` 属性是布尔数值，所以，将 1 替换为 `TRUE`，将 0 替换为 `FALSE`。如下图所示。
  ![action.csv 文件中包含 actionId、userId、courseName、duration、feature0、feature1、feature2、feature3、label 列](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-004.png "带有表头行的 actions.csv 文件")

2. 删除所有 CSV 文件中的表头行。
