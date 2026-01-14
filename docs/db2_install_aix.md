---
title: "Installing Plug-In on IBM AIX"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_install_aix.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# Installing Plug-In on IBM AIX

In this article

Veeam Plug-In for IBM Db2 is an additional component of Veeam Backup & Replication. The installation package of the plug-in is included in the Veeam Backup & Replication installation ISO file and available for download from [veeam.com](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).

|  |
| --- |
| Important |
| Keep in mind the following:   * IBM Db2 must be installed on the machine. * The /opt/veeam directory must be writable.  * The NOEXEC mount option must be disabled for the /var and /tmp directories.  * To install Veeam Plug-In, use the sudo command or a user with root privileges. Make sure the root user has privileges to add the .PKG file.  * If you want to install Veeam Plug-In scale-out cluster, repeat the described installation process on all cluster nodes. |

To install Veeam Plug-In for IBM Db2 on an IBM AIX machine, perform the following steps:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. In the installation disk folder, navigate to the \Plugins\IBM Db2\AIX\ppc64 folder.

1. Upload the VeeamPluginforDB2-13.0.1.180-1.aix6.1.ppc.rpm package to the machine with IBM Db2.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for IBM Db2 from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).

1. Open the setup archive, in the \VeeamPluginforDB2-13.0.1.180\DB2\_AIX\ppc64 folder, find the VeeamPluginforDB2-13.0.1.180-1.aix6.1.ppc.rpm file.
2. Upload the VeeamPluginforDB2-13.0.1.180-1.aix6.1.ppc.rpm package to the machine with IBM Db2.

1. Install the plug-in from package with root privileges. Make sure the root user has privileges to add the PKG file.

|  |
| --- |
| rpm -i VeeamPluginforDB2-13.0.1.180-1.aix6.1.ppc.rpm |

Once Veeam Plug-In is installed, you must configure the plug-in settings. For details, see [Configuring Plug-In](db2_configure.md).

Page updated 1/6/2026

Page content applies to build 13.0.1.1071
