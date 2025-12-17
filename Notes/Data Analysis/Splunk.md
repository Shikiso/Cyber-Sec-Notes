# Search Field Operators
| Field Name                         | Operator | Example                   | Explanation                                                                                                                                                        |
| ---------------------------------- | -------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Equal  <br>**                    | =        | UserName=Mark             | This operator is used to match values against the field. In this example, it will look for all the events, where the value of the field UserName is equal to Mark. |
| **Not Equal to  <br>**             | !=       | UserName!=Mark            | This operator returns all the events where the UserName value does not match Mark.                                                                                 |
| **Less than  <br>**                | <        | Age < 10                  | Showing all the events with the value of Age less than 10.                                                                                                         |
| **Less than or Equal to  <br>**    | <=       | Age <= 10                 | Showing all the events with the value of Age less than or equal to 10.                                                                                             |
| **Greater than  <br>**             | >        | Outbound_traffic > 50 MB  | This will return all the events where the Outbound traffic value is over 50 MB.                                                                                    |
| **Greater Than or Equal to  <br>** | >=       | Outbound_traffic >= 50 MB | This will return all the events where the Outbound traffic value is greater or equal to 50 MB.                                                                     |
# Boolean Operators
| **Operator  <br>** | **Syntax  <br>**                      | **Explanation  <br>**                                                               |
| ------------------ | ------------------------------------- | ----------------------------------------------------------------------------------- |
| **NOT  <br>**      | field_A **NOT** value                 | Ignore the events from the result where field_A contain the specified value.        |
| **OR  <br>**       | field_A=value1 **OR** field_A=value2  | Return all the events in which field_A contains either value1 or value2.            |
| **AND  <br>**      | field_A=value1 **AND** field_B=value2 | Return all the events in which field_A contains value1 and field_B contains value2. |
# Filtering Results

## Fields
When searching through a large amount of data you can add or remove specific data using filters. The fields command allows you do such a thing.

| **Command**           | **fields**                                                                                                                                                                                                              |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Explanation  <br>** | Fields command is used to add or remove mentioned fields from the search results. To remove the field, minus sign ( - ) is used before the fieldname and plus ( + ) is used before the fields which we want to display. |
| **Syntax  <br>**      | \| fields <field_name1>  <field_name2>                                                                                                                                                                                  |
| **Example**           | \| `fields + HostName - EventID`                                                                                                                                                                                        |
**Example Search Query:** `index=windowslogs | fields + host + User + SourceIp`
- - -
## Search
| **Command**           | **search**                                                                            |
| --------------------- | ------------------------------------------------------------------------------------- |
| **Explanation  <br>** | This command is used to search for the raw text while using the chaining command `\|` |
| **Syntax  <br>**      | \| search  <search_keyword>                                                           |
| **Example**           | \| `search "Powershell"`                                                              |
**Example Search Query:** `index=windowslogs | search Powershell`  
- - -
## Dedup
| **Command**           | **dedup**                                                                                                                                                                                                            |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Explanation  <br>** | Dedup is the command used to remove duplicate fields from the search results. We often get the results with various fields getting the same results. These commands remove the duplicates to show the unique values. |
| **Syntax  <br>**      | \| dedup <fieldname>                                                                                                                                                                                                 |
| **Example**           | \| `dedup EventID`                                                                                                                                                                                                   |
**Example Search Query:** `index=windowslogs | table EventID User Image Hostname | dedup EventID`
- - -
## Rename
| **Command**           | **rename**                                                                                                                                                                     |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Explanation  <br>** | It allows us to change the name of the field in the search results. It is useful in a scenario when the field name is generic or log, or it needs to be updated in the output. |
| **Syntax  <br>**      | \| rename  <fieldname>                                                                                                                                                         |
| **Example**           | \| `rename User as Employees`                                                                                                                                                  |
**Example Search Query**: `index=windowslogs | fields + host + User + SourceIp | rename User as Employees`
- - -

# Structuring
## Table  

| **Explanation  <br>** | Each event has multiple fields, and not every field is important to display. The Table command allows us to create a table with selective fields as columns. |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Syntax  <br>**      | \| table <field_name1> <fieldname_2>                                                                                                                         |
| **Example**           | \| `table`  <br><br>\| `head 20` # will return the top 20 events from the result list.                                                                       |
**Example Search Query:** `index=windowslogs | table EventID Hostname SourceName`
- - -
## Head

| **Explanation  <br>** | The **head** command returns the first 10 events if no number is specified.                                                                  |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **Syntax  <br>**      | \| head <number>                                                                                                                             |
| **Example**           | \| `head`   # will return the top 10 events from the result list<br><br>\| `head 20`    # will return the top 20 events from the result list |
**Example Search Query:** `index=windowslogs |  table _time EventID Hostname SourceName | **head 5**`
- - -
## Tail

| **Explanation  <br>** | The **Tail** command returns the last 10 events if no number is specified.                                                                  |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **Syntax  <br>**      | \| tail <number>                                                                                                                            |
| **Example**           | \| `tail` # will return the last 10 events from the result list<br><br>\| `tail 20`   # will return the last 20 events from the result list |
**Example Search Query:** `index=windowslogs |  table _time EventID Hostname SourceName | tail 5`
- - -
## Sort  

| **Explanation  <br>** | The **Sort** command allows us to order the fields in ascending or descending order. |
| --------------------- | ------------------------------------------------------------------------------------ |
| **Syntax  <br>**      | \| `sort` <field_name>                                                               |
| **Example**           | \| `sort Hostname` # This will sort the result in Ascending order.                   |
**Example Search Query:** `index=windowslogs |  table _time EventID Hostname SourceName | sort Hostname`  
- - -
## Reverse

| **Explanation  <br>** | The reverse command simply reverses the order of the events. |
| --------------------- | ------------------------------------------------------------ |
| **Syntax  <br>**      | \|  reverse                                                  |
| **Example**           | `<Search Query> \| reverse`                                  |

**Example Search Query:** `index=windowslogs | table _time EventID Hostname SourceName | reverse`
- - -
# Transformation
Transformational commands are those commands that change the result into a data structure from the field-value pairs.
## Top  

| **Command**           | **top**                                                     |
| --------------------- | ----------------------------------------------------------- |
| **Explanation  <br>** | This command returns frequent values for the top 10 events. |
| **Syntax  <br>**      | \| top  <field_name><br><br>\| top limit=6 <field_name>     |
| **Example**           | `top limit=3 EventID`                                       |
**Example Search Query:** `index=windowslogs | top limit=7 Image`  
- - -
## Rare

| **Command**           | **rare**                                                                                                    |
| --------------------- | ----------------------------------------------------------------------------------------------------------- |
| **Explanation  <br>** | This command does the opposite of top command as it returns the least frequent values or bottom 10 results. |
| **Syntax  <br>**      | \| rare <field_name><br><br>\| rare limit=6 <field_name>                                                    |
| **Example**           | `rare limit=3 EventID`                                                                                      |
**Example Search Query:** `index=windowslogs | rare limit=7 Image`    

- - -
## Highlight

| **Command**           | **highlight**                                                                       |
| --------------------- | ----------------------------------------------------------------------------------- |
| **Explanation  <br>** | The highlight command shows the results in raw events mode with fields highlighted. |
| **Syntax  <br>**      | highlight      <field_name1>      <field_name2>                                     |
| **Example**           | `highlight User, host, EventID, Image`                                              |
**Example Search Query:** `index=windowslogs | highlight User, host, EventID, Image`
- - -
## STATS Commands

SPL supports various stats commands that help in calculating statistics on the values. Some common stat commands are:

| **Command**       | **Explanation**                                                   | **Syntax**                        | **Example**              |
| ----------------- | ----------------------------------------------------------------- | --------------------------------- | ------------------------ |
| **Average  <br>** | This command is used to calculate the average of the given field. | stats avg(field_name)             | stats avg(product_price) |
| **Max  <br>**     | It will return the maximum value from the specific field.         | stats max(field_name)             | stats max(user_age)      |
| **Min**           | It will return the minimum value from the specific field.         | stats min(field_name)             | stats min(product_price) |
| **Sum**           | It will return the sum of the fields in a specific value.         | stats sum(field_name)             | stats sum(product_cost)  |
| **Count**         | The count command returns the number of data occurrences.         | stats count(function) AS new_NAME | stats count(source_IP)   |

- - -
## Splunk Chart Commands 

These are very important types of transforming commands that are used to present the data in table or visualization form. Most of the chart commands utilize various stat commands.
## Chart

| **Command**           | **chart**                                                                      |
| --------------------- | ------------------------------------------------------------------------------ |
| **Explanation  <br>** | The chart command is used to transform the data into tables or visualizations. |
| **Syntax  <br>**      | \| chart <function>                                                            |
| **Example**           | \| `chart count by User`                                                       |

**Example Search Query:** `index=windowslogs | chart count by User`  
- - -
## Timechart

| **Command**           | **timechart**                                                                                                                                |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **Explanation  <br>** | The timechart command returns the time series chart covering the field following the function mentioned. Often combined with STATS commands. |
| **Syntax  <br>**      | \| timechart function  <field_name>                                                                                                          |
| **Example**           | \| `timechart count by Image`                                                                                                                |
**Example Search Query:** `index=windowslogs | timechart count by Image`