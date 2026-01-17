---
title: "Starting PowerShell Sessions from PowerShell Console"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/from_windows_powershell.html"
last_updated: "11/27/2025"
product_version: "13.0.1.1071"
---

# Starting PowerShell Sessions from PowerShell Console


You can run Veeam Explorers cmdlets from the PowerShell command-line shell.

Using Veeam Explorers Cmdlets for Backups and Replicas Created with Veeam Backup & Replication

You can run Veeam Explorers cmdlets on [machines where the Veeam Backup & Replication console is installed](#windows_machines) and on [Linux machines](#linux_machines).

Machines With Veeam Backup & Replication Console

To use Veeam Explorers cmdlets on a machine where the Veeam Backup & Replication console is installed, perform the following steps:

1. Start a PowerShell session. For more information on starting the session, see [this Microsoft article](https://docs.microsoft.com/en-us/powershell/scripting/windows-powershell/starting-windows-powershell?view=powershell-7.5).
2. Run the [Connect-VBRServer](https://helpcenter.veeam.com/docs/vbr/powershell/connect-vbrserver.html?ver=13) cmdlet to connect to a local or remote backup server.

Linux Machines

You can run Veeam Explorer cmdlets on a Veeam Software Appliance or other Linux machines.

* If you want to run Veeam Explorer cmdlets on a Veeam Software Appliance, note that the necessary services and PowerShell modules are already installed.

Before you begin, you must enable SSH connections and root shell access to the Veeam Software Appliance. For details, see the [Configuring Remote Access Settings](https://helpcenter.veeam.com/docs/vbr/userguide/hmc_configure_remote_access.html?ver=13#managing-ssh-access) section of the Veeam Backup & Replication User Guide.

To import the modules and connect to the backup server, perform the following steps:

1. Start a PowerShell session to use PowerShell commands.

|  |
| --- |
| pwsh |

1. Run the Import-Module cmdlet to import the necessary PowerShell modules. For example, to import Veeam Backup PowerShell Module and all Veeam Explorer modules available on Linux machines, run the following commands:

|  |
| --- |
| Import-Module /opt/veeam/powershell/Veeam.Backup.PowerShell/Veeam.Backup.PowerShell.psd1  Import-Module /opt/veeam/veeam-saphana-powershell/Veeam.SapHana.PowerShell/Veeam.SapHana.PowerShell.psd1  Import-Module /opt/veeam/veeam-oracle-powershell/Veeam.Oracle.PowerShell/Veeam.Oracle.PowerShell.psd1get-o  Import-Module /opt/veeam/veeam-postgresql-powershell/Veeam.PostgreSQL.PowerShell/Veeam.PostgreSQL.PowerShell.psd1  Import-Module /opt/veeam/veeam-mongodb-powershell/Veeam.MongoDB.PowerShell/Veeam.MongoDB.PowerShell.psd1 |

The remaining Veeam Explorers PowerShell modules are not supported on Linux machines.

1. Run the [Connect-VBRServer](https://helpcenter.veeam.com/docs/vbr/powershell/connect-vbrserver.html?ver=13) cmdlet to connect to a backup server.

* If you want to run Veeam Explorer cmdlets on another Linux machine, make sure the machine meets the following requirements:

* The machine is running one of the following Linux distributions:

* Rocky Linux 9 latest version
* RHEL 9.6

* ASP.NET Core Runtime 8.0 environment or later is installed on the machine. To install this package, run the following command:

|  |
| --- |
| dnf install aspnetcore-runtime-8.0 -y |

* Windows PowerShell version 7 or later is installed on the machine. For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/powershell/scripting/install/install-rhel?view=powershell-7.5).

Once these requirements are met, perform the following steps:

1. Add the repository containing Veeam Software Appliance packages:

|  |
| --- |
| dnf install https://repository.veeam.com/rocky/9.2/vbr/13.0/optional/x86\_64/veeam-optional-release-latest-13.0.1.180-1.x86\_64.rpm -y |

This command gives the dnf package manager access to the necessary Veeam Software Appliance packages.

1. Install the Veeam Explorers PowerShell modules and Veeam services required for restore operations:

|  |
| --- |
| dnf install veeam-powershell -y  dnf install veeam-vbr-pkg-mount.x86\_64 veeam-vbr-pkg-transport.x86\_64 veeam-vbr-pkg-deployment.x86\_64 -y  dnf install /opt/veeam/vbr/Packages/veeamdeployment-13.0.1.180-1.x86\_64.rpm -y  dnf install /opt/veeam/vbr/Packages/veeam-mount-13.0.1.180-1.x86\_64.rpm -y  dnf install /opt/veeam/vbr/Packages/veeamtransport-13.0.1.180-1.x86\_64.rpm -y |

1. Start a PowerShell session to use PowerShell commands.

|  |
| --- |
| pwsh |

1. Run the Import-Module cmdlet to import the necessary PowerShell modules. For example, to import Veeam Backup PowerShell Module and all Veeam Explorer modules available on Linux machines, run the following commands:

|  |
| --- |
| Import-Module /opt/veeam/powershell/Veeam.Backup.PowerShell/Veeam.Backup.PowerShell.psd1  Import-Module /opt/veeam/veeam-saphana-powershell/Veeam.SapHana.PowerShell/Veeam.SapHana.PowerShell.psd1  Import-Module /opt/veeam/veeam-oracle-powershell/Veeam.Oracle.PowerShell/Veeam.Oracle.PowerShell.psd1get-o  Import-Module /opt/veeam/veeam-postgresql-powershell/Veeam.PostgreSQL.PowerShell/Veeam.PostgreSQL.PowerShell.psd1  Import-Module /opt/veeam/veeam-mongodb-powershell/Veeam.MongoDB.PowerShell/Veeam.MongoDB.PowerShell.psd1 |

The remaining Veeam Explorers PowerShell modules are not supported on Linux machines.

1. Run the [Connect-VBRServer](https://helpcenter.veeam.com/docs/vbr/powershell/connect-vbrserver.html?ver=13) cmdlet to connect to a backup server.

Using Veeam Explorers Cmdlets for Backups Created with Veeam Backup for Microsoft 365

When you install Veeam Backup for Microsoft 365 and Veeam Explorers, all related PowerShell modules are automatically imported into the active memory. If your PowerShell session was opened before you start installation of Veeam Backup for Microsoft 365, run the Import-Module cmdlet to import the Veeam.Archiver.PowerShell module and Veeam Explorers modules. For example:

|  |
| --- |
| Import-Module "C:\Program Files\Veeam\Backup365\Veeam.Archiver.PowerShell\Veeam.Archiver.PowerShell.psd1"  Import-Module "C:\Program Files\Veeam\Backup and Replication\Explorers\Exchange\Veeam.Exchange.PowerShell\Veeam.Exchange.PowerShell.psd1"  Import-Module "C:\Program Files\Veeam\Backup and Replication\Explorers\SharePoint\Veeam.SharePoint.PowerShell\Veeam.SharePoint.PowerShell.psd1"  Import-Module "C:\Program Files\Veeam\Backup and Replication\Explorers\Teams\Veeam.Teams.PowerShell\Veeam.Teams.PowerShell.psd1" |

To use Veeam Explorer cmdlets for Veeam Backup for Microsoft 365, perform the following steps:

1. Start a PowerShell session on a machine that has Veeam Backup for Microsoft 365 PowerShell installed. For more information on starting the session, see [this Microsoft article](https://docs.microsoft.com/en-us/powershell/scripting/windows-powershell/starting-windows-powershell?view=powershell-7.5).
2. Connect to a local or remote Veeam Backup for Microsoft 365 server.

For more information on how to connect to Veeam Backup for Microsoft 365 server, see [Connect-VBOServer](https://helpcenter.veeam.com/docs/vbo365/powershell/connect-vboserver.html?ver=80).


