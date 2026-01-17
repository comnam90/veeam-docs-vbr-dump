---
title: "Permanent Failover"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_permanent_failover.html"
last_updated: "11/9/2023"
product_version: "13.0.1.1071"
---


In this article

To finalize the failover process, a tenant can permanently fail over to the VM replica on the cloud host. A tenant can perform the permanent failover operation if they want to permanently switch from the original VM to a VM replica on the cloud host and use this replica as the original VM. As a result of permanent failover, the VM replica takes on the role of the original VM.

In the cloud replication scenario, you can perform permanent failover after full site failover. The permanent failover operation can be started by a tenant from the tenant Veeam backup console or by the SP from the SP Veeam backup console. To perform permanent failover for all VMs in the cloud failover plan, a tenant or the SP needs to process every VM in the cloud failover plan individually.

Permanent failover in the Veeam Cloud Connect Replication scenario practically does not differ from the regular permanent failover operation.

Permanent Failover for Snapshot-Based Replicas

The permanent failover operation for snapshot-based replicas is performed in the following way:

1. Veeam Backup & Replication removes snapshots (restore points) of the VM replica from the snapshot chain and deletes associated files from the storage (datastore or volume depending on the virtualization platform). Changes that were written to the snapshot delta file or differencing disk are committed to the VM replica disk files to bring the VM replica to the most recent state.
2. Veeam Backup & Replication removes the VM replica from the Veeam Backup & Replication console and database on the tenant side and SP side.
3. To protect the VM replica from corruption after permanent failover is complete, Veeam Backup & Replication reconfigures the replication job by adding the source VM to the list of exclusions. When the replication job starts, the original VM is skipped from processing. As a result, no data is written to the working VM replica. Note that other jobs are not modified automatically. When the replication job starts, the source VM is skipped from processing. As a result, no data is written to the working VM replica.

Permanent Failover for CDP Replicas

The permanent failover operation for CDP replicas is performed in the following way:

1. Veeam Backup & Replication powers off the replica.
2. Veeam Backup & Replication removes short-term and long-term restore points of the replica from the replication chain and deletes associated files from the datastore. Changes that were written to the protective virtual disks (<disk\_name>-interim.vmdk) are committed to the replica to bring the replica to the most recent state.
3. Veeam Backup & Replication removes the replica from the Veeam Backup & Replication console and database on the tenant side and SP side.
4. To protect the replica from corruption after permanent failover is complete, Veeam Backup & Replication reconfigures the current CDP policy by adding the source VM to the list of exclusions. Note that other policies and jobs are not modified automatically. When the CDP policy starts, the source VM is skipped from processing. As a result, no data is written to the working VM replica.

Page updated 11/9/2023

Page content applies to build 13.0.1.1071
