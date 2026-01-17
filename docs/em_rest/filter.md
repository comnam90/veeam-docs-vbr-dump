---
title: "filter"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/filter.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

The filter parameter lets you filter query results and limit a set of displayed items.

By default, the query results are not filtered: the REST API lists all resource collections. Using the filter parameter, you can request only those items that match the specified criteria.

The filter component in the query string has the following format:

|  |
| --- |
| filter=<filterCriteria> |

where <filterCriteria> is a logical expression that combines the following elements:

* [Comparison expressions](query_comparison.md)
* [Optional] [Logical Operators: AND, OR](query_and_or.md)
* [Optional] [Grouping operators](query_grouping.md)

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
