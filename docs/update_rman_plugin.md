---
title: "Upgrading Veeam Plug-In for Oracle RMAN"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/update_rman_plugin.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# Upgrading Veeam Plug-In for Oracle RMAN

In this article

Periodically, Veeam releases a new version of Veeam Backup & Replication that contains new features and bug fixes. The release package also contains a new version of Veeam Plug-Ins.

Veeam Backup & Replication 13 supports different versions of Veeam Plug-In depending on which OS is running on the backup server:

* Veeam Backup & Replication on Linux supports management of Veeam Plug-Ins 13. Management of previous versions of Veeam Plug-Ins is not supported.
* Veeam Backup & Replication on Microsoft Windows supports management of Veeam Plug-Ins 12.3.2.4165 and later.

Note that Veeam Backup & Replication must be the same or later than the version of Veeam Plug-In. If you want to use the latest functionality, you must upgrade both Veeam Backup & Replication and Veeam Plug-In to the latest version. If you use an earlier Veeam Plug-In build, it may not have all the features and bug fixes introduced in your Veeam Backup & Replication version. To learn more about the Veeam Plug-In builds included in Veeam Backup & Replication installation ISO files, see [this Veeam KB article](https://www.veeam.com/kb4474).

|  |
| --- |
| Important |
| Consider the following:   * You must upgrade Veeam Backup & Replication before you upgrade Veeam Plug-Ins. To learn how to upgrade Veeam Backup & Replication, see [Upgrade and Update](vbr_updating.md).  * [For Linux computers] Operations in the terminal of the machine with the database require root privileges. |

Before You Begin

Veeam Plug-In installation files are included in the installation image of Veeam Backup & Replication and available for download from [veeam.com](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins). You must get the installation files on the Oracle server. To do this, perform the following steps:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. Open the mounted image and find the following packages:

1. [For Linux] In the \Packages folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \Plugins\Oracle RMAN folder, find the Veeam Plug-In installation file that suits your OS.

1. Upload packages that you need to the Oracle server.

Using veeam.com

1. Download the current setup archive for Veeam Plug-In for Oracle RMAN from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. Open the setup archive and find the following packages:

1. [For Linux] In the \VeeamPluginforOracleRMAN-13.0.1.180-1\veeam-openssl3 folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \VeeamPluginforOracleRMAN-13.0.1.180-1\ folder, find the Veeam Plug-In installation file that suits your OS.

1. Upload packages that you need to the Oracle server.

After you uploaded the files, you can upgrade Veeam Plug-In. The upgrade procedure depends on the type of package and OS that you use:

* [Upgrading Plug-In on Microsoft Windows](#win)
* [Upgrading Plug-In on Linux (.RPM)](#lin)
* [Upgrading Plug-In on Linux (.TAR.GZ)](#tar)
* [Upgrading Plug-In on Oracle Solaris](#sol)
* [Upgrading Plug-In on IBM AIX](#aix)

Upgrading Plug-In on Windows

To upgrade Veeam Plug-In for Oracle RMAN on a Windows machine, upload the VeeamPluginforOracleRMAN.exe file of the new version to the Oracle Database server and install it. The first launch of the file will remove the old version. The second launch will install the new version.

You can upgrade Veeam Plug-In for Oracle RMAN to a later version in the unattended mode using the same command that is used for unattended installation. For details, see [Installing Plug-In on Windows Machine in Unattended Mode](install_plugin_windows.md#unat).

Upgrading Plug-In on Linux (.RPM)

To upgrade Veeam Plug-In for Oracle RMAN on a Linux machine, do the following:

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforOracleRMAN-13.0.1.180-1.x86\_64.rpm packages to the Oracle server.
2. Install the veeam-openssl3 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| rpm -i veeam-openssl3-3.0.0.31-1.x86\_64.rpm |

1. To upgrade Veeam Plug-In, run the following command. Note that the operation requires root privileges.

|  |
| --- |
| rpm -U VeeamPluginforOracleRMAN-13.0.1.180-1.x86\_64.rpm |

|  |
| --- |
| Tip |
| To find out which version of Veeam Plug-In is installed on your server, you can use the following command: rpm -qa | grep VeeamPlugin |

Upgrading Plug-In on Linux (.TAR.GZ)

To upgrade Veeam Plug-In for Oracle RMAN on a Linux machine from the .TAR.GZ archive, do the following:

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforOracleRMAN.tar.gz files to the Oracle server.
2. Install the veeam-openssl3 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| rpm -i veeam-openssl3-3.0.0.31-1.x86\_64.rpm |

1. Unpack the plug-in files from the archive to the /opt/veeam directory. Old Veeam Plug-In files will be replaced by new files.

|  |
| --- |
| tar -xzvf VeeamPluginforOracleRMAN.tar.gz -C /opt/veeam |

Upgrading Plug-In on Oracle Solaris

To upgrade Veeam Plug-In for Oracle RMAN on an Oracle Solaris machine, do the following:

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforOracleRMAN-13.0.1.180-1.SPARC.pkg package to the Oracle server. If you need the 32-bit version, choose the i386 package.

1. Make sure the pkgadd administration file (admin\_file) contains the following entry: "instance=overwrite". For details, see [this Oracle article](https://docs.oracle.com/cd/E26505_01/html/E29492/swmgrpkgs-19113.html).
2. To upgrade Veeam Plug-In, run the following command:

|  |
| --- |
| pkgadd -a admin\_file -d /tmp/VeeamPluginforOracleRMAN-13.0.1.180-1.SPARC.pkg |

Upgrading Plug-In on IBM AIX

To upgrade Veeam Plug-In for Oracle RMAN on an IBM AIX machine, do the following:

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforOracleRMAN-13.0.1.180-1.aix6.1.ppc.rpm package to the Oracle server.

1. To upgrade Veeam Plug-In, run the following command. Note that the operation requires root privileges.

|  |
| --- |
| rpm -U VeeamPluginforOracleRMAN-13.0.1.180-1.aix6.1.ppc.rpm |

Page updated 1/6/2026

Page content applies to build 13.0.1.1071
