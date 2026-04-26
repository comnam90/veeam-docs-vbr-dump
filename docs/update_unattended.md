---
title: "Updating Veeam Backup & Replication in Silent Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/update_unattended.html"
last_updated: "7/21/2025"
product_version: "13.0.1.2067"
---

# Updating Veeam Backup & Replication in Silent Mode


Veeam Backup & Replication updates can be installed in the silent mode.

To install a Veeam Backup & Replication update, perform the following steps:

1. [Download the update installation archive and extract the executable file](#download).
2. [Install the update on the backup server](#install).

|  |
| --- |
| ![Updating Veeam Backup & Replication in Silent Mode](images/icon_important.webp)Important! |
| The script that installs Veeam Backup & Replication updates must be run with elevated privileges (run as Administrator). |

Step 1. Download and Extract Executable File

Download and extract the executable file for update installation:

1. Download the installation archive for the Veeam Backup & Replication update from the Release Notes page for a certain update/patch. For example, for v12.1 updates, download the latest patch from [this Veeam KB article](https://www.veeam.com/kb4510).
2. Extract the executable file from the downloaded archive.
3. Save the extracted file locally on the backup server where you plan to install the update, or place it in a network shared folder.

Alternatively, you can get the update/patch executable file from the Updates folder on the downloaded ISO image.

Step 2. Install Update

To install the Veeam Backup & Replication update on the backup server, use the following command syntax:

|  |
| --- |
| %patch% [/silent][/noreboot][/log <log\_path>][VBR\_AUTO\_UPGRADE="1"] |

The command has the following parameters:

Step 2. Install Update

| Option | Parameter | Required | Description |
| %patch% | path | Yes | Specifies a path to the update installation file on the backup server or in a network shared folder.  Example: C:\Temp\VeeamBackup&Replication\_11.0.1.1261\_20220302.exe |
| silent | — | Yes | Sets the user interface level to “no”, which means no user interaction is needed during installation. |
| noreboot | — | No | Suppresses reboot if reboot is required during the Veeam Backup & Replication update installation. |
| log | path | No | Specifies a full path to the log file for the Veeam Backup & Replication update installation.  Example: C:\Logs\veeam.log |
| VBR\_AUTO\_UPGRADE | 0/1 | No | Specifies if you want Veeam Backup & Replication to automatically upgrade existing components in the backup infrastructure. Veeam Backup & Replication performs automatic upgrade after the Veeam Backup Service is started on the backup server.  Specify 1 to enable automatic upgrade.  Example: VBR\_AUTO\_UPGRADE="1" |

For example:

You want to install the Veeam Backup & Replication update with the following options:

* Path to the update installation file: C:\Temp\VeeamBackup&Replication\_12.0.0.1420\_20230223.exe
* Silent install: enabled
* Noreboot: enabled
* Path to the log file: C:\Logs\veeam.log
* Components auto upgrade: enabled

The command to install the Veeam Backup & Replication update will be the following:

|  |
| --- |
| C:\Temp\VeeamBackup&Replication\_12.0.0.1420\_20230223.exe /silent /noreboot /log C:\Logs\veeam.log VBR\_AUTO\_UPGRADE="1" |

Installation Results

You can use the last exit code to verify if the installation process has completed successfully.

* In cmd.exe, use the %ERRORLEVEL% variable to check the last exit code.
* In Microsoft Windows PowerShell, use the $LastExitCode variable to check the last exit code.

Veeam Backup & Replication does not provide any confirmation about the results of automatic components upgrade. To check if components have been successfully upgraded, use the Veeam Backup & Replication console.

Related Topics

* [Updating Veeam Backup & Replication](update_vbr_windows.md)
* [Installing Veeam Backup & Replication in Silent Mode](install_vbr_answer_file.md)


