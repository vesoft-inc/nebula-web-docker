# Prepare CSV files

With Studio, you can bulk import vertex and edge data into a Nebula Graph database. Currently, only CSV files without headers are supported. Each file represents vertex or edge data of one type.

To create applicable CSV files, process the source data as follows:

1. Generate CSV files for vertex and edge data:

   - `user.csv`: Contains the vertices representing users with the `userId` property.
   - `course.csv`: Contains the vertices representing courses with the `courseId` and `courseName` properties.
   - `actions.csv` contains:
     - The edges representing actions with the `actionId`, `label`, `duration`, `feature0`, `feature1`, `feature2`, and `feature3` properties. For the `label` column, 1 is replaced with `TRUE` and 0 is replaced with `FALSE`.
     - The `userId` column representing the source vertices of the edges.
     - The `courseName` column representing the destination vertices of the edges.

    This figure shows an example of a CSV file with the header.

    ![The actions.csv file contains the actionId, userId, courseName, duration, feature0, feature1, feature2, feature3, and label columns](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-035.png "actions.csv file with a header")

2. Delete all the headers from the CSV files.
