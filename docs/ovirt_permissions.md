---
title: "Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_permissions.html"
last_updated: "1/21/2026"
product_version: "13.0.1.1071"
---

# Permissions


The accounts used to deploy and administer backup infrastructure components must have the following permissions.

Backup Server Windows Account Permissions

The Windows account used to install Veeam Backup & Replication on the backup server must have the following permissions.

| Account | Required Permission |
| --- | --- |
| Setup Account | The account used to install Veeam Backup & Replication must have the Local Administrator permissions on the backup server. |
| Veeam Backup & Replication User Account | The account used to run Veeam Backup & Replication services must be a LocalSystem account or must have the Local Administrator permissions on the backup server. |

oVirt KVM Manager Permissions

The administrator account that the backup server uses to access the oVirt KVM Manager must have the SuperUser privileges. For more information on system permissions, see [Red Hat Virtualization documentation](https://access.redhat.com/documentation/en-us/red_hat_virtualization/4.4/html/administration_guide/part-administering_and_maintaining_the_red_hat_virtualization_environment#sect-System_Permissions) or [Oracle Linux Virtualization Manager documentation](https://docs.oracle.com/en/virtualization/oracle-linux-virtualization-manager/admin/admin-admin-global-config.html).


