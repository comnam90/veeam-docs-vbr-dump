---
title: "Step 3. Specify Packages"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/protection_group_packages.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# Step 3. Specify Packages

In this article

At the Package step of the wizard, specify what setup files you want to obtain to deploy Veeam Agents. Veeam Backup & Replication will export the specified setup files to the specified folder. Then, you must use these setup files to deploy Veeam Agents on computers you plan to protect. To learn more, see [Deploying Veeam Agents Using Generated Setup Files](agents_deploy_package.md).

To specify setup files to export:

1. In the Export path field, click Browse.
2. In the Select Folder window, specify a path to the folder to which Veeam Backup & Replication will export Veeam Agent setup files. Setup files can be exported to the following locations:

* If you use Veeam Backup & Replication on Linux, setup files are exported to a folder on the server where the Veeam Backup & Replication console is installed.
* If you use Veeam Backup & Replication on Microsoft Windows, setup files can be exported:

* To a folder on the server where the Veeam Backup & Replication console is installed.
* To a folder on the local drive of the Veeam backup server.
* To an SMB network shared folder accessible from the Veeam backup server.

1. In the Agent installation packages to export field, select setup files depending on the type of the OS that runs on computers you plan to add to the protection group.

1. If you plan to protect Windows computers, select the Microsoft Windows package option.
2. If you plan to protect Mac computers, select the Apple Mac package with the device profile option.
3. If you plan to protect Unix computers, expand the Unix Packages option and select packages for specific Unix distributions.

If you select the Unix Packages option, Veeam Backup & Replication will export setup files for all Unix distributions supported by Veeam Agent for IBM AIX and Veeam Agent for Oracle Solaris.

1. If you plan to protect Linux computers, expand the Linux packages for supported distributions option and select options depending on the distributions you need.

|  |
| --- |
| NOTE |
| You can also export installation packages of the nosnap version of Veeam Agent for Linux (including Veeam Agent for Linux on Power) for the supported Linux distributions. |

If you select the Linux packages for supported distributions option, Veeam Backup & Replication will export setup files for all Linux distributions supported by Veeam Agent for Linux.

1. Click Advanced to specify advanced settings for the protection group. To learn more, see [Specify Advanced Protection Group Settings](pg_pre_installed_advanced.md).

![Step 3. Specify Packages](images/protection_group_packages.webp "Specify Packages")

Page updated 11/13/2025

Page content applies to build 13.0.1.1071
