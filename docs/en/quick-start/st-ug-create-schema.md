# Create a schema

To bulk import data into a Nebula Graph database, you must have a schema. You can create a schema with the **Console** module or the **Schema** module of Studio.

> **NOTE**: You can use nebula-console to create a schema. For more information, see [Deploy Nebula Graph with Docker Compose
](https://github.com/vesoft-inc/nebula-docker-compose/blob/master/README.md "Click to go to GitHub website") and [Get started with Nebula Graph](https://docs.nebula-graph.io/manual-EN/1.overview/2.quick-start/1.get-started/ "Click to go to Nebula Graph website").

## Prerequisites

To create a schema on Studio, you must do a check of these:

- Studio is connected to Nebula Graph.
- Your account has the privileges of GOD, ADMIN, or DBA. For more information, see [Nebula Graph roles](https://docs.nebula-graph.io/manual-EN/3.build-develop-and-administration/4.account-management-statements/built-in-roles/ "Click to go to Nebula Graph website").
- The schema is designed.
- A graph space is created.
  > **NOTE**: If no graph space exists, and your account has GOD privileges, you can create a graph space with **Console** or **Schema**.

## Create a schema with Schema

To create a schema on the **Schema** page, make sure that the version of Studio is v1.2.0-beta or later then follow these steps:

1. Create tags. For more information, see [Operate tags](../manage-schema/st-ug-crud-tag.md).
2. Create edge types. For more information, see [Operate edge types](../manage-schema/st-ug-crud-edge-type.md).

## Create a schema with Console

To create a schema on the **Console** page, follow these steps:

1. In the toolbar, click the **Console** tab.
2. In the **Current Graph Space** field, choose a graph space name. In this example, **mooc_actions** is used.

   ![Choose a graph space name for the Current Graph Space field](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-031.png "Choose a graph space")

3. In the input box, enter these statements one by one and click the ![Icon of Run](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-008.png "Run") icon.

   ```nGQL
    nebula> CREATE TAG user (userId int); -- To create a tag named "user", with one property
    nebula> CREATE TAG course (courseId int, courseName string); -- To create a tag named "course", with two properties
    nebula> CREATE EDGE action (actionId int, duration double, label bool, feature0 double, feature1 double, feature2 double, feature3 double); -- To create an edge type named "action", with seven properties
    ```

If the preceding statements are executed successfully, the schema is created. You can run the statements as follows to view the schema.

```nGQL
nebula> SHOW TAGS; -- To list all the tags in the current graph space
nebula> SHOW EDGES; -- To list all the edge types in the current graph space
nebula> DESCRIBE TAG user;
nebula> DESCRIBE TAG course;
nebula> DESCRIBE EDGE action; -- To view the definition of the tags and edge types
```

If the schema is created successfully, in the result window, you can see the definition of the tags and edge types. For example, this figure shows the result of the `DESCRIBE EDGE action` statement.

![The result window shows the definition of the action edge](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-048.png "Result of the DESCRIBE EDGE action statement")

## Next to do

When a schema is created, you can [import data](st-ug-import-data.md).
