---
title: "Specifying Preferred Networks for Veeam Plug-Ins in Managed Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/preferred_network.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Specifying Preferred Networks for Veeam Plug-Ins in Managed Mode


You can specify networks over which Veeam Plug-Ins in managed mode must transport data when you perform data protection and disaster recovery tasks on remote backup repositories. This setting applies only to Veeam Plug-Ins network traffic, without affecting the data traffic of other Veeam Backup & Replication components. Setting a dedicated network for Veeam Plug-Ins backup and replication operations can help to reduce heavy network loads.

|  |
| --- |
| Note |
| Consider the following:   * By default, if there are no specified preferred networks for Veeam Plug-In data traffic, Veeam Plug-In will connect to preferred networks specified in Veeam Backup & Replication. For details on setting preferred networks in Veeam Backup & Replication, see [Specifying Preferred Networks](select_backup_network.md). * Veeam Plug-In does not save information about failed network connections. If backup or restore operations fail, Veeam Plug-In tries to connect to the following network from the preferred networks list to finish the started operations. Regardless of the first unsuccessful connection, Veeam Plug-In will try to perform the next backup operations first on the failed network. * Veeam Plug-In network preferences take priority over Veeam Backup & Replication network preferences. Only if the preferred networks for Veeam Plug-In data traffic are not available for any reason, Veeam Plug-In will try to connect to the Veeam Backup & Replication preferred networks. |

To specify networks for data transfer, you must create a list of preferred networks. When Veeam Plug-In needs to transfer data, it uses networks from this list. If a connection over any of the preferred networks cannot be established for any reason, Veeam Plug-In will automatically fail over to the following network from the preferred networks list.

For more information on creating and managing the list of preferred networks that specific Veeam Plug-Ins will use, see the following sections:

* [Specifying Preferred Networks for Veeam Plug-In for SAP HANA](preferred_network_hana.md)
* [Specifying Preferred Networks for Veeam Plug-In for Oracle RMAN](preferred_network_rman.md)
* [Specifying Preferred Networks for Veeam Plug-In for SAP on Oracle](preferred_network_sap_orcl.md)
* [Specifying Preferred Networks for Veeam Plug-In for Microsoft SQL Server](preferred_network_mssql.md)


