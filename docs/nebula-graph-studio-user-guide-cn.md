# Nebula Graph Studio 用户手册

本手册将指导您在 **Nebula Graph Studio** 中创建图空间、标签、边类型，导入数据以及图探索。

## 概述

**Nebula Graph Studio** 集 `ngql` 查询语言，数据导入以及图探索功能于一身，极大降低了使用 **Nebula Graph** 的门槛。**Nebula Graph Studio** 可以让您随时连接本地或其他设备上的 **Nebula Graph** 服务。

## 前提条件

使用 **Nebula Graph Studio** 前请确保您已：

1. 请确保 docker、**Nebula Graph Studio** 以及 Chrome 浏览器安装在同一主机上，否则无法导入数据。例如，您在Mac上安装了 docker、Chrome 浏览器，但是 **Nebula Graph Studio** 安装在了虚拟机上，那么将无法把数据导入到 **Nebula Graph** 中。

2. [安装 Nebula Graph](https://github.com/vesoft-inc/nebula-docker-compose/blob/master/README_zh-CN.md) 服务且启动 **Nebula Graph**。

3. [安装 docker](https://docs.docker.com/install/) 且启动 docker。

## 安装并启动 **Nebula Graph Studio**

1. 在命令行中输入以下命令，下载 **Nebula Graph Studio** 安装包。

```bash
$ git clone https://github.com/vesoft-inc/nebula-web-docker
```

2. 在命令行中，进入到安装文件夹 `nebula-web-docker`。

3. 输入 `ls -a` 显示安装文件下所有的隐藏文件。

4. 输入 `vi .env` 修改 `.env` 文件中的导入文件的路径。例如，将要导入的文件存放在 `/User/nebula/` 路径下，则 `WORKING_DIR=/Users/nebula`。

5. 文件修改完成后，输入 `:wq`，保存文件并退出。

6. 输入 `docker-compose pull && docker-compose up` 启动 **Nebula Graph Studio** 服务。

```bash
    Creating docker_importer_1 ... done
    Creating docker_client_1   ... done
    Creating docker_web_1      ... done
    Creating docker_nginx_1    ... done
```

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

在创建图 schema 前，单击右侧的**清除** <img width="39" alt="clear_icon" src="https://user-images.githubusercontent.com/40747875/72044761-9e24b600-32ef-11ea-8913-c5e8ca8f2812.png">  图标，清除控制台输入框中的默认查询语句。

1. 在控制台输入框中输入以下语句创建 `NBA` 图空间，并单击**运行** <img width="39" alt="run_icon" src="https://user-images.githubusercontent.com/40747875/72045829-04123d00-32f2-11ea-80a8-b796daaa8583.png"> 图标。

```
CREATE SPACE NBA;
```

**注意**：成功创建 `NBA` 图空间后需要再次单击右侧的**清除**图标来清除该语句。

2. 在控制台输入框中输入以下语句来使用刚刚创建的 `NBA` 图空间，并单击**运行**图标。

```
USE NBA;
```

**注意**：该语句不能清除，在第3步中将继续使用 **USE NBA** 语句。

3. 在控制台输入框中输入以下语句创建 `player`、`team` 点类型，`follow`、`serve` 边类型，并单击**运行**图标。

```
CREATE TAG player (name string, age int);
CREATE TAG team (name string);
CREATE EDGE follow (degree int);
CREATE EDGE serve (start_year int, end_year int);
```

**说明**：到此就完成了图 schema 的创建。

<img width="1545" alt="create_schema" src="https://user-images.githubusercontent.com/40747875/72046081-9f0b1700-32f2-11ea-8d4d-e586a404c065.png">   

## 导入数据

在图 schema 创建完成后，可以导入需要的数据。在本示例中我们准备了两个点数据文件分别是 `player.csv`、`team.csv`，以及两个边文件分别是 `follow.csv`、`serve.csv`。

**注意**：目前仅支持无 header 的 CSV 文件数据导入。

1. 单击**导入**选项卡，进入**初始化**，在 **Spaces** 下拉列表中选择需要的图空间，此处选择 `NBA`。单击**下一步**。

<img width="1545" alt="init" src="https://user-images.githubusercontent.com/40747875/72046564-ab43a400-32f3-11ea-804b-94fbb15af940.png">

2. 在**选择文件**中，单击**选择文件**。此处选中四个文件，分别是 `player.csv`、`team.csv`、`follow.csv` 以及 `serve.csv`。

<img width="1545" alt="select_files" src="https://user-images.githubusercontent.com/40747875/72047071-b0552300-32f4-11ea-9b20-bcc0b210850f.png">

3. 在**类型**列中选择数据类型。在本示例中 `follow.csv` 和 `serve.csv` 文件对应边类型，`player.csv` 和 `team.csv` 文件对应点类型。单击**下一步**。

**说明**：您也可以在**操作**栏下单击**预览**来查看文件的部分数据，或点击**删除**来删除选中的文件。

<img width="1545" alt="file_to_type" src="https://user-images.githubusercontent.com/40747875/72047582-d29b7080-32f5-11ea-8a66-953b23fc2036.png">

4. 在**配置 Vertex** 中，单击**添加 Vertex**。在弹出的窗口中，从**文件名**下拉列表中选择文件名，此处选择 `player.csv`，然后单击**确认**。

<img width="1545" alt="configure_vertex" src="https://user-images.githubusercontent.com/40747875/72048030-d8458600-32f6-11ea-8a78-ca698eb27f6a.png">

5. 单击页面底部的 **+Tag** 按钮，在 **VertexId** 下选择 vertexId 对应的列名，此处我们选择 `column 0`。ID Hash 保留默认选项：`保留原值`。

<img width="1545" alt="vertex_id" src="https://user-images.githubusercontent.com/40747875/72048605-21e2a080-32f8-11ea-8d28-eea5762055a0.png">

6. 在 **TAG** 下拉列表中选择 `player`。然后在对应列中选择 `player` 属性所对应的列。此处 `name` 对应 `column 1`、`age` 对应 `column 2`。

<img width="1545" alt="vertex_prop_map" src="https://user-images.githubusercontent.com/40747875/72048826-9cabbb80-32f8-11ea-9889-882ddd6f19b4.png">

**说明**：重复第4、5、6步，添加 `team.csv` 的 `VertexId` 映射和属性映射，配置完成后单击**下一步**。

7. 在**配置边**中，单击**添加 Edge**。在弹出的窗口中，从**文件名**下拉列表中选择文件名，此处选择 `follow.csv`，然后单击**确认**。

<img width="1545" alt="edge_config" src="https://user-images.githubusercontent.com/40747875/72049268-881bf300-32f9-11ea-8014-7011f2258243.png">

8. 在**类型**下拉列表中选择文件对应的边类型，此处选择 `follow`。

9. 在对应列中选择边的属性所对应的文件列名。此处 `srcId` 对应 `column 0`， `dstId` 对应 `column 1`， `rank` 属性默认忽略，`degree` 属性对应 `column 2`。

<img width="1545" alt="edge_prop_map" src="https://user-images.githubusercontent.com/40747875/72049409-dfba5e80-32f9-11ea-91ed-b7bb092f12b8.png"> 

**说明**：重复第7、8、9步，添加 `serve` 边类型的属性映射，配置完成后单击**下一步**。

10. 单击**导入**，开始导入数据。导入成功后可以看到日志信息。

<img width="1545" alt="import_data" src="https://user-images.githubusercontent.com/40747875/72049709-7b4bcf00-32fa-11ea-9851-2b5f619e2c83.png">

## 图探索

在数据导入完成后，可以开始探索 **Nebula Graph** 中的图数据。

1. 单击**图探索**选项卡，进入图探索。

2. 在 **Spaces** 下拉列表中选择 `NBA`。

3. 单击**添加起点**。

<img width="1545" alt="data_explore" src="https://user-images.githubusercontent.com/40747875/72049921-ec8b8200-32fa-11ea-8026-ba0d04fe3eac.png">

**说明**：您可以选择一个起点或多个起点来查找与之相关联的点。本示例中选择一个起点，该起点的 VertexID 为100。如果您选择多个起点，则按照以下方式输入：

```
100
200
300
```

4. 在弹出的窗口中输入起点的 VertexId 值，此处输入100。单击**确认添加**。

<img width="1545" alt="start_vertex" src="https://user-images.githubusercontent.com/40747875/72050299-c0243580-32fb-11ea-8972-600884420aae.png">

5. 单击点100，然后单击**拓展**。

<img width="1545" alt="click_to_select_a_vertex" src="https://user-images.githubusercontent.com/40747875/72050395-f82b7880-32fb-11ea-95ba-089666660ecb.png">

6. 在 **Edge Type** 下拉列表中选择 `follow` 并单击**拓展**，显示如下关联点。

![cursor_over](https://user-images.githubusercontent.com/40747875/72673599-dd00fb80-3aa7-11ea-9fe9-7d6abb012801.png)


**说明**：将光标移动到 vertex 102 上时将显示该点的所有属性值。