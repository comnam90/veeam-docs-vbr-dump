---
title: "Restoring VMs from Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/extract_utility_console_restore.html"
last_updated: "11/22/2023"
product_version: "13.0.1.1071"
---

# Restoring VMs from Backup

In this article

This command restores data for all machines or for the selected machine from the backup file.

Syntax

|  |
| --- |
| extract.exe -restore [-vm vmname] [-host hostname] [-password backupkey] pathtobackup [outputdir] [-log] |

Parameters

| Parameter | Description | Required/Optional |
| --- | --- | --- |
| vm | Name of the machine that you want to restore. Use this parameter to filter machines in the backup. If you want to restore all machines from the backup file, do not specify this parameter. | Optional |
| host | Name of the host on which the initial machine resides. Specify this parameter to filter machines that have the same name but reside on different hosts.  Note: This parameter must be specified if the vm parameter is used. | Optional |
| pathtobackup | Path to the backup file from which the machine must be restored. | Required |
| password | Password for the encrypted backup file. | Required for encrypted backup files |
| outputdir | Path to the directory to which machine data must be restored. If this parameter is not specified, the machine will be restored to the current directory. | Optional |
| log | SwitchParameter. Enables log creation. The log file will be created in the current directory. | Optional |

Example

This command restores winsrv29 machine from an encrypted backup file to the C:/Backup directory.

|  |
| --- |
| extract.exe -restore -vm winsrv29 -password "standard 1" "C:/Backup/Single/Backup Job Single StorageD2022-10-03T132735\_1E50.vbk" C:/backup |

Page updated 11/22/2023

Page content applies to build 13.0.1.1071
