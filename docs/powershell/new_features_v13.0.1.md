---
title: "New Features"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new_features_v13.0.1.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# New Features


This section contains information on new features introduced in Veeam PowerShell v13.0.1.

Deployment

High Availability (HA) Cluster

In this version, you can run new cmdlets to configure and manage an HA cluster.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBRHighAvailabilityClusterNode](new-vbrhighavailabilityclusternode.md) | Defines settings of the secondary node of an HA cluster. | | [Add-VBRHighAvailabilityCluster](add-vbrhighavailabilitycluster.md) | Assembles an HA cluster. | | [Get-VBRHighAvailabilityCluster](get-vbrhighavailabilitycluster.md) | Returns an HA cluster. | | [Remove-VBRHighAvailabilityCluster](remove-vbrhighavailabilitycluster.md) | Disassembles an HA cluster. | | [Start-VBRHighAvailabilityClusterFailover](start-vbrhighavailabilityclusterfailover.md) | Starts failover of an HA cluster. | | [Start-VBRHighAvailabilityClusterSwitchover](start-vbrhighavailabilityclusterswitchover.md) | Starts switchover of an HA cluster. | |

Data Replication

Universal CDP to VMware vSphere

In this version, you can run new cmdlets to create and manage a universal CDP policy.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRUniversalCDPPolicy](add-vbruniversalcdppolicy.md) | Creates a universal CDP policy. | | [Set-VBRUniversalCDPPolicy](set-vbruniversalcdppolicy.md) | Modifies a universal CDP policy. | | [Install-VBRDiscoveredComputerCDPAgent](install-vbrdiscoveredcomputercdpagent.md) | Installs Veeam CDP Guest Service and Veeam CDP volume filter driver. | | [Uninstall-VBRDiscoveredComputerCDPAgent](uninstall-vbrdiscoveredcomputercdpagent.md) | Removes Veeam CDP Guest Service and Veeam CDP volume filter driver. | | [New-VBRUniversalCDPCloudDestination](new-vbruniversalcdpclouddestination.md) | Defines the target location settings for cloud universal CDP policies. | | [New-VBRUniversalCDPvCDCloudDestination](new-vbruniversalcdpvcdclouddestination.md) | Defines the target location settings for VDC universal CDP policies. | | [New-VBRUniversalCDPViDestination](new-vbruniversalcdpvidestination.md) | Defines the target location settings for universal CDP policies. | | [New-VBRUniversalCDPNetworkMappingRule](new-vbruniversalcdpnetworkmappingrule.md) | Defines network mapping rules for universal CDP policies. | | [Get-VBRDiscoveredComputerNetwork](get-vbrdiscoveredcomputernetwork.md) | Returns network adapters of discovered computers from universal CDP protection groups. | |

Veeam Cloud Connect

Backups

In this version, you can run a new cmdlet to remove selected backups of AD tenants and tenants managed by the Service Provider.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Remove-VBRCloudTenantBackup](remove-vbrcloudtenantbackup.md) | Removes selected backups of tenants from disk. | |

Veeam Plug-Ins for Enterprise Applications

Application Backup Policy Settings for Veeam Plug-In for Microsoft SQL Server

In this version, you can run new cmdlets to create and modify the Microsoft SQL Server backup settings for application backup policies.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBRMSSQLOptions](new-vbrmssqloptions.md) | Creates the Microsoft SQL Server backup settings for application backup policies. | | [New-VBRMSSQLProcessingOptions](new-vbrmssqlprocessingoptions.md) | Creates the Microsoft SQL Server database processing settings for application backup policies. | | [Set-VBRMSSQLProcessingOptions](set-vbrmssqlprocessingoptions.md) | Modifies the Microsoft SQL Server database processing settings for application backup policies. | | [New-VBRMSSQLStorageOptions](new-vbrmssqlstorageoptions.md) | Creates the Microsoft SQL Server storage encryption settings for application backup policies. | | [New-VBRMSSQLCredentialsOptions](new-vbrmssqlcredentialsoptions.md) | Creates the Microsoft SQL Server credentials settings for application backup policies. | |


