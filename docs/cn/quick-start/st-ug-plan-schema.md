# 规划 Schema

在使用 Studio 之前，您需要先根据 Nebula Graph 数据库的要求规划您的 Schema（模式）。

 Schema 至少要包含以下要素：

* 标签（Tag，即点类型），以及每种标签的属性。
* 边类型（Edge Type），以及每种边类型的属性。

本文以美国 Stanford Network Analysis Platform (SNAP) 提供的 [Social Network: MOOC User Action Dataset](https://snap.stanford.edu/data/act-mooc.html "点击前往 Stanford Network Analysis Platform (SNAP)网站") 为基础，并在其中加入由公开网络上获取的不重复的 97 个课程名称，说明如何规划 Schema。

下表列出了 Schema 要素。

| 要素  | 名称  | 属性名称 (数据类型)  |  说明  |
| :---  | :---  | :---  | :---  |
| 标签  | **user**  | `userId` (`int`) <br /> 将使用 `userId` 生成这类点数据的 VID。 | 表示指定 MOOC 平台的用户。  |
| 标签  | **course** | - `courseId` (`int`)<br /> - `courseName` (`string`) <br />本示例中将使用 `courseName` 的值通过 `Hash()` 函数生成这类点数据的 VID。因为 Nebula Graph 要求同一个图空间中所有点的 VID 必须始终唯一，而 `courseId` 与部分 **user** 类 VID 重复，所以，不能使用 `courseId` 生成 **course** 类点数据的 VID。 | 表示指定 MOOC 平台上的课程。  |
| 边类型  | **action**  | - `actionId` (`int`) <br /> - `duration` (`double`)：代表源数据中的 _timestamp_ 数据，表示行为持续时间 <br /> - `label` (`bool`)：表示 **user** 完成一个行为后是否退出了课程 <br /> - `feature0` (`double`) <br /> - `feature1` (`double`) <br /> - `feature2` (`double`) <br /> - `feature3` (`double`) |  表示用户参与课程的行为，分别用参与活动的持续时间、参与后用户是否退出了 MOOC 平台以及行为的四个维度（feature）来描述。其中，`label` 为 `true` 表示退出 MOOC 平台，为 `false` 表示未退出平台。 |

下图说明示例中 **user** 类点与 **course** 类点之间如何发生关系（**action**）。

![用户在 MOOC 平台上参加课程](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-006.png "示例中 user 与 course 的关系")
