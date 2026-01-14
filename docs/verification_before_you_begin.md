---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/verification_before_you_begin.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create and start a SureBackup job, check the following prerequisites:

* A valid Veeam Universal License of Veeam Backup & Replication must be installed on the backup server. When using a legacy socket-based license, Enterprise or higher edition is required.
* All applications and services on which verified machines are dependent must be virtualized in your environment.
* To perform full recoverability testing, you must create or connect a virtual lab. For more information, see sections [Creating Virtual Lab](create_vlab.md) and [Connecting to Existing Virtual Lab](connect_to_vlab.md).
* If you plan to verify Microsoft Windows machines, you must configure Microsoft Windows-based mount server. For more information, see [Mount Servers](mount_server.md).
* If you plan to scan machine data for malware, [check requirements and limitations](av_scan_about.md#av_limitations).
* If you plan to verify machines with a ping test, the firewall on tested machines must allow ping requests.
* If you plan to verify machines with a heartbeat test, VMware Tools must be installed in tested machines.
* [For storage snapshots] The storage system must be added to the backup infrastructure.

Consider the following limitations:

* Verified VM replicas must be in the Ready state. If a VM replica is in the Failover or Failback state, you will not be able to verify it with the SureBackup job.
* You cannot link the following machines backups to the SureBackup job: backups of VMware Cloud Director VMs, backups created by backup copy jobs and backups stored in [cloud backup repositories](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_repository.html?ver=13).
* The source backup or replication job has a higher priority than the SureBackup job. If the source backup or replication job starts when the SureBackup job is running, and this job is about to modify the restore point from which the VM is started, Veeam Backup & Replication automatically powers off VMs in the virtual lab and completes the SureBackup job.
* The Microsoft SQL Server Checker script runs on the backup server side. For this reason, Named Pipes or TCP/IP connections must be enabled for the Microsoft SQL Server running in the virtual lab. For more information, see [Microsoft Docs](https://msdn.microsoft.com/en-us/library/dd983822%28v%3Dnav.71%29.aspx).

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
