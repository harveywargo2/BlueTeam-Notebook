## Has Operators 

Filters a record set for data with a case-insensitive string. `has` searches for indexed terms, where an indexed [term](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/datatypes-string-operators#what-is-a-term) is three or more characters. If your term is fewer than three characters, the query scans the values in the column, which is slower than looking up the term in the term index.


#### Understanding string terms
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/datatypes-string-operators#what-is-a-term 

Kusto indexes all columns, including columns of type `string`. Multiple indexes are built for such columns, depending on the actual data. These indexes aren't directly exposed, but are used in queries with the `string` operators that have `has` as part of their name, such as `has`, `!has`, `hasprefix`, `!hasprefix`. 

**The semantics of these operators are dictated by the way the column is encoded. Instead of doing a "plain" substring match, these operators match _terms_.**

By default, each `string` value is broken into maximal sequences of alphanumeric characters, and each of those sequences is made into a term.

For example, in the following `string`, the terms are `Kusto`, `KustoExplorerQueryRun`, and the following substrings: `ad67d136`, `c1db`, `4f9f`, `88ef`, `d94f3b6b0b5a`.

#### Gotchas
- Watch how things are broken up into terms.  
- Some items like command lines can be broken into unpredictable terms. 
- t is best to test with `contains` or other string operators that run on the actual stringfirst before using `has` even though `has` is more performant operator

Some examples from AzureActivity logs in Sentinel
AzureActivity for OperationNameValue = Microsoft.Resourcehealth/healthevent/
~~~

AzureActivity
| where OperationNameValue has 'resourcehealth'
//Works

AzureActivity
| where OperationNameValue has 'resource'
// Missed search
~~~

### has_any
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/has-anyoperator
### has_all
- https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/has-all-operator


