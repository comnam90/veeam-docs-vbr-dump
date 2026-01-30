---
title: "Restoring Databases (HDBSQL Commands)"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/saphana_restore_scripts.html"
last_updated: "11/8/2024"
product_version: "13.0.1.1071"
---

# Restoring Databases (HDBSQL Commands)


You can use HDBSQL to restore SAP HANA databases from backups stored on Veeam backup repositories. For details on the HDBSQL restore, see [this SAP article](https://help.sap.com/docs/SAP_HANA_PLATFORM/4fe29514fd584807ac9f2a04f6754767/c4205f73bb571014ba46d209981bc1f5.html?locale=en-US&version=2.0.06).

To recover SAP HANA databases from backups stored on Veeam backup repositories, do the following:

1. Log in to SAP HANA HDBSQL as the HDB administrator. Use HDBUSERSTORE to securely store connection details on a client machine. For details, see [this SAP article](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/dd95ac9dbb571014a7d7f0234d762fdb.html?locale=en-US&version=2.0.05).

|  |
| --- |
| sh4adm@linux-q0pn:/usr/sap/SH4/HDB01> hdbuserstore SET <key> hostname:30013@SID <username> <password>  sh4adm@linux-q0pn:/usr/sap/SH4/HDB01> hdbsql -U <key> |

1. Recover a tenant database to the latest state using Backint. As the timestamp, specify the current data and time or future date and time.

|  |
| --- |
| alter stop database <DATABASE\_NAME>; |


