## Summarize 
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/summarizeoperator

## Distinct
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/distinctoperator

## Count
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/countoperator

~~~
<table>
| where <condition>
| summarize count(<field>) by <field>
~~~

## make_set
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/makeset-aggfunction

The `make_set` command in KQL is an aggregation function used to create a dynamic array of distinct values from a specified expression within a group. It can be a valuable tool for analyzing unique values across different categories in your data.

Example of compressing all accounts
~~~
DeviceProcessEvents
| summarize AccountSet=make_set(AccountName) by DeviceName
~~~

## arg_max & arg_min
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/arg-max-aggfunction
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/arg-min-aggfunction

