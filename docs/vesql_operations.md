---
title: "SQL Server Database Operations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_operations.html"
last_updated: "11/9/2023"
product_version: "13.0.1.1071"
---

# SQL Server Database Operations

In this article

The following table lists SQL Server database operations and their display names that appear in the fine-tune dialog.

| Entity | Operation | Display Format | Constraints |
| --- | --- | --- | --- |
| Table | CREATE | <date\_time> Created[/Modified] <table\_name> Table <table ID> <initiator> | — |
| DROP | <date\_time> Deleted <table\_name> Table <table ID> <initiator> | — |
| ALTER | <date\_time> Column added <table\_name> Table <table ID> <initiator> | — |
| INSERT INTO | <date\_time> Inserted row <table\_name>[/table\_ID] Table <initiator> | Table name will not be displayed for deleted table, only table ID will be shown. |
| DELETE FROM | <date\_time> Deleted row <table\_name>[/table\_ID] Table <initiator> | Table name will not be displayed for deleted table, only table ID will be shown. |
| UPDATE | <date\_time> Modified <table\_name>>[/table\_ID] Table <initiator> | Table name will not be displayed for deleted table, only table ID will be shown. |
| TRUNCATE | <date\_time> Truncated Table <initiator> | Table name and ID will not be displayed for deleted table. |
| BULK INSERT | <date\_time> Inserted row <table\_name>[/table\_ID] Table <initiator> | — |
| View | CREATE | <date\_time> Created <view\_name> View <initiator> | — |
| DROP | <date\_time> Deleted <view\_name> Table <initiator> | — |
| ALTER | <date\_time> Modified <view\_name> View <initiator> | — |
| Index | CREATE | <date\_time> Created <index\_name> Index <initiator> | — |
| DROP | <date\_time> Deleted <index\_name> Index <initiator> | — |
| ALTER | <date\_time> Modified <index\_name> Index <initiator> | — |
| Procedure | CREATE | <date\_time> Created <procedure\_name> Procedure <initiator> | — |
| DROP | <date\_time> Deleted <procedure\_name> Table <initiator> | — |
| ALTER | <date\_time> Modified <procedure\_name> Procedure <initiator> | — |
| Function | CREATE | <date\_time> Created <function\_name> Function <initiator> | — |
| DROP | <date\_time> Deleted <function\_name> Table <initiator> | — |
| ALTER | <date\_time> Modified <function\_name> Function <initiator> | — |
| Schema | CREATE | <date\_time> Created <schema\_name> Schema <initiator> | — |
| DROP | <date\_time> Deleted <schema\_name> Schema <initiator> | — |
| ALTER | <date\_time> Modified <schema\_name> Schema <initiator> | Schema cannot be detected. |
| User | CREATE | <date\_time> Created <user\_name> User <initiator> | — |
| DROP | <date\_time> Deleted <user\_name> User <initiator> | — |
| ALTER | <date\_time> Modified <user\_name> User <initiator> | — |
| Trigger | CREATE | <date\_time> Created <trigger\_name> Trigger <initiator> | — |
| DROP | <date\_time> Deleted <trigger\_name> Trigger <initiator> | — |
| ALTER | <date\_time> Modified <trigger\_name> Trigger <initiator> | — |

Page updated 11/9/2023

Page content applies to build 13.0.1.1071
