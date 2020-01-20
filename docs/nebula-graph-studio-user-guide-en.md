# Nebula Graph Studio User Guide

This guide will walk you through the process of creating graph spaces, tags, edge types, importing data and graph exploration in **Nebula Graph Studio**.

## Overview

**Nebula Graph Studio** integrates `ngql` query language, data importing and graph exploration, which greatly lowers the entrance to using **Nebula Graph**. **Nebula Graph Studio** allows you to connect to the **Nebula Graph** services on your local computer or other devices at any time.

## Requirements

Please ensure that the following requirements are met before using **Nebula Graph Studio**:

1. Ensure that docker, **Nebula Graph Studio** and Chrome explorer are installed on the same host, otherwise, the data importing function will not work. For example, if you install docker, Chrome explorer on your Mac, but **Nebula Graph Studio** is installed in a virtual machine, then you cannot import data to **Nebula Graph**.

2. [Installed Nebula Graph](https://github.com/vesoft-inc/nebula-docker-compose/blob/master/README.md) services and started **Nebula Graph**.

3. [Installed docker](https://docs.docker.com/install/) and started docker.

## Installing and Starting **Nebula Graph Studio**

1. Execute the following command to download the **Nebula Graph Studio** package.

```bash
$ git clone https://github.com/vesoft-inc/nebula-web-docker
```

2. Change your current directory to the `nebula-web-docker` directory.

3. Enter the `ls -a` command to display all the hidden files in the instllation directory.

4. Enter the `vi .env` command to modify the directory for the files to be imported in the `.env` file. For example, if the files to be imported is stored in the `/User/nebula/` directory, then the directory must be changed to `WORKING_DIR=/Users/nebula`.

5. After the file is modified, enter the `:wq` command to save the file and exit.

6. Enter the `docker-compose pull && docker-compose up` command to start **Nebula Graph Studio** services.

```bash
    Creating docker_importer_1 ... done
    Creating docker_client_1   ... done
    Creating docker_web_1      ... done
    Creating docker_nginx_1    ... done
```

**Note**: The above informtion indicates that **Nebula Graph Studio** has been started successfully.

## Configurating Database

After installing **Nebula Graph Studio**, you need to configure the **Nebula Graph** database and connect to it.

1. In the search box of Chrome explorer, enter `localhost:7001`, and the interface to configure database is displayed.

2. Enter the host address and port number of the **Nebula Graph** service in the **Host** field, for example *192.168.11.100: 3699*. The port number is 3699 by default.

**Note**: The **Host** field does not support addresses and ports such as *127.0.0.1: 3699* or *localhost: 3699*. You must provide a real address for **Nebula Graph** services.

3. Enter the username to log in **Nebula Graph** in the **Username** field. By default is `user`.

4. Enter the password to log in **Nebula Graph** in the **Password** field. By default is `password`.

5. Click **Connect**.

![config_database](https://user-images.githubusercontent.com/40747875/72593339-ab6d2080-393f-11ea-91ab-f4fd07e970f1.png)

## Creating Graph Schema

After successfully connecting to the **Nebula Graph** database, you will be automatically taken to the console page. Entering the `ngql` statement to create a graph schema in the console is similar to create a graph schema on the command line. In this document, we will create a graph space named `NBA`. This graph space contains two tags (also called vertex types), which are `player` and `team`, and two edge types, which are `follow` and `serve`.

Before creating the graph schema, click the **Clear** <img width="39" alt="clear_icon" src="https://user-images.githubusercontent.com/40747875/72044761-9e24b600-32ef-11ea-8913-c5e8ca8f2812.png">  icon on the right to clear the default query in the input box.

1. Enter the following statement in the input box of the console to create the `NBA` graph space and click the **Run** <img width="39" alt="run_icon" src="https://user-images.githubusercontent.com/40747875/72045829-04123d00-32f2-11ea-80a8-b796daaa8583.png"> icon.

```
CREATE SPACE NBA;
```

**Note**: After successfully creating the `NBA` graph space, you need to click the **Clear** icon on the right again to clear the statement.

2. Enter the following statement in the input box of the console to use the `NBA` graph space you just created and click the **Run** icon.

```
USE NBA;
```

**Note**: This statement cannot be cleared, because the **USE NBA** statement will be used in step 3.

3. Enter the following statements in the input box of the console to create the `player` and `team` tags, `follow` and `serve` edge types, and click the **Run** icon.

```
CREATE TAG player (name string, age int);
CREATE TAG team (name string);
CREATE EDGE follow (degree int);
CREATE EDGE serve (start_year int, end_year int);
```

**Note**: The graph schema is completed now.

![schema_created](https://user-images.githubusercontent.com/40747875/72595375-ab235400-3944-11ea-9d30-a48f20fee205.png)

## Importing Data

After the graph schema is created, you can import the required data. In this example we have prepared two vertex files, `player.csv` and `team.csv`, and two edge files, `follow.csv` and `serve.csv`. You can find the four files in the `example` folder.

**Note**: Only support for importing data from CSV files without header.

1. Click the **import** tab and enter **Init**. Select the required graph space in the **Spaces** drop-down list. We select `NBA` here. Click **Next**.

![select_graph](https://user-images.githubusercontent.com/40747875/72596032-22a5b300-3946-11ea-8001-7e27fc005013.png)

2. In the **Select Files** tab, click the **Select Files** button. We select four files: `player.csv`, `team.csv`, `follow.csv` and `serve.csv`.

![select_files](https://user-images.githubusercontent.com/40747875/72596622-3998d500-3947-11ea-9347-016ef8fc7768.png)

3. Select the data type in the **Type** column. In this example, the `follow.csv` and `serve.csv` files correspond to the edge type, and the `player.csv` and `team.csv` files correspond to the vertex type. Click **Next**.

**Note**: You can also click **Preview** under the **Operation** column to view some data of the file, or click **Delete** to delete the selected file.

![match_type](https://user-images.githubusercontent.com/40747875/72597090-fe4ad600-3947-11ea-8681-adf49fc64f4d.png)

4. In the **Config Vertices** tab, click **Add Vertex**. In the pop-up window, select the file name from the **Name** drop-down list. Select `player.csv` here, and click **Confirm**.

![add_vertex](https://user-images.githubusercontent.com/40747875/72597466-d314b680-3948-11ea-92fd-6e40ee1097c4.png)

5. Click the **+Tag** button at the bottom of the page and select the column name corresponding to vertexId under **VertexId**. Here, we select `column 0` and keep **ID Hash** as the default option: `Primitive`.

![add_tag](https://user-images.githubusercontent.com/40747875/72597655-24bd4100-3949-11ea-9822-e4c0b97bc772.png)

6. Select `player` in the **TAG** drop-down list. Then select the columns corresponding to the `player` attributes in the corresponding columns. Here, `name` corresponds to `column 1` and `age` corresponds to `column 2`.

![vertex-schema-match](https://user-images.githubusercontent.com/40747875/72598125-23d8df00-394a-11ea-866e-78521a124582.png)

**Note**: Repeat step 4, 5 and 6 to add the `VertexId` mapping and attributes mapping of `team.csv`, and click **Next** after the configuration is complete.

7. In the **Config Edges** tab, click **Add Edge**. In the pop-up window, select the file name from the **Name** drop-down list. Select `follow.csv` here, and click **Confirm**.

![select_edge](https://user-images.githubusercontent.com/40747875/72598592-0bb58f80-394b-11ea-9298-a36ef1786a9b.png)

8. Select the edge type corresponding to the file in the **Type** drop-down list. We select `follow` here.

9. Select the column name corresponding to the attribute of the edge in the corresponding column. Here `srcId` corresponds to `column 0` and `dstId` corresponds to `column 1`, `rank` attribute is ignored by default, and `degree` attribute corresponds to `column 2`.

![edge-schema-match](https://user-images.githubusercontent.com/40747875/72598965-d3fb1780-394b-11ea-99c8-2fff915f9c9a.png) 

**Note**: Repeat step 7, 8 and 9 to add the attributes mapping for the `serve` edge type. Click **Next** after the configuration is complete.

10. Click **Run Import** to start importing data. You can see the log information after the import is successful.

![log](https://user-images.githubusercontent.com/40747875/72599516-d27e1f00-394c-11ea-8d1a-a0c522372761.png)

## Graph Exploration

After the data importing is complete, you can start exploring the graph data in **Nebula Graph**.

1. Click the **explore** tab to enter graph exploration.

2. Select `NBA` from the **Spaces** drop-down list.

3. Click **Add Vertices**.

![graph_explore](https://user-images.githubusercontent.com/40747875/72599911-8da6b800-394d-11ea-8d3b-f9437bc75645.png)

**Note**: You can select a starting vertex or multiple starting vertices to find the vertices associated with it (them). In this example, we select a starting vertex with a VertexID of 100. If you select multiple starting vertices, enter them as follows:
```
100
200
300
```

4. Enter the VertexId value of the starting vertex in the pop-up window. We enter 100 here. Click **Add**.

![starting-vertex](https://user-images.githubusercontent.com/40747875/72600217-2e957300-394e-11ea-86dd-cdad5460a708.png)

5. Click vertex 100 and then click **Expand**.

![vertex-expand](https://user-images.githubusercontent.com/40747875/72600859-5df8af80-394f-11ea-8989-6c6654fd4609.png)

6. Select `follow` from the **Edge Type** drop-down list and click **Expand** to display the following related vertices.

![show-relation](https://user-images.githubusercontent.com/40747875/72600748-31449800-394f-11ea-8c0b-f95c46f28b60.png)

**Note**: When you move your cursor over vertex 102, all the attributes of it are displayed.