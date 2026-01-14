---
title: "Authentication Against Replica Set"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_auth_methods.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Authentication Against Replica Set

In this article

When you configure MongoDB Backup, you can choose one of several methods to authenticate against MongoDB replica sets that you plan to back up. Veeam Backup & Replication will use this method to connect to the MongoDB replica set and collect information about replica set configuration. For more information, see [Rescan Job](mongo_rescan_job.md).

|  |
| --- |
| Important |
| Before you you configure MongoDB Backup, consider access permissions listed in [Permissions](mongo_plan_and_manage_permissions.md). |

You can select one of the following methods to connect to MongoDB replica sets:

* User name and password. When you select authentication with User name and password, Veeam Backup & Replication uses Salted Challenge Response Authentication Mechanism (SCRAM) authentication method. This is the default authentication mechanism for MongoDB.
* User name and password with TLS. When you select authentication with user name, password and the TLS protocol, Veeam Backup & Replication uses SCRAM authentication method and may use client certificates for credentials encryption. SCRAM with TLS offers a more secure connection to the replica set than just SCRAM.
* X.509 certificate with TLS. When you select authentication with the X.509 certificate and the TLS protocol, Veeam Backup & Replication uses client certificates for encryption and authentication. To use this authentication method, you must specify client certificates. This method offers a more secure connection to the replica set than SCRAM with TLS.

Veeam Backup & Replication stores all specified credentials encrypted in the configuration database.

Related Task

[Specify Deployments](mongo_protection_group_scope_deployments.md)

Page updated 9/2/2025

Page content applies to build 13.0.1.1071
