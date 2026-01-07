There are two types of databases:
- Relation databases - Store structured data
- Non-Relation databases - Stores data in a non-tabular format

Relational databases will use a table for store data.
This table will consist of rows and columns, e.g below.

| **ID** | **Name** | **Age** |
| ------ | -------- | ------- |
| 0      | Jake     | 46      |
| 1      | Mark     | 22      |
| 2      | Sarah    | 76      |
Tables have keys (in the table above its ID), you have primary and foreign keys.
Primary keys are keys for the table such as ID in the example. Foreign keys come from other tables and can be used to reference a row in one table with another row in a different table.
Example:

| **ID** | **Name** | **Age** | **Class_ID** |
| ------ | -------- | ------- | ------------ |
| 0      | Jake     | 46      | 1            |
| 1      | Mark     | 22      | 0            |
| 2      | Sarah    | 76      | 2            |

| **ID** | **Class** | **Students** |
| ------ | --------- | ------------ |
| 0      | Maths     | 12           |
| 1      | English   | 15           |
| 2      | Science   | 9            |
