---
title: "searching_vm_backups"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/searching_vm_backups.html"
last_updated: "1/12/2024"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup Enterprise Manager allows you to search for guest OS files in all machine backups with guest indexing enabled. After you find necessary files, you can select them to perform file restore.

|  |
| --- |
| Important |
| By default, backup repository is the primary destination for the search. This means, in particular, that if a backup (with an indexed guest) is stored both in a repository and tape, the Enterprise Manager search results will only include the files from backup stored in the repository. Files from tape-archived backup will appear in search results only if nothing is found in the repository (the capability is supported in the Enterprise and Enterprise Plus editions). |

You can use one of the following search modes:

* [Simple search](performing_simple_search.md) — allows you to search for files in a selected restore point of a selected machine backup
* [Advanced search](performing_advanced_search.md) — allows you to search for files in all restore points of a selected machine backup and filter search results by certain criteria

Page updated 1/12/2024

Page content applies to build 13.0.1.1071
