---
title: "Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_plan_and_manage_permissions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Permissions


For the general permissions that must be granted to the user account to install and work with Veeam Backup & Replication, see [Permissions](required_permissions.md) for Veeam Backup & Replication. In addition to the general requirements, make sure that the accounts used to protect IRIS instances have the following permissions:

* Permissions for IRIS ODB Servers

The account specified for the ODB server in the protection group settings must have root privileges and be able to authenticate against the Veeam Backup & Replication server. Veeam Backup & Replication uses this account to install the Veeam Transport service and the IRIS components over SSH or with the Deployment Kit. For enhanced security, we recommend that you use a separate account dedicated to backup and restore operations. For details, see Creating Protection Group.

To process installed IRIS instances, you must specify the user name of the IRIS instance owner in the Instance Processing step in the Backup Policy wizard. Veeam Backup & Replication connects to the instance through the Veeam Transport service and switches to this user to perform application-aware processing. You do not need to specify a password for this account. For details, see [Specify Processing Settings](iris_policy_processing.md).

* Permissions for Storage Systems

The storage system that hosts the IRIS data volumes must be registered in Veeam Backup & Replication with the Block storage for application protection role. Use storage credentials that allow creating and removing storage snapshots and thin clones, and exporting and mounting volumes to backup proxies and target servers. For details, see [Universal Storage API Integrated Systems Permissions](usais_permissions.md).

Page updated 2026-07-28

