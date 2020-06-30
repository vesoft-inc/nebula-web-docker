# Nebula Graph Studio 用户手册

本手册将指导您在 **Nebula Graph Studio** 中创建图空间、标签、边类型，导入数据以及图探索。

## 概述

**Nebula Graph Studio** 集 nGQL 查询语言，数据导入以及图探索功能于一身，极大降低了使用 **Nebula Graph** 的门槛。**Nebula Graph Studio** 可以让您随时连接本地或其他设备上的 **Nebula Graph** 服务。

## 前提条件

使用 **Nebula Graph Studio** 前请确保您已：

1. [安装 Nebula Graph](https://github.com/vesoft-inc/nebula-docker-compose/blob/master/README_zh-CN.md) 服务且启动 **Nebula Graph**。此处我们推荐使用 [Nebula Graph Docker](https://github.com/vesoft-inc/nebula-docker-compose/blob/master/README_zh-CN.md)安装。

2. [安装 docker](https://docs.docker.com/install/) 且启动 docker。

## 安装并启动 **Nebula Graph Studio**

1. 在命令行中输入以下命令，下载 **Nebula Graph Studio** 安装包。

```bash
$ git clone https://github.com/vesoft-inc/nebula-web-docker
```

2. 在命令行中，进入到安装文件夹 `nebula-web-docker`。

3. 输入 `docker-compose pull && docker-compose up` 启动 **Nebula Graph Studio** 服务。

```bash
    Creating docker_importer_1 ... done
    Creating docker_client_1   ... done
    Creating docker_web_1      ... done
    Creating docker_nginx_1    ... done
```

4. 启动成功，访问: http://0.0.0.0:7001

**说明**：出现以上信息则表示 **Nebula Graph Studio** 启动成功。

## 配置数据库

在成功安装 **Nebula Graph Studio** 后，需要配置 **Nebula Graph** 数据库并连接到该数据库。

1. 在 Chrome 浏览器搜索框中输入`localhost:7001`，出现配置数据库界面。

2. 在 **Host** 字段输入 **Nebula Graph** 服务所在的主机地址和端口号，例如 *192.168.11.100:3699*。默认情况下端口号为：3699。

**注意**：**Host** 字段不支持输入 *127.0.0.1:3699* 或 *localhost:3699* 类型的地址和端口，必须提供一个真实的 **Nebula Graph** 服务地址。

3. 在**用户名**字段输入登录 **Nebula Graph** 的用户名称，默认为 user。

4. 在**密码**字段输入登录 **Nebula Graph** 的密码，默认为 password。

5. 单击**连接**。

![configure_database](https://user-images.githubusercontent.com/40747875/72044103-df1bcb00-32ed-11ea-8e6d-708ef06d8ecf.png)

## 创建图 Schema

在成功连接到 **Nebula Graph** 图数据库后，将自动进入到控制台页面。在控制台中输入 `ngql` 语句来创建图 schema 和命令行中输入 `ngql` 语句来创建图 schema 类似。在本文档示例中我们将创建一个名叫 `NBA` 的图空间，该图空间包含了两个 tag（也称作点类型）分别是 `player`、`team`，以及两个边类型分别是 `follow`、`serve`。

在创建图 schema 前，单击右侧的**清除** <img width="39" alt="clear_icon" src="https://user-images.githubusercontent.com/42762957/85966745-44c25780-b9f3-11ea-862c-335c1525cae6.png">  图标，清除控制台输入框中的默认查询语句。

1. 在控制台输入框中输入以下语句创建 `NBA` 图空间，并单击**运行** <img width="39" alt="run_icon" src="https://user-images.githubusercontent.com/40747875/72045829-04123d00-32f2-11ea-80a8-b796daaa8583.png"> 图标。

```ngql
CREATE SPACE NBA;
```

**注意**：成功创建 `NBA` 图空间后需要再次单击右侧的**清除**图标来清除该语句。

2. 在当前 Space 选择刚创建的 `NBA` 图空间，这相当于在控制台输入框中输入以下语句使用图空间，并单击**运行**图标。

```ngql
USE NBA;
```

3. 在控制台输入框中输入以下语句创建 `player`、`team` 点类型，`follow`、`serve` 边类型，并单击**运行**图标。

```ngql
CREATE TAG player (name string, age int);
CREATE TAG team (name string);
CREATE EDGE follow (degree int);
CREATE EDGE serve (start_year int, end_year int);
```

**说明**：到此就完成了图 schema 的创建。

<img width="1545" alt="create_schema" src="https://user-images.githubusercontent.com/40747875/72046081-9f0b1700-32f2-11ea-8d4d-e586a404c065.png">

## 导入数据

在图 schema 创建完成后，可以导入需要的数据。在本示例中我们准备了两个点数据文件分别是 `player.csv`、`team.csv`，以及两个边文件分别是 `follow.csv`、`serve.csv`。示例数据点击[这里](https://github.com/vesoft-inc/nebula-web-docker/tree/master/example)。

**注意**：目前仅支持无 header 的 CSV 文件数据导入。

1. 单击**导入**选项卡，进入**初始化**，在 **Spaces** 下拉列表中选择需要的图空间，此处选择 `NBA`。单击**下一步**。

<img width="1545" alt="init" src="https://user-images.githubusercontent.com/42762957/85967401-f1e99f80-b9f4-11ea-9b45-6fe900c86da8.png">

2. 在**选择文件**中，单击**选择文件**。此处选中四个文件，分别是 `player.csv`、`team.csv`、`follow.csv` 以及 `serve.csv`。单击**下一步**。

<img width="1545" alt="select_files" src="https://user-images.githubusercontent.com/40747875/72047071-b0552300-32f4-11ea-9b20-bcc0b210850f.png">

**说明**：您也可以在**操作**栏下单击**预览**来查看文件的部分数据，或点击**删除**来删除选中的文件。

<img width="1545" alt="file_to_type" src="https://user-images.githubusercontent.com/42762957/85967772-cfa45180-b9f5-11ea-894e-1a26cd98941f.png">

3. 在**关联点** 中，单击**绑定数据源**。在弹出的窗口中，从**文件名**下拉列表中选择文件名，此处选择 `player.csv`，然后单击**确认**。

<img width="1545" alt="configure_vertex" src="https://user-images.githubusercontent.com/40747875/72048030-d8458600-32f6-11ea-8a78-ca698eb27f6a.png">

4. 单击页面底部的 **+Tag** 按钮，在 **VertexId** 下选择 vertexId 对应的列名，此处我们选择 `column 0`。ID Hash 保留默认选项：`保留原值`。

<img width="1545" alt="vertex_id" src="https://user-images.githubusercontent.com/42762957/85968468-d16f1480-b9f7-11ea-8413-85fef81a3198.png">

5. 在 **TAG** 下拉列表中选择 `player`。然后在对应列中选择 `player` 属性所对应的列。此处 `vertexId` 对应 `column 0`、`name` 对应 `column 1`、`age` 对应 `column 2`。

<img width="1545" alt="vertex_prop_map" src="https://user-images.githubusercontent.com/42762957/85968829-aa651280-b9f8-11ea-9d10-e2a99be787f4.png">

**说明**：重复第 3、4、5 步，添加 `team.csv` 的 `VertexId` 映射和属性映射，配置完成后单击**下一步**。

6. 在**关联边**中，单击**绑定数据源**。在弹出的窗口中，从**文件名**下拉列表中选择文件名，此处选择 `follow.csv`，然后单击**确认**。

<img width="1545" alt="edge_config" src="https://user-images.githubusercontent.com/40747875/72049268-881bf300-32f9-11ea-8014-7011f2258243.png">

7. 在**类型**下拉列表中选择文件对应的边类型，此处选择 `follow`。

8. 在对应列中选择边的属性所对应的文件列名。此处 `srcId` 对应 `column 0`， `dstId` 对应 `column 1`， `rank` 属性默认忽略，`degree` 属性对应 `column 2`。

<img width="1545" alt="edge_prop_map" src="https://user-images.githubusercontent.com/42762957/85969686-f5802500-b9fa-11ea-8047-ed67e7d7bfcd.png">

**说明**：重复第 6、7、8 步，添加 `serve` 边类型的属性映射，配置完成后单击**下一步**。

9. 单击**导入**，开始导入数据。导入成功后可以看到日志信息。

<img width="1545" alt="import_data" src="https://user-images.githubusercontent.com/40747875/72049709-7b4bcf00-32fa-11ea-9851-2b5f619e2c83.png">

## 图探索

在数据导入完成后，可以开始探索 **Nebula Graph** 中的图数据。

1. 单击**图探索**选项卡，进入图探索。

2. 在 **Spaces** 下拉列表中选择 `NBA`。

3. 单击**添加起点**。

<img width="1545" alt="data_explore" src="https://user-images.githubusercontent.com/42762957/85970352-d5516580-b9fc-11ea-8641-a3311fc58aaf.png">

**说明**：您可以选择一个起点或多个起点来查找与之相关联的点。本示例中选择一个起点，该起点的 VertexID 为100。如果您选择多个起点，则按照以下方式输入：

```ngql
100
200
300
```

如果所选点不存在，则会提示不存在，且无法添加。

4. 在弹出的窗口中输入起点的 VertexId 值，此处输入100。单击**确认添加**。

<img width="1545" alt="start_vertex" src="https://user-images.githubusercontent.com/42762957/85970947-81478080-b9fe-11ea-89d3-078c44ba1346.png">

5. 单击点100，然后单击**拓展**。

<img width="1545" alt="click_to_select_a_vertex" src="https://user-images.githubusercontent.com/42762957/85971086-d2f00b00-b9fe-11ea-82c0-5464efe8a1a3.png">

6. 在 **Edge Type** 下拉列表中选择 `follow` 并单击**拓展**，显示如下关联点。

![cursor_over](https://user-images.githubusercontent.com/42762957/85976248-b2c74880-ba0c-11ea-8d7d-6068f2fc4c42.png)

**说明**：将光标移动到 vertex 102 上时将显示该点的所有属性值。

7. 点击**显示**，此处选中标签 player 的 name 属性，显示效果见下图。

![show](https://user-images.githubusercontent.com/42762957/85976397-12255880-ba0d-11ea-8618-172d0134b6e0.png)
