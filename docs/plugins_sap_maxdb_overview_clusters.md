---
title: "Support for Clusters"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_overview_clusters.html"
last_updated: "11/6/2025"
product_version: "13.0.1.1071"
---

# Support for Clusters


Veeam Plug-In supports backup and restore of SAP MaxDB databases that operate as parts of a failover cluster.

Veeam Plug-In supports data backup and restore for the following types of clusters:

* High availability disaster recovery (HADR)
* Failover clusters

To back up data with Veeam Plug-In, clustered databases must be managed with the following cluster management software:

* IBM PowerHA (for clusters running IBM AIX only)
* IBM Tivoli System Automation (TSA)
* Pacemaker (for clusters running Linux-based OS only)

Backup of Cluster

To back up databases that operate as part of a failover cluster, do the following:

1. Install and configure Veeam Plug-In for SAP MaxDB on each node of the cluster. For more information, see [Installing Veeam Plug-In for SAP MaxDB](plugins_sap_maxdb_deploy_install.md) and [Configuring Environment](plugins_sap_maxdb_deploy_configure.md).
2. Perform the backup on the active cluster node. For more information, see [SAP MaxDB Backup](plugins_sap_maxdb_backup_backint.md).

Veeam Plug-In will start the backup job on the primary cluster node.

In case of clustered database, Veeam Plug-In can store data from several cluster nodes in the same backup file on the backup repository. To do this, Veeam Plug-In needs the name of the cluster. Depending on the cluster management software that you use, Veeam Plug-In gets the cluster name in one of the following names:

* In case of IBM PowerH and IBM TSA, Veeam Plug-In gets the cluster name automatically.
* In case of Pacemaker, you must set the cluster name in the [veeam\_config.xml](db2_configure_file.md) file. You must set the name with the customServerName parameter. The parameter value must be the same as the name of your cluster.

|  |
| --- |
| <PluginParameters customServerName="hostname.domain.tld" /> |

For example, if your cluster has the name maxdb1 and the domain for the environment is customer1.local, you have to set the following entry:

|  |
| --- |
| <PluginParameters customServerName="maxdb001.customer1.local" /> |

Keep in mind that you must add the parameter to the existing line in the veeam\_config.xml file. If you create a new line with the same name as the existing line, Veeam Plug-In will consider parameters only in the first detected line. Other parameters will be ignored.

Restore of Cluster

To restore a database that operates as part of a failover cluster, you must start the restore process on the primary cluster node.


