---
title: "New Features"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new_features_v13.html"
last_updated: "9/8/2025"
product_version: "13.0.1.1071"
---

# New Features

In this article

This section contains information on new features introduced in Veeam PowerShell v13.

Backup Infrastructure

Virtualization Servers and Hosts

In this version, you can get information about Linux components installed on the backup server.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VBRLinuxPackage](get-vbrlinuxpackage.md) | Returns information about Linux components installed on the backup server. | | [Uninstall-VBRServerComponent](uninstall-vbrservercomponent.md) | Removes a  backup infrastructure component from the backup infrastructure. | |

Mount Server Settings

In this version, you can run new cmdlets to perform operations with Windows and Linux mount servers.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VBRDefaultLinuxMountServer](get-vbrdefaultlinuxmountserver.md) | Returns the default Linux mount server. | | [Get-VBRDefaultWindowsMountServer](get-vbrdefaultwindowsmountserver.md) | Returns the default Windows mount server. | | [Set-VBRDefaultLinuxMountServer](set-vbrdefaultlinuxmountserver.md) | Modifies the default Linux mount server. | | [Set-VBRDefaultWindowsMountServer](set-vbrdefaultwindowsmountserver.md) | Modifies the default Microsoft Windows mount server. | | [Get-VBRRepositoryMountServerOptions](get-vbrrepositorymountserveroptions.md) | Returns settings of a mount server associated with a backup repository. | |

Object Storage Repositories

In this version, you can run new cmdlets to add an IBM Cloud object storage repository to the backup infrastructure.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRIBMCloudRepository](add-vbribmcloudrepository.md) | Adds the IBM Cloud object storage repository to the backup infrastructure. | | [Set-VBRIBMCloudRepository](set-vbribmcloudrepository.md) | Modifies the IBM Cloud object storage repository to the backup infrastructure. | |

Managing Security Settings

Security and Compliance Analyzer

In this version, you can run new cmdlets to start Security and Compliance Analyzer scans and view the results.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Start-VBRSecurityComplianceAnalyzer](start-vbrsecuritycomplianceanalyzer.md) | Starts the Security & Compliance Analyzer scan. | | [Get-VBRSecurityComplianceAnalyzerResults](get-vbrsecuritycomplianceanalyzerresults.md) | Returns Security & Compliance Analyzer scan results. | |

Veeam Software Appliance

Veeam Updater

In this version, you can run new cmdlets to configure Veeam Updater for Veeam Software Appliances.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VBRAvailableUpdates](get-vbravailableupdates.md) | Returns available software updates. | | [Install-VBRAvailableUpdates](install-vbravailableupdates.md) | Installs available software updates. | | [Get-VBRGeneralUpdateOptions](get-vbrgeneralupdateoptions.md) | Returns general update settings. | | [Get-VBRInternetProxyUpdateOptions](get-vbrinternetproxyupdateoptions.md) | Returns internet proxy settings. | | [New-VBRMaintenanceWindowOptions](new-vbrmaintenancewindowoptions.md) | Configures a maintenance window for automatic update installation. | | [Set-VBRGeneralUpdateOptions](set-vbrgeneralupdateoptions.md) | Modifies general update settings. | | [Set-VBRInternetProxyUpdateOptions](set-vbrinternetproxyupdateoptions.md) | Modifies internet proxy settings. | |

Data Recovery

Instant Recovery to Microsoft Azure

In this version, you can run new cmdlets to instantly recover workloads to Microsoft Azure.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBRAzureApplianceTemplateDeploymentOptions](new-vbrazureappliancetemplatedeploymentoptions.md) | Defines deployment options for a helper appliance template. | | [Get-VBRAzureApplianceTemplate](get-vbrazureappliancetemplate.md) | Returns deployed helper appliance templates. | | [Deploy-VBRAzureApplianceTemplate](deploy-vbrazureappliancetemplate.md) | Deploys a helper appliance template. | | [Remove-VBRAzureApplianceTemplate](remove-vbrazureappliancetemplate.md) | Removes deployed helper appliance templates. | | [Start-VBRAzureInstantRecovery](start-vbrazureinstantrecovery.md) | Starts Instant Recovery to Microsoft Azure. | | [Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md) | Returns an array of objects on the Instant Recovery to Microsoft Azure operation. | | [Get-VBRAzureInstantRecoverySession](get-vbrazureinstantrecoverysession.md) | Returns session logs for the Instant Recovery to Microsoft Azure operation. | | [New-VBRAzureInstantRecoverySwitchingOptions](new-vbrazureinstantrecoveryswitchingoptions.md) | Defines the switchover options. | | [Get-VBRAzureInstantRecoverySwitchingOptions](get-vbrazureinstantrecoveryswitchingoptions.md) | Returns the switchover options. | | [Set-VBRAzureInstantRecoverySwitchingOptions](set-vbrazureinstantrecoveryswitchingoptions.md) | Sets the switchover options for an Instant Recovery operation. | | [Start-VBRAzureInstantRecoveryMigration](start-vbrazureinstantrecoverymigration.md) | Starts migration to production for the specified Instant Recovery to Microsoft Azure operation. | | [Switch-VBRAzureInstantRecoveryMigration](switch-vbrazureinstantrecoverymigration.md) | Starts the manual switchover for finalizing the migration to production process after you perform the Instant Recovery to Microsoft Azure. | | [Stop-VBRAzureInstantRecovery](stop-vbrazureinstantrecovery.md) | Stops the specified Instant Recovery to Microsoft Azure operation. | |

Restore to Amazon EC2

In this version, you can define settings of a private IP address for Amazon EC2 instances.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBRAmazonIpAddress](new-vbramazonipaddress.md) | Defines settings of a private IP address for Amazon EC2 instances. | |

Microsoft EntraID Support

In this version, you can run new cmdlets to work with a Microsoft Entra ID infrastructure and jobs.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBREntraIDTenantProtectedScope](new-vbrentraidtenantprotectedscope.md) | Specifies the tenant protection scope. | | [New-VBREntraIDBackupSecondaryTarget](new-vbrentraidbackupsecondarytarget.md) | Defines secondary repository settings. | | [Set-VBREntraIDBackupSecondaryTarget](set-vbrentraidbackupsecondarytarget.md) | Modifies secondary repository settings. | | [Add-VBREntraIDTenantBackupJob](add-vbrentraidtenantbackupjob.md) | Creates a Microsoft Entra ID tenant backup job. | | [Set-VBREntraIDTenantBackupJob](set-vbrentraidtenantbackupjob.md) | Modifies a backup job that protects a Microsoft Entra ID tenant. | |

Veeam Plug-Ins for Enterprise Applications

In this version, you can run new cmdlets to work with operations log (oplog) processing options for MongoDB replica sets.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBRMongoDBOplogProcessingOptions](new-vbrmongodboplogprocessingoptions.md) | Enables operations log (oplog) processing options for MongoDB replica sets. | | [Set-VBRMongoDBOplogProcessingOptions](set-vbrmongodboplogprocessingoptions.md) | Modifies operations log (oplog) processing options for MongoDB replica sets. | |

Tape Devices

In this version, you can run new cmdlets to file to tape jobs and object to tape jobs.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Sync-VBRFileToTapeJob](sync-vbrfiletotapejob.md) | Starts an active full for a selected GFS file to tape job. | | [Sync-VBRObjectToTapeJob](sync-vbrobjecttotapejob.md) | Starts an active full for a selected GFS object to tape job. | |

Veeam Plug-Ins for Enterprise Applications

In this version, you can create SAP HANA storage encryption settings for application backup policies.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBRSAPHANAStorageOptions](new-vbrsaphanastorageoptions.md) | Creates the SAP HANA storage encryption settings for application backup policies. | |

Page updated 9/8/2025

Page content applies to build 13.0.1.1071
