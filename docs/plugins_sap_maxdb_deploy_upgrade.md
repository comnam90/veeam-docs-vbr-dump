---
title: "Upgrading Veeam Plug-In for SAP MaxDB"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_deploy_upgrade.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Upgrading Veeam Plug-In for SAP MaxDB


Periodically, Veeam releases a new version of Veeam Backup & Replication that contains new features and bug fixes. The release package also contains a new version of Veeam Plug-Ins.

Veeam Backup & Replication 13 supports different versions of Veeam Plug-In depending on which OS is running on the backup server:

* Veeam Backup & Replication on Linux supports management of Veeam Plug-Ins 13. Management of previous versions of Veeam Plug-Ins is not supported.
* Veeam Backup & Replication on Microsoft Windows supports management of Veeam Plug-Ins 12.3.2.4165 and later.

Note that Veeam Backup & Replication must be the same or later than the version of Veeam Plug-In. If you want to use the latest functionality, you must upgrade both Veeam Backup & Replication and Veeam Plug-In to the latest version. If you use an earlier Veeam Plug-In build, it may not have all the features and bug fixes introduced in your Veeam Backup & Replication version. To learn more about the Veeam Plug-In builds included in Veeam Backup & Replication installation ISO files, see [this Veeam KB article](https://www.veeam.com/kb4474).

To restore data from a backup, the version of Veeam Plug-In must be the same or later than the version that created the backup. Restore with an earlier version of Veeam Plug-In from a backup created with a later version is not supported and may cause the restore to fail. This limitation applies to build numbers, not only major versions. For example, you cannot use Veeam Plug-In build 13.0.1.1071 to restore data from a backup created with build 13.0.1.2067.

|  |
| --- |
| Important |
| Consider the following:   * You must upgrade Veeam Backup & Replication before you upgrade Veeam Plug-Ins. To learn how to upgrade Veeam Backup & Replication, see [Upgrade and Update](vbr_updating.md).  * Operations in the terminal of the machine with the database require root privileges. * If SAP MaxDB operates as part of a failover cluster, repeat the upgrade process on each cluster node. |

Before You Begin

Veeam Plug-In installation files are included in the installation image of Veeam Backup & Replication and available for download from [veeam.com](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins). You must get the installation files on the SAP MaxDB server. To do this, perform the following steps:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. Open the mounted image and find the following packages:

1. [For Linux] In the \Packages folder, find the openssl-fips-redistributable-3.1.2-3.1.2.2-1.x86\_64.rpm package.
2. [For Linux] In the \Plugins\SAP MaxDB\Linux folder, find the Veeam Plug-In installation file that suits your OS.
3. [For IBM AIX] In the \Plugins\SAP MaxDB\AIX\ppc64 folder, find the VeeamPluginforSAPMaxDB-13.1.0.411-1.aix6.1.ppc.rpm package.

1. Upload packages that you need to the SAP MaxDB server.

Using veeam.com

1. Download the current setup archive for Veeam Plug-In for SAP MaxDB from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. Open the setup archive and find the following packages:

1. [For Linux] In the \VeeamPluginforSAPMaxDB-13.1.0.411\openssl-fips-redistributable-3.1.2 folder, find the openssl-fips-redistributable-3.1.2-3.1.2.2-1.x86\_64.rpm package.
2. [For Linux] In the \VeeamPluginforSAPMaxDB-13.1.0.411\x64 folder, find the Veeam Plug-In installation file that suits your OS.
3. [For IBM AIX] In the \VeeamPluginforSAPMaxDB-13.1.0.411\AIX\ppc64 folder, find the VeeamPluginforSAPMaxDB-13.1.0.411-1.aix6.1.ppc.rpm package.

1. Upload packages that you need to the SAP MaxDB server.

After you uploaded the files, you can upgrade Veeam Plug-In. The upgrade procedure depends on the type of package and OS that you use:

* [Upgrading Plug-In on Linux (.RPM)](#rpm)
* [Upgrading Plug-In on Linux (.TAR.GZ)](#tar)
* [Upgrading Plug-In on IBM AIX](#aix)

After the upgrade, you do not need to reconfigure Veeam Plug-In, the plug-in configuration files will be preserved.

Upgrading Plug-In on Linux (.RPM)

To upgrade Veeam Plug-In for SAP MaxDB on a Linux machine, do the following:

1. Upload openssl-fips-redistributable-3.1.2-3.1.2.2-1.x86\_64.rpm and VeeamPluginforSAPMaxDB-13.1.0.411-1.x86\_64.rpm packages to the SAP MaxDB server.
2. To upgrade Veeam Plug-In, run the following commands:

1. Install the openssl-fips-redistributable-3.1.2 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| rpm -i openssl-fips-redistributable-3.1.2-3.1.2.2-1.x86\_64.rpm |

1. To upgrade Veeam Plug-In, run the following command:

|  |
| --- |
| rpm -U VeeamPluginforSAPMaxDB-13.1.0.411-1.x86\_64.rpm |

|  |
| --- |
| Tip |
| To find out which version of Veeam Plug-In is installed on your server, you can use the following command: rpm -qa | grep VeeamPlugin |

Upgrading Plug-In on Linux (.TAR.GZ)

To upgrade Veeam Plug-In for SAP MaxDB on a Linux machine from the archive, do the following:

1. Upload openssl-fips-redistributable-3.1.2-3.1.2.2-1.x86\_64.rpm and VeeamPluginforSAPMaxDB.tar.gz files to the SAP MaxDB server.
2. Install the openssl-fips-redistributable-3.1.2 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| rpm -i openssl-fips-redistributable-3.1.2-3.1.2.2-1.x86\_64.rpm |

1. Unpack the plug-in files from the archive to the /opt/veeam directory. Old Veeam Plug-In files will be replaced by new files.

|  |
| --- |
| tar -xzvf VeeamPluginforSAPMaxDB.tar.gz -C /opt/veeam |

Upgrading Plug-In on IBM AIX

To upgrade Veeam Plug-In for SAP MaxDB on an IBM AIX machine, do the following:

1. Upload the VeeamPluginforSAPMaxDB-13.1.0.411-1.aix6.1.ppc.rpm package to the SAP MaxDB server.
2. To upgrade Veeam Plug-In, run the following command. Note that the operation requires root privileges.

|  |
| --- |
| rpm -U VeeamPluginforSAPMaxDB-13.1.0.411-1.aix6.1.ppc.rpm |

Page updated 2026-08-04

