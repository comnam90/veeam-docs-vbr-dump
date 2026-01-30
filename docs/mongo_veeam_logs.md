---
title: "Logs and Support"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_veeam_logs.html"
last_updated: "9/1/2025"
product_version: "13.0.1.1071"
---

# Logs and Support


If you have any questions or issues with Veeam Backup & Replication, you can search for a resolution on [Veeam R&D Forums](https://forums.veeam.com/) or submit a support case on the [Veeam Customer Support Portal](https://www.veeam.com/support.html).

When you submit a support case, attach a file containing logs related to Veeam Backup & Replication and Veeam Agent for Linux operations.

Veeam Agent for Linux Logs

To export Veeam Agent for Linux logs, run the following command on the protected computer with MongoDB:

|  |
| --- |
| veeamconfig grablogs |

Veeam Agent will collect logs, export them to an archive file with the name veeam\_logs\_<date>\_<time>.tar.gz, and save the archive to the current working directory.

For example:

|  |
| --- |
| user@srv01:~$ veeamconfig grablogs |

Veeam Backup & Replication Logs

For details on how to collect Veeam Backup & Replication logs, see [Exporting Logs](exporting_logs.md).


