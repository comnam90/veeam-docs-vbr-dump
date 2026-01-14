---
title: "Running Veeam PowerShell Session from Linux Machines"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/running_ps_sessions_linux.html"
last_updated: "11/26/2025"
product_version: "13.0.1.1071"
---

# Running Veeam PowerShell Session from Linux Machines

In this article

Veeam Backup & Replication supports usage of Veeam Backup PowerShell on a Veeam Software Appliance or other Linux machines. To run cmdlets on a Veeam Software Appliance, you need to enable SSH connections and root shell access and import the Veeam Backup PowerShell Module. Before you run the cmdlets on a Linux machine, you must create an optional repository for the Veeam package, install the Veeam Backup PowerShell module and import it to your Linux system. After that, you can connect to the backup server.

Requirements

Consider the following requirements:

* You can run the Veeam Backup PowerShell module on the following Linux distributions:

* Rocky Linux 9 latest version.
* RHEL 9.6.

* To run Veeam Backup PowerShell cmdlets on a Linux machine, you must install the following components:

1. Install the ASP.NET Core Runtime 8.0 environment or later:

|  |
| --- |
| dnf install aspnetcore-runtime-8.0 -y |

1. Install Windows PowerShell. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/powershell/scripting/install/install-rhel?view=powershell-7.5).

* To run Veeam PowerShell cmdlets, you must have Veeam Backup Administrator role. For more information, see [Users and Roles](https://helpcenter.veeam.com/docs/vbr/userguide/users_roles.html?ver=13).
* A machine that runs the PowerShell session must have Windows PowerShell version 7 installed.
* To utilize the Veeam Explorer PowerShell functionality, you must install the necessary Veeam Explorer PowerShell modules. For more information, see [Starting PowerShell Sessions](https://helpcenter.veeam.com/docs/vbr/explorers_powershell/ps_sessions.html?ver=13) in the Veeam Explorers PowerShell Reference.

Configuring Veeam Backup PowerShell on Veeam Software Appliance

1. Enable SSH connections and root shell access to the Veeam Software Appliance. For more information, see the [Configuring Remote Access Settings](https://helpcenter.veeam.com/docs/vbr/userguide/hmc_configure_remote_access.html?ver=13#managing-ssh-access) section of the Veeam Backup & Replication User Guide.
2. Start a PowerShell session to use PowerShell commands.

|  |
| --- |
| pwsh |

1. Import the Veeam Backup PowerShell Module:

|  |
| --- |
| Import-Module /opt/veeam/powershell/Veeam.Backup.PowerShell/Veeam.Backup.PowerShell.psd1 |

1. Connect to the Veeam backup server:

|  |
| --- |
| Connect-VBRServer -Server "192.24.125.135" -User "veeamadmin" -Password "Password" |

Configuring Veeam Backup PowerShell on Linux Machines

To be able to perform operations Veeam Backup PowerShell on Linux machines, perform the following steps:

1. Create an optional Linux repository:

|  |
| --- |
| dnf install <https://repository.veeam.com/rocky/9.2/vbr/13.0/optional/x86_64/veeam-optional-release-latest-13.0.1.180-1.x86_64.rpm> -y |

1. Install the Veeam Backup PowerShell Module:

|  |
| --- |
| dnf install veeam-powershell -y |

1. Start a PowerShell session to use PowerShell commands.

|  |
| --- |
| pwsh |

1. Import the Veeam Backup PowerShell Module:

|  |
| --- |
| Import-Module /opt/veeam/powershell/Veeam.Backup.PowerShell/Veeam.Backup.PowerShell.psd1 |

1. Connect to a Veeam backup server:

|  |
| --- |
| Connect-VBRServer -Server "192.24.125.135" -User "veeamadmin" -Password "Password" |

Page updated 11/26/2025

Page content applies to build 13.0.1.1071
