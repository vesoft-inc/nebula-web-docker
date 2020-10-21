# Operate graph spaces

When Studio is connected to Nebula Graph, you can create or delete a graph space. You can use **Console** or **Schema** to do these operations. This article only introduces how to use **Schema** to operate graph spaces in a Nebula Graph database.

## Prerequisites

To operate a graph space on Studio, you must do a check of these:

- Studio is connected to a Nebula Graph database.
- Your account has the authority of GOD. It means that:
  - If the authentication is enabled in Nebula Graph, you can use `user` and `password` to sign in to Studio.
  - If the authentication is disabled in Nebula Graph, you must use `root` and its password to sign in to Studio.

## Create a graph space

To create a graph space on **Schema**, follow these steps:

1. In the toolbar, click the **Schema** tab.
2. On the **Graph Space List** page, click the **+ Create** button.
3. On the **Create** page, do these settings:

   a. **Name**: Specify a name to the new graph space. In this example, `mooc_actions` is used. The name must be distinct in the database.

   b. **Optional Parameters**: Set `partition_num`, `replica_factor`, `charset`, or `collate`. In this example, these parameters are set to `10`, `1`, `utf8`, and `utf8_bin` separately. For more information, see [`CREATE SPACE` syntax](https://docs.nebula-graph.io/manual-EN/2.query-language/4.statement-syntax/1.data-definition-statements/create-space-syntax/ "Click to go to the Nebula Graph website").

   In the **Equivalent to the following nGQL statement** panel, you can see the statement equivalent to the preceding settings.

4. Confirm the settings and then click the **+ Create** button. If the graph space is created successfully, you can see it on the graph space list.

![The Create page with settings for a graph space](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-026.png "Create a graph space")

## Delete a graph space

To delete a graph space on **Schema**, follow these steps:

1. In the toolbar, click the **Schema** tab.
2. In the graph space list, find a graph space and then the ![Icon of deletion](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-017.png "Delete") icon in the **Operations** column.

   ![Graph space list with the graph space to be deleted](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-029.png "Delete a graph space")
3. On the dialog box, confirm the information and then click the **OK** button.  
   When the graph space is deleted successfully, it is removed from the graph space list.

## Next to do

After a graph space is created, you can create or edit a schema, including:

- [Operate tags](st-ug-crud-tag.md)
- [Operate edge types](st-ug-crud-edge-type.md)
- [Operate indexes](st-ug-crud-index.md)
