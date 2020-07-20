# Nebula Graph Studio User Guide

This guide will walk you through the process of creating graph spaces, tags, edge types, importing data and graph exploration in **Nebula Graph Studio**.

## Overview

**Nebula Graph Studio** integrates nGQL query language, data importing and graph exploration, which greatly lowers the entrance to using **Nebula Graph**. **Nebula Graph Studio** allows you to connect to the **Nebula Graph** services on your local computer or other devices at any time.

## Requirements

Please ensure that the following requirements are met before using **Nebula Graph Studio**:

1. [Installed Nebula Graph](https://github.com/vesoft-inc/nebula-docker-compose/blob/master/README.md) services and started **Nebula Graph**. Here we recommend using [Nebula Graph Docker](https://github.com/vesoft-inc/nebula-docker-compose/blob/master/README.md) for installation.

2. [Installed docker](https://docs.docker.com/install/) and started docker.

## Installing and Starting **Nebula Graph Studio**

1. Execute the following command to download the **Nebula Graph Studio** package.

```bash
$ git clone https://github.com/vesoft-inc/nebula-web-docker
```

2. Change your current directory to the `nebula-web-docker` directory.

3. Enter the `docker-compose pull && docker-compose up` command to start **Nebula Graph Studio** services.

4. Sucess，visit: http://0.0.0.0:7001

```bash
    Creating docker_importer_1 ... done
    Creating docker_client_1   ... done
    Creating docker_web_1      ... done
    Creating docker_nginx_1    ... done
```

**Note**: The above information indicates that **Nebula Graph Studio** has been started successfully.

## Configuring Database

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

Before creating the graph schema, click the **Clear** <img width="39" alt="clear_icon" src="https://user-images.githubusercontent.com/42762957/85966745-44c25780-b9f3-11ea-862c-335c1525cae6.png">  icon on the right to clear the default query in the input box.

1. Enter the following statement in the input box of the console to create the `NBA` graph space and click the **Run** <img width="39" alt="run_icon" src="https://user-images.githubusercontent.com/40747875/72045829-04123d00-32f2-11ea-80a8-b796daaa8583.png"> icon.

```ngql
CREATE SPACE NBA;
```

**Note**: After successfully creating the `NBA` graph space, you need to click the **Clear** icon on the right again to clear the statement.

2. Choose the `NBA` graph space you just created in the Current Space column to use it and click the **Run** icon.

![image](https://user-images.githubusercontent.com/42762957/87892696-5e921000-ca70-11ea-872e-a7cfa5f48022.png)

3. Enter the following statements in the input box of the console to create the `player` and `team` tags, `follow` and `serve` edge types, and click the **Run** icon.

```ngql
CREATE TAG player (name string, age int);
CREATE TAG team (name string);
CREATE EDGE follow (degree int);
CREATE EDGE serve (start_year int, end_year int);
```

**Note**: The graph schema is completed now.

![schema_created](https://user-images.githubusercontent.com/40747875/72595375-ab235400-3944-11ea-9d30-a48f20fee205.png)

## Importing Data

After the graph schema is created, you can import the required data. In this example we have prepared two vertex files, `player.csv` and `team.csv`, and two edge files, `follow.csv` and `serve.csv`. You can find the four files in the [example](https://github.com/vesoft-inc/nebula-web-docker/tree/master/example) folder.

**Note**: Only support for importing data from CSV files without header.

1. Click the **import** tab and enter **Init**. Select the required graph space in the **Spaces** drop-down list. We select `NBA` here. Click **Next**.

![select_graph](https://user-images.githubusercontent.com/42762957/85967488-28271f00-b9f5-11ea-889f-334eff7a164b.png)

2. In the **Select Files** tab, click the **Select Files** button. We select four files: `player.csv`, `team.csv`, `follow.csv` and `serve.csv`. Click **Next**.

![select_files](https://user-images.githubusercontent.com/40747875/72596622-3998d500-3947-11ea-9347-016ef8fc7768.png)

**Note**: You can also click **Preview** under the **Operation** column to view some data of the file, or click **Delete** to delete the selected file.

![match_type](https://user-images.githubusercontent.com/42762957/85967696-a1bf0d00-b9f5-11ea-9ef1-9e6e09fe66df.png)

3. In the **Map Vertices** tab, click **Bind Datasource**. In the pop-up window, select the file name from the **Name** drop-down list. Select `player.csv` here, and click **Confirm**.

![add_vertex](https://user-images.githubusercontent.com/40747875/72597466-d314b680-3948-11ea-92fd-6e40ee1097c4.png)

4. Click the **+Tag** button at the bottom of the page and select the column name corresponding to vertexId under **VertexId**. Here, we select `column 0` and keep **ID Hash** as the default option: `Primitive`.

![add_tag](https://user-images.githubusercontent.com/42762957/85968736-712ca280-b9f8-11ea-87c3-055555038e90.png)

5. Select `player` in the **TAG** drop-down list. Then select the columns corresponding to the `player` attributes in the corresponding columns. Here, `vertexId` corresponds to `column 0`, `name` corresponds to `column 1` and `age` corresponds to `column 2`.

![vertex-schema-match](https://user-images.githubusercontent.com/42762957/85969254-b1d8eb80-b9f9-11ea-847f-a4e328fe990c.png)

**Note**: Repeat step 3, 4 and 5 to add the `VertexId` mapping and attributes mapping of `team.csv`, and click **Next** after the configuration is complete.

6. In the **Map Edges** tab, click **Bind Datasource**. In the pop-up window, select the file name from the **Name** drop-down list. Select `follow.csv` here, and click **Confirm**.

![select_edge](https://user-images.githubusercontent.com/40747875/72598592-0bb58f80-394b-11ea-9298-a36ef1786a9b.png)

7. Select the edge type corresponding to the file in the **Type** drop-down list. We select `follow` here.

8. Select the column name corresponding to the attribute of the edge in the corresponding column. Here `srcId` corresponds to `column 0` and `dstId` corresponds to `column 1`, `rank` attribute is ignored by default, and `degree` attribute corresponds to `column 2`.

![edge-schema-match](https://user-images.githubusercontent.com/42762957/85969902-9078ff00-b9fb-11ea-8cce-119a03238188.png)

**Note**: Repeat step 6, 7 and 8 to add the attributes mapping for the `serve` edge type. Click **Next** after the configuration is complete.

9. Click **Run Import** to start importing data. You can see the log information after the import is successful.

![log](https://user-images.githubusercontent.com/42762957/85970290-a1764000-b9fc-11ea-835b-62e6573306e2.png)

## Graph Exploration

After the data importing is complete, you can start exploring the graph data in **Nebula Graph**.

1. Click the **explore** tab to enter graph exploration.

2. Select `NBA` from the **Spaces** drop-down list.

3. Click **Add Vertices**.

![graph_explore](https://user-images.githubusercontent.com/42762957/85970736-ef3f7800-b9fd-11ea-87b0-eec82fd19fae.png)

**Note**: You can select a starting vertex or multiple starting vertices to find the vertices associated with it (them). In this example, we select a starting vertex with a VertexID of 100. If you select multiple starting vertices, enter them as follows:

```ngql
100
200
300
```

If the selected vertex does not exist, **Studio** will prompt that the vertex does not exist and it cannot be added.

4. Enter the VertexId value of the starting vertex in the pop-up window. We enter 100 here. Click **Add**.

![starting-vertex](https://user-images.githubusercontent.com/42762957/85970996-9d4b2200-b9fe-11ea-88d2-fb1c139139ad.png)

5. Click vertex 100 and then click **Expand**.

![vertex-expand](https://user-images.githubusercontent.com/42762957/85971159-f87d1480-b9fe-11ea-902a-a8f516fa3916.png)

6. Select `follow` from the **Edge Type** drop-down list and click **Expand** to display the following related vertices.

![show-relation](https://user-images.githubusercontent.com/42762957/85971496-dafc7a80-b9ff-11ea-8a62-0c18c84bdde3.png)

**Note**: When you move your cursor over vertex 102, all the attributes of it are displayed.

7. Click **Show Tags**, select the name property of the tag player. Now the selected property is displayed.

![show](https://user-images.githubusercontent.com/42762957/85976870-06866180-ba0e-11ea-8edd-28a034d4d248.png)

Show Edges is similar to Show Tags.

8. Batch selecting.

Hold down the left mouse button and drag to select multiple vertices in batch.

![image](https://user-images.githubusercontent.com/42762957/86690932-f4727780-c03a-11ea-9012-fbaa7ba27941.png)
