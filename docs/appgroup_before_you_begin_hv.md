---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/appgroup_before_you_begin_hv.html"
last_updated: "8/7/2024"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create and start a recovery verification job, check the following prerequisites:

* A valid license for Enterprise edition of Veeam Backup & Replication must be installed on the backup server.
* All applications and services on which verified machines are dependent must be virtualized in your environment.
* If you plan to scan machines data for malware, [check requirements and limitations](av_scan_about.md#av_limitations).
* If you plan to verify machines with a ping test, the firewall on tested machines must allow ping requests.
* If you plan to verify machines with a heartbeat test, Hyper-V Integration Services must be installed in tested machines.

* If backup file that is used to add the machine to an application group cannot be found, Veeam Backup & Replication will search for other backup files containing this machine.

* To open a console of a verified machine, you must have the RDP client version 7.0 and later installed on the backup server. The RDP client is pre-installed on Microsoft Windows 7 OS and later.
* You cannot add to application groups VMs from backups created with backup copy jobs and backups stored in Cloud Connect backup repositories.

Page updated 8/7/2024

Page content applies to build 13.0.1.1071
