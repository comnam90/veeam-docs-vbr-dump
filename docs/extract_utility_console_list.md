---
title: "Displaying List of Machines in Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/extract_utility_console_list.html"
last_updated: "11/22/2023"
product_version: "13.0.1.1071"
---

# Displaying List of Machines in Backup

In this article

This command displays the list of all machines in the backup file from which you want to perform restore.

Syntax

|  |
| --- |
| extract.exe -dir [-vm vmname] [-host hostname] [-password backupkey] pathtobackup |

Parameters

| Parameter | Description | Required/Optional |
| --- | --- | --- |
| vm | Name of the machine that you want to restore. Use this parameter to filter machines in the backup. | Optional |
| host | Name of the host on which the initial machine resides. Specify this parameter to filter machines that have the same name but reside on different hosts.  Note: This parameter must be specified if the vm parameter is used. | Optional |
| password | Password for the encrypted backup file. | Required for encrypted backup files |
| pathtobackup | Path to the backup file from which the machine must be restored. | Required |

Page updated 11/22/2023

Page content applies to build 13.0.1.1071
