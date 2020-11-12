# Operate Indexes

You can create an index for a tag and/or an edge type. An index lets traversal start from vertices or edges with the same property and it can make a query more efficient. You can create two index types: Tag Index and Edge Type Index. With Studio, you can use the **Console** tab page or the **Schema** tab page to create, retrieve, and delete indexes. This article only introduces how to use the **Schema** tab page to operate an index.

> **NOTE**: You can create an index when a tag or an edge type is created. But an index can decrease the write speed during data import. We recommend that you import data firstly and then create and rebuild an index. For more information, see [nGQL Manual](https://docs.nebula-graph.io/manual-EN/2.query-language/4.statement-syntax/1.data-definition-statements/ "Click to go to the Nebula Graph website").

## Studio version

Studio of v1.2.0-beta or later versions supports this function. To update the version, run this command.

```bash
docker-compose pull && docker-compose up
```

## Prerequisites

To operate an index on Studio, you must do a check of these:

- The version of Studio is v1.2.0-beta or later.
- Studio is connected to Nebula Graph.
- A graph space, tags, and edge types are created.
- Your account has the authority of GOD, ADMIN, or DBA.

## Create an index

To create an index on the **Schema** tab page, follow these steps:

1. In the toolbar, click the **Schema** tab.
2. On the **Graph Space List** page, find a graph space, and then click its name or the ![Icon of setting](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-018.png "Set") icon in the **Operations** column.
3. In the **Current Graph Space** field, confirm the name of the graph space. If necessary, you can choose another name to change the graph space.
4. Click the **Index** tab and then click the **+ Create** button.
5. On the **Create** page, do these settings:

   a. **Index Type**: Choose to create an index for a tag or for an edge type. In this example, **Edge Type** is chosen.

   b. **Name**: Choose a tag name or an edge type name. In this example, **action** is chosen.

   c. **Index Name**: Specify a name for the new index. In this example, **action_index** is used.

   d. **Indexed Properties**: Click **Add**, and then, in the dialog box, choose a property. If necessary, repeat this step to choose more properties. You can drag the properties to sort them. In this example, `actionId` and `label` are chosen.
   > **NOTE**: The order of the indexed properties has an effect on the result of the `LOOKUP` statement. For more information, see [nGQL Manual](https://docs.nebula-graph.io/manual-EN/2.query-language/4.statement-syntax/2.data-query-and-manipulation-statements/lookup-syntax/#error_code_411 "Click to go to the Nebula Graph website").

   When the settings are done, the **Equivalent to the following nGQL statement** panel shows the statement equivalent to the settings.  
![A page for index creation](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-030.png "Create an index")

6. Confirm the settings and then click the **+ Create** button.  
   When an index is created, the index list shows the new index.

## View indexes

To view indexes on the **Schema** tab page, follow these steps:

1. In the toolbar, click the **Schema** tab.
2. In the graph space list, find a graph space, and then click its name or the ![Icon of setting](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-018.png "Set") icon in the **Operations** column.
3. In the **Current Graph Space** field, confirm the name of the graph space. If necessary, you can choose another name to change the graph space.
4. Click the **Index** tab, in the upper left corner, choose an index type, **Tag** or **Edge Type**.
5. In the list, find an index and click its row. All its details are shown in the expanded row.

## Delete an index

To delete an index on **Schema**, follow these steps:

1. In the toolbar, click the **Schema** tab.
2. In the graph space list, find a graph space, and then click its name or the ![Icon of setting](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-018.png "Set") icon in the **Operations** column.
3. In the **Current Graph Space** field, confirm the name of the graph space. If necessary, you can choose another name to change the graph space.
4. Click the **Index** tab, find an index and then the ![Icon of deletion](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-017.png "Delete") icon in the **Operations** column.
