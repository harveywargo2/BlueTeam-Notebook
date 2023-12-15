
# General Concepts 
## Tabular Operators 
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/tabularexpressionstatements
The most common kind of query statement is a tabular expression **statement**, which means both its input and output consist of tables or tabular datasets. Tabular statements contain zero or more **operators**, each of which starts with a tabular input and returns a tabular output. 

## Pipe Flow
KQL queries are written as a sequence of operations connected by pipes (`|`). This allows you to build complex analyses by chaining together various operators, each manipulating the data in a specific way. This flow of data through the pipeline is known as **KQL Pipe Flow**.

#### General Overview of KQL Pipe Flow
- **Start with a data source:** This could be a table, a view, or the result of another query.
- **Apply operators one after another:** Each operator receives the output of the previous operator as its input.
- **Each operator performs its specific task:** This could be filtering rows, projecting columns, aggregating data, joining tables, or generating new data.
- **The result of each operator is fed into the next one:** This allows you to build complex workflows by chaining together multiple operations.
- **The final output of the pipeline is a new table:** This table contains the transformed data according to your query.
- **Create Data & Filter:**

#### Key Tips for KQL Pipe Flow
- **Order matters: ** The order of operators in the pipe is crucial as each operator operates on the output of the previous one.
- **Each operator is self-contained: ** Each operator takes a table as input and produces a new table as output. This allows for modular and reusable queries.
- **Data flows through the pipe sequentially: ** Each operator processes the entire input before passing the result to the next operator.
- **Pipeline can be complex or simple: ** You can build simple queries with just a few operators or create intricate workflows with multiple stages and branching logic.
- **Efficiency: ** It is easy to identify performance efficiency by measuring the time and or output from each Pipe Flow Output
- **Order Matters for Efficiency: **  Filter the table down as much as possible before using more intense operators
- **Data Size/Footprint/Indexing effects performance: ** Queries on larger data sets or non indexed fields will be less performant than smaller and indexed
- **Some Operators Don't Follow Pipe Flow: **


## Take & Limit 
There is actually no difference between `TAKE` and  `LIMIT` in KQL. They are synonyms and behave identically. Both operators are used to **limit the number of rows returned by a query**.

The reason for having two options is to make KQL easier to learn for users familiar with other query languages. Some languages use **LIMIT**, while others use **TAKE**. Having both options available provides flexibility and reduces the learning curve.

#### Key Points 
- **Both operators are interchangeable:** You can use **TAKE** or **LIMIT** in your KQL queries with the same result.
- **Both operators are case-insensitive:** You can write **TAKE** or **take**, **LIMIT** or **limit**, and they will have the same effect.
- **The order matters:** The **TAKE** or **LIMIT** operator should be placed at the end of your KQL query pipe, after any filtering or aggregation operations.
- **Both operators are efficient:** Kusto optimizes query execution based on the presence of **TAKE** or **LIMIT**, ensuring it only processes the required number of rows.

## Data Types 
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/scalar-data-types/

[gettype()](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/gettypefunction)Used to get the data type for a field

Example in Sentinel Audit Logs
~~~
AuditLogs
| extend GTDetails = gettype(AdditionalDetails)
| extend GTDCategory = gettype(Category)
| extend GTDTimeStamp = gettype(TimeGenerated)
| limit 100
~~~


## Rendering Output w/ Project 
The `project` operator in KQL is a powerful tool for manipulating the columns in your data. It allows you to:
- `project`: Select the columns to include, rename or drop, and insert new computed columns.
- `project-away`: select excluded columns
- `project-rename`: renames columns of output table
- `# project-reorder`: reorder columns of output table


## Where 

The `where` operator is a fundamental tool in KQL for filtering data based on a specified condition. It allows you to extract a subset of rows that meet your criteria, enabling focused analysis on the relevant information. Here's an explanation of the `where` operator and its functionalities:

**Functionality:**
- **Filters rows:** Based on a specified logical expression, the `where` operator removes rows that don't satisfy the condition.
- **Supports various comparisons:** You can use comparison operators like `==`, `!=`, `<`, `>`, `<=`, and `>=` to compare column values with specific values or other expressions.
- **Supports logical operators:** Combining comparison operators with `and`, `or`, and `not` allows you to create complex filtering conditions.
- **PIPE Flow Filters** You can use multiple `where` operators in a sequence to apply multiple filters to the data.

**Important points:**
- The `where` operator should be placed before any aggregation or projection operators in your query pipe.
- You can use parentheses to group complex logical expressions.
- KQL provides various functions and operators that can be used within the `where` condition for advanced filtering functionalities.

Generic Example
~~~
<Table_Name> 
| where <condition> 
| where <condition> 
| where <condition> 
| Render <Output_Table>
~~~

## Logical Binary Operators
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/logicaloperators

## Numerical Operators
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/numoperators

## String & In Operators 
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/datatypes-string-operators
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/in-cs-operator

**Pay Attention to Case-Sensitivity for Different Operators**

## Let (Variable)
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/letstatement

## Datatable (create a table)
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/datatableoperator