---
title: "Using Group Managed Service Accounts"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/using_gmsa.html"
last_updated: "1/9/2026"
product_version: "13.0.1.1071"
---

# Using Group Managed Service Accounts

In this article

A Group Managed Service Account (gMSA) is the type of domain account configured on the server. It does not need the administrator to manage the password as this role is performed by the Microsoft Windows operating system. Randomly generated complex passwords are automatically changed every 30 days which reduce the risk of brute force and dictionary attacks. For more information about gMSAs, see [this Microsoft article](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/service-accounts-group-managed).

You can use gMSAs to only run guest processing tasks.

|  |
| --- |
| Note |
| For application-aware processing, using a gMSA is supported for backups or replicas of VMs that run Microsoft Active Directory (domain controllers), Microsoft Exchange, Microsoft SQL Server, and Oracle 12c Release 2 and later. You cannot back up or replicate VMs that run Microsoft SharePoint with the gMSA. |

Requirements and Limitations

gMSAs have the following requirements and limitations:

* To use gMSAs, a Windows server must be selected as the guest interaction proxy for the backup job. Consider the following:

* If you use automatic proxy selection, a Windows server will be selected automatically.
* If you use specific servers as guest interaction proxies, at least one Windows server must be selected as a preferred server.

For more information on proxy selection, see [Creating Backup Jobs](backup_job.md).

* gMSAs are applicable to Microsoft Windows Server 2012 and later. For more information about operating system and Microsoft Active Directory requirements, see [this Microsoft article](https://docs.microsoft.com/en-us/windows-server/security/group-managed-service-accounts/getting-started-with-group-managed-service-accounts#BKMK_gMSA_Req).

|  |
| --- |
| Note |
| Consider that this section describes the gMSA configuration compatible with most environments. To reduce the number of possible issues, it is recommended to perform all required steps to configure the domain controller and implement the gMSA. |

* gMSAs are not supported for backups of the Linux target machines joined to the Active Directory domain.

* When using gMSAs for guest processing, consider the following:

+ For backup and replication jobs:

* A guest interaction proxy must be joined to the Active Directory domain where the gMSA was created.
* The gMSA must also have Logon as a service permission granted.

+ For CDP policies, the backup server must be joined to the Active Directory domain where the gMSA was created.

* Veeam Explorers do not support data recovery using gMSAs.
* Since gMSAs require a connection to the domain controller, these accounts work only over network.
* If you use gMSAs to manage the restore process of VM guest OS files, consider [Requirements and Limitations](guest_restore_before_you_begin.md).
* If you back up a machine using a gMSA, both the guest interaction proxy and the target machine must have network access to the domain controllers and be in the same domain to obtain the gMSA password. On the target machine the gMSA must be added to the Administrators group (local or domain). Domain Administrator permissions are only required for Microsoft Active Directory backups, for other supported applications local Administrator permissions are sufficient.

|  |
| --- |
| Important |
| Consider that granting Domain Administrator permissions to gMSAs makes them a potential source of vulnerability. |

Before You Begin

Before you start using gMSAs, configure the domain controller:

1. The domain controller requires a root key to generate gMSA passwords. Ensure that the Key Distribution Service is enabled on the domain controller and use the following command in Microsoft Windows PowerShell to generate a root key:

|  |
| --- |
| Add-KdsRootKey -EffectiveImmediately |

Wait until the Active Directory replication is finished or force it manually. For more information about creating KDS root keys, see [this Microsoft article](https://learn.microsoft.com/en-us/windows-server/security/group-managed-service-accounts/create-the-key-distribution-services-kds-root-key#to-create-the-kds-root-key-using-the-add-kdsrootkey-cmdlet).

1. To enable gMSA support in Microsoft Windows PowerShell, use the following commands:

|  |
| --- |
| Install-WindowsFeature RSAT-AD-PowerShell,NET-Framework-Features | Out-Null;  Import-Module ServerManager;  Import-Module ActiveDirectory; |

Creating gMSA

To create a gMSA, use the New-ADServiceAccount cmdlet on the domain controller. For example:

|  |
| --- |
| $gMSAName = 'DOMAIN\gmsa01'  $gMSAGroupName = 'gMSAComputerAccountsGroup'  $gMSADNSHostName = 'gmsa01.srv.local'  New-ADServiceAccount -Name $gMSAName -DNSHostName $gMSADNSHostName -PrincipalsAllowedToRetrieveManagedPassword $gMSAGroupName -Enabled $True |

Consider the following:

* In the DNSHostName parameter, specify the FQDN of the gMSA.
* For the PrincipalsAllowedToRetrieveManagedPassword parameter specify the AD group containing computer accounts which will use the gMSA. As an alternative, specify computer accounts separated by comma.
* By default, created gMSAs are shown in the Managed Service Accounts container.

For more information about all cmdlet parameters, see [this Microsoft article](https://docs.microsoft.com/en-us/windows-server/security/group-managed-service-accounts/getting-started-with-group-managed-service-accounts#BKMK_CreateGMSA).

|  |
| --- |
| Note |
| To provide a more secure environment, use separate gMSAs for critical backup infrastructure components. |

To refresh AD group membership after you create a gMSA, run the following command on the machines on which you plan to install the gMSA:

|  |
| --- |
| C:\WINDOWS\system32\klist.exe -lh 0 -li 0x3e7 purge |

Alternatively, you can reboot these machines.

Adding gMSA

To add a gMSA on the server or the target machine, add the gMSA to the local Administrators group:

|  |
| --- |
| Add-LocalGroupMember -Group "Administrators" -Member "DOMAIN\gmsa01$" |

|  |
| --- |
| Note |
| For domain controller VMs, add the gMSA to the domain Administrators group. |

For guest processing, add the gMSA on the guest OS machine and the guest interaction proxy.

Using gMSA

To run guest processing tasks with the gMSA, do the following:

1. Make sure that the following services run under the LocalSystem account:

* The Veeam Backup Service on the backup server.
* The Veeam Data Mover Service/Veeam Transport Service on the guest interaction proxy.

1. Add the gMSA account type to the Credentials Manager. For more information, see [Group Managed Service Accounts](credentials_manager_gmsa.md).
2. Select the gMSA when specifying guest OS credentials for jobs or policies.

Page updated 1/9/2026

Page content applies to build 13.0.1.1071
