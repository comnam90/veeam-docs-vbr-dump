---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surebackup_before_you_begin_hv.html"
last_updated: "1/19/2026"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you create and start a recovery verification job, check the following prerequisites:

* A valid Veeam Universal License of Veeam Backup & Replication must be installed on the backup server. When using a legacy socket-based license, Enterprise or higher edition is required.

* All applications and services on which verified machines are dependent must be virtualized in your environment.
* You must create or connect a virtual lab. For more information, see sections [Creating Virtual Lab](vlab_hv.md) and [Connecting to Existing Virtual Lab](connect_to_vlab_hv.md).

* If you plan to scan machine data for malware, [check requirements and limitations](av_scan_about.md#av_limitations).
* If you plan to verify machines protected by Veeam Agent for Linux, a DHCP server must be available in the production network. During recovery verification, an additional Linux-based virtual machine (Helper Appliance) is registered on the target host. This appliance requires a DHCP server to obtain an IP address.

* If you plan to verify machines with a ping test, the firewall on tested machines must allow ping requests.
* If you plan to verify machines with a heartbeat test, Hyper-V Integration Services must be installed in tested machines.
* To open a console of a verified machine, you must have the RDP client version 7.0 and later installed on the backup server. The RDP client is pre-installed on Microsoft Windows 7 OS and later.

Consider the following limitations:

* You cannot link the following machines backups to the SureBackup job: backups created by backup copy jobs and backups stored in [cloud backup repositories](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_repository.html?ver=13).

* The source backup job has a higher priority than the SureBackup job. If the source backup job starts when the SureBackup job is running, and this job is about to modify the restore point from which the VM is started, Veeam Backup & Replication automatically powers off VMs in the virtual lab and completes the SureBackup job.


