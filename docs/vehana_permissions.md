---
title: "Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vehana_permissions.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Permissions


The following table lists the user account permissions necessary to launch Veeam Explorer for SAP HANA and restore SAP HANA data.

| Operation | Required Roles and Permissions |
| --- | --- |
| Veeam Explorer for SAP HANA launch | The account used to run Veeam Explorer for SAP HANA must meet the following requirements:   * The account must be a member of the local Administrators or Users group on the machine where Veeam Explorer for SAP HANA is running.  * The account must have one of the following roles on the backup server:  * The Veeam Backup Administrator or Veeam Restore Operator default roles. * A custom role with at least the Manage restores permission and the Veeam Explorer for SAP HANA restore option, with access to the target server and the backup. For more information, see [Configuring Roles](configure_roles.md#custom_roles). |
| Restore | When restoring your data with Veeam Explorer for SAP HANA, make sure to configure user accounts as follows:   * The account used for SAP HANA data recovery must be a Linux user with operating system user (<sid>adm) privileges on the target machine. Operating system user privileges are required to execute restore operations and to handle database processes. For more information about operating system user privileges, see the [SAP HANA documentation](https://help.sap.com/docs/SAP_HANA_PLATFORM/6b94445c94ae495c83a19646e7c3fd56/be98c998bb5710149e8cace9b0c08908.html). * The database user on the target SAP HANA system must have the SYSTEM, RECOVERY OPERATOR or DATABASE ADMIN privilege. |


