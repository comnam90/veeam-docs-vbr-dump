---
title: "Veeam PowerShell Licensing"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/licensing.html"
last_updated: "8/22/2025"
product_version: "13.0.1.1071"
---

# Veeam PowerShell Licensing

In this article

On this page, you can check which Veeam cmdlets are available under each of Veeam product edition.

|  |
| --- |
| Important |
| Consider the following:   * Cmdlets that are not available under a license do not show warnings immediately, but may cause your scripts to fail. Check the availability of the cmdlets on this page or in the Applies to section in the cmdlets descriptions. * Neither the [Get-VBRCommand](get-vbrcommand.md) cmdlet nor the [Get-Help](using_get-help.md) cmdlet do not filter the Veeam PowerShell cmdlets by licenses. |

Connecting to Veeam Backup Server

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Connect-VBRServer](connect-vbrserver.md) | ✓ | ✓ | ✓ |
| [Disconnect-VBRServer](disconnect-vbrserver.md) | ✓ | ✓ | ✓ |
| [Get-VBRServerSession](get-vbrserversession.md) | ✓ | ✓ | ✓ |

Backup Infrastructure

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRESX](add-vbresx.md) | ✓ | ✓ | ✓ |
| [Add-VBRESXi](add-vbresxi.md) | ✓ | ✓ | ✓ |
| [Add-VBRHvCluster](add-vbrhvcluster.md) | ✓ | ✓ | ✓ |
| [Add-VBRHvHost](add-vbrhvhost.md) | ✓ | ✓ | ✓ |
| [Add-VBRHvScvmm](add-vbrhvscvmm.md) | ✓ | ✓ | ✓ |
| [Add-VBRLinux](add-vbrlinux.md) | ✓ | ✓ | ✓ |
| [Add-VBRSmbV3Cluster](add-vbrsmbv3cluster.md) | ✓ | ✓ | ✓ |
| [Add-VBRSmbV3Host](add-vbrsmbv3host.md) | ✓ | ✓ | ✓ |
| [Add-VBRvCenter](add-vbrvcenter.md) | ✓ | ✓ | ✓ |
| [Add-VBRWinServer](add-vbrwinserver.md) | ✓ | ✓ | ✓ |
| [Find-VBRHvEntity](find-vbrhventity.md) | ✓ | ✓ | ✓ |
| [Find-VBRViDatastore](find-vbrvidatastore.md) | ✓ | ✓ | ✓ |
| [Find-VBRViDatastoreCluster](find-vbrvidatastorecluster.md) | ✓ | ✓ | ✓ |
| [Find-VBRViEntity](find-vbrvientity.md) | ✓ | ✓ | ✓ |
| [Find-VBRViFolder](find-vbrvifolder.md) | ✓ | ✓ | ✓ |
| [Find-VBRViResourcePool](find-vbrviresourcepool.md) | ✓ | ✓ | ✓ |
| [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) | ✓ | ✓ | ✓ |
| [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) | ✓ | ✓ | ✓ |
| [Get-VBRLocalhost](get-vbrlocalhost.md) | ✓ | ✓ | ✓ |
| [Get-VBRServer](get-vbrserver.md) | ✓ | ✓ | ✓ |
| [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) | ✓ | ✓ | ✓ |
| [Remove-VBRServer](remove-vbrserver.md) | ✓ | ✓ | ✓ |
| [Rescan-VBREntity](rescan-vbrentity.md) | ✓ | ✓ | ✓ |
| [Set-VBRESX](set-vbresx.md) | ✓ | ✓ | ✓ |
| [Set-VBRESXi](set-vbresxi.md) | ✓ | ✓ | ✓ |
| [Set-VBRvCenter](set-vbrvcenter.md) | ✓ | ✓ | ✓ |

Proxy Servers

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRHvProxy](add-vbrhvproxy.md) | ✓ | ✓ | ✓ |
| [Add-VBRViProxy](add-vbrviproxy.md) | ✓ | ✓ | ✓ |
| [Disable-VBRHvProxy](disable-vbrhvproxy.md) | ✓ | ✓ | ✓ |
| [Disable-VBRViProxy](disable-vbrviproxy.md) | ✓ | ✓ | ✓ |
| [Enable-VBRHvProxy](enable-vbrhvproxy.md) | ✓ | ✓ | ✓ |
| [Enable-VBRViProxy](enable-vbrviproxy.md) | ✓ | ✓ | ✓ |
| [Get-VBRHvProxy](get-vbrhvproxy.md) | ✓ | ✓ | ✓ |
| [Get-VBRJobProxy](get-vbrjobproxy.md) | ✓ | ✓ | ✓ |
| [Get-VBRViProxy](get-vbrviproxy.md) | ✓ | ✓ | ✓ |
| [Remove-VBRHvProxy](remove-vbrhvproxy.md) | ✓ | ✓ | ✓ |
| [Remove-VBRViProxy](remove-vbrviproxy.md) | ✓ | ✓ | ✓ |
| [Set-VBRJobProxy](set-vbrjobproxy.md) | ✓ | ✓ | ✓ |
| [Set-VBRViProxy](set-vbrviproxy.md) | ✓ | ✓ | ✓ |

Backup Repositories

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRBackupRepository](add-vbrbackuprepository.md) | ✓ | ✓ | ✓ |
| [Get-VBRBackupRepository](get-vbrbackuprepository.md) | ✓ | ✓ | ✓ |
| [Set-VBRBackupRepository](set-vbrbackuprepository.md) | ✓ | ✓ | ✓ |
| [Remove-VBRBackupRepository](remove-vbrbackuprepository.md) | ✓ | ✓ | ✓ |
| [Sync-VBRBackupRepository](sync-vbrbackuprepository.md) | ✓ | ✓ | ✓ |

Scale-Out Backup Repositories

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRScaleOutBackupRepository](add-vbrscaleoutbackuprepository.md) | ✕ | Limited: 3 extents maximum | ✓ |
| [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md) | ✕ | ✓ | ✓ |
| [Set-VBRRepositoryExtent](set-vbrrepositoryextent.md) | ✕ | ✓ | ✓ |
| [Set-VBRScaleOutBackupRepository](set-vbrscaleoutbackuprepository.md) | ✕ | ✓ | ✓ |
| [Enable-VBRRepositoryExtentMaintenanceMode](enable-vbrrepositoryextentmaintenancemode.md) | ✕ | ✓ | ✓ |
| [Disable-VBRRepositoryExtentMaintenanceMode](disable-vbrrepositoryextentmaintenancemode.md) | ✕ | ✓ | ✓ |
| [Start-VBRRepositoryExtentBackupEvacuation](start-vbrrepositoryextentbackupevacuation.md) | ✕ | ✓ | ✓ |

WAN Accelerators

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRWANAccelerator](add-vbrwanaccelerator.md) | ✕ | ✕ | ✓ |
| [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) | ✕ | ✕ | ✓ |
| [Remove-VBRWANAccelerator](remove-vbrwanaccelerator.md) | ✕ | ✕ | ✓ |
| [Clear-VBRWANCache](clear-vbrwancache.md) | ✕ | ✕ | ✓ |

Backup and Replication Jobs

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRHvBackupJob](add-vbrhvbackupjob.md) | ✓ | ✓ | ✓ |
| [Add-VBRHvBackupJob](add-vbrhvbackupjob.md) | ✓ | ✓ | ✓ |
| [Add-VBRViBackupJob](add-vbrvibackupjob.md) | ✓ | ✓ | ✓ |
| [Add-VBRViBackupJob](add-vbrvibackupjob.md) | ✓ | ✓ | ✓ |
| [Reset-HvVmChangeTracking](reset-hvvmchangetracking.md) | ✓ | ✓ | ✓ |
| [Set-VBRHvReplicaJob](set-vbrhvreplicajob.md) | ✓ | ✓ | ✓ |
| [Set-VBRViReplicaJob](set-vbrvireplicajob.md) | ✓ | ✓ | ✓ |

Replicas

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Get-VBRReplica](get-vbrreplica.md) | ✓ | ✓ | ✓ |
| [Remove-VBRReplica](remove-vbrreplica.md) | ✓ | ✓ | ✓ |

Managing Jobs

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Copy-VBRJob](copy-vbrjob.md) | ✓ | ✓ | ✓ |
| [Disable-VBRJob](disable-vbrjob.md) | ✓ | ✓ | ✓ |
| [Enable-VBRJob](enable-vbrjob.md) | ✓ | ✓ | ✓ |
| [Get-VBRJob](get-vbrjob.md) | ✓ | ✓ | ✓ |
| [Remove-VBRJob](remove-vbrjob.md) | ✓ | ✓ | ✓ |
| [Start-VBRJob](start-vbrjob.md) | ✓ | ✓ | ✓ |
| [Stop-VBRJob](stop-vbrjob.md) | ✓ | ✓ | ✓ |

Objects in Jobs

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRHvJobObject](add-vbrhvjobobject.md) | ✓ | ✓ | ✓ |
| [Add-VBRViJobObject](add-vbrvijobobject.md) | ✓ | ✓ | ✓ |
| [Get-VBRJobObject](get-vbrjobobject.md) | ✓ | ✓ | ✓ |
| [Remove-VBRJobObject](remove-vbrjobobject.md) | ✓ | ✓ | ✓ |

Replica Re-IP Rules

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Get-VBRHvReplicaReIpRule](get-vbrhvreplicareiprule.md) | ✓ | ✓ | ✓ |
| [Get-VBRViReplicaReIpRule](get-vbrvireplicareiprule.md) | ✓ | ✓ | ✓ |
| [New-VBRHvReplicaReIpRule](new-vbrhvreplicareiprule.md) | ✓ | ✓ | ✓ |
| [New-VBRViReplicaReIpRule](new-vbrvireplicareiprule.md) | ✓ | ✓ | ✓ |

Jobs Schedule

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Disable-VBRJobSchedule](disable-vbrjobschedule.md) | ✓ | ✓ | ✓ |
| [Enable-VBRJobSchedule](enable-vbrjobschedule.md) | ✓ | ✓ | ✓ |
| [Get-VBRJobScheduleOptions](get-vbrjobscheduleoptions.md) | ✓ | ✓ | ✓ |
| [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) | ✓ | ✓ | ✓ |
| [New-VBRDailyOptions](new-vbrdailyoptions.md) | ✓ | ✓ | ✓ |
| [New-VBRJobScheduleOptions](new-vbrjobscheduleoptions.md) | ✓ | ✓ | ✓ |
| [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) | ✓ | ✓ | ✓ |
| [Reset-VBRJobScheduleOptions](reset-vbrjobscheduleoptions.md) | ✓ | ✓ | ✓ |
| [Set-VBRBackupWindowOptions](set-vbrbackupwindowoptions.md) | ✓ | ✓ | ✓ |
| [Set-VBRJobSchedule](set-vbrjobschedule.md) | ✓ | ✓ | ✓ |
| [Set-VBRJobScheduleOptions](set-vbrjobscheduleoptions.md) | ✓ | ✓ | ✓ |

Jobs Options

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Get-VBRJobOptions](get-vbrjoboptions.md) | ✓ | ✓ | ✓ |
| [New-VBRJobOptions](new-vbrjoboptions.md) | ✓ | ✓ | ✓ |
| [Reset-VBRJobOptions](reset-vbrjoboptions.md) | ✓ | ✓ | ✓ |
| [Set-VBRJobOptions](set-vbrjoboptions.md) | ✓ | ✓ | ✓ |
| [New-VBRNotificationOptions](new-vbrnotificationoptions.md) | ✓ | ✓ | ✓ |
| [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) | ✓ | ✓ | ✓ |

Application-Aware Processing

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Disable-VBRJobVSSIntegration](disable-vbrjobvssintegration.md) | ✓ | ✓ | ✓ |
| [Enable-VBRJobVSSIntegration](enable-vbrjobvssintegration.md) | ✓ | ✓ | ✓ |
| [Get-VBRJobObjectVssOptions](get-vbrjobobjectvssoptions.md) | ✓ | ✓ | ✓ |
| [Get-VBRJobVSSOptions](get-vbrjobvssoptions.md) | ✓ | ✓ | ✓ |
| [New-VBRJobVssOptions](new-vbrjobvssoptions.md) | ✓ | ✓ | ✓ |
| [Reset-VBRJobVssOptions](reset-vbrjobvssoptions.md) | ✓ | ✓ | ✓ |
| [Set-VBRJobObjectVssOptions](set-vbrjobobjectvssoptions.md) | ✓ | ✓ | ✓ |
| [Set-VBRJobVssOptions](set-vbrjobvssoptions.md) | ✓ | ✓ | ✓ |

Guest File System Indexing

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Disable-VBRJobGuestFSIndexing](disable-vbrjobguestfsindexing.md) | ✓ | ✓ | ✓ |
| [Enable-VBRJobGuestFSIndexing](enable-vbrjobguestfsindexing.md) | ✓ | ✓ | ✓ |

Advanced Job Options

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Set-VBRJobAdvancedBackupOptions](set-vbrjobadvancedbackupoptions.md) | ✓ | ✓ | ✓ |
| [Set-VBRJobAdvancedHvOptions](set-vbrjobadvancedhvoptions.md) | ✓ | ✓ | ✓ |
| [Set-VBRJobAdvancedNotificationOptions](set-vbrjobadvancednotificationoptions.md) | ✓ | ✓ | ✓ |
| [Set-VBRJobAdvancedOptions](set-vbrjobadvancedoptions.md) | ✓ | ✓ | ✓ |
| [Set-VBRJobAdvancedStorageOptions](set-vbrjobadvancedstorageoptions.md) | ✓ | ✓ | ✓ |

Replica Failover

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Start-VBRHvReplicaFailback](start-vbrhvreplicafailback.md) | ✓ | ✓ | ✓ |
| [Start-VBRHvReplicaFailover](start-vbrhvreplicafailover.md) | ✓ | ✓ | ✓ |
| [Start-VBRViReplicaFailback](start-vbrvireplicafailback.md) | ✓ | ✓ | ✓ |
| [Start-VBRViReplicaFailover](start-vbrvireplicafailover.md) | ✓ | ✓ | ✓ |
| [Stop-VBRHvReplicaFailback](stop-vbrhvreplicafailback.md) | ✓ | ✓ | ✓ |
| [Stop-VBRReplicaFailover](stop-vbrreplicafailover.md) | ✓ | ✓ | ✓ |
| [Stop-VBRViReplicaFailback](stop-vbrvireplicafailback.md) | ✓ | ✓ | ✓ |

Failover Plans

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRFailoverPlan](add-vbrfailoverplan.md) | ✕ | ✓ | ✓ |
| [Get-VBRFailoverPlan](get-vbrfailoverplan.md) | ✕ | ✓ | ✓ |
| [New-VBRFailoverPlanObject](new-vbrfailoverplanobject.md) | ✕ | ✓ | ✓ |
| [Remove-VBRFailoverPlan](remove-vbrfailoverplan.md) | ✕ | ✓ | ✓ |
| [Set-VBRFailoverPlan](set-vbrfailoverplan.md) | ✕ | ✓ | ✓ |
| [Set-VBRFailoverPlanObject](set-vbrfailoverplanobject.md) | ✕ | ✓ | ✓ |
| [Start-VBRFailoverPlan](start-vbrfailoverplan.md) | ✕ | ✓ | ✓ |
| [Undo-VBRFailoverPlan](undo-vbrfailoverplan.md) | ✕ | ✓ | ✓ |

Backup Copy Jobs

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBREPBackupCopyJob](add-vbrepbackupcopyjob.md) | ✓ | ✓ | ✓ |
| [Add-VBRHvBackupCopyJob](add-vbrhvbackupcopyjob.md) | ✓ | ✓ | ✓ |
| [Add-VBRvCloudBackupCopyJob](add-vbrvcloudbackupcopyjob.md) | ✓ | ✓ | ✓ |
| [Add-VBRViBackupCopyJob](add-vbrvibackupcopyjob.md) | ✓ | ✓ | ✓ |
| [Sync-VBRBackupCopyJob](sync-vbrbackupcopyjob.md) | ✓ | ✓ | ✓ |

Configuration Backup

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Get-VBRConfigurationBackupJob](get-vbrconfigurationbackupjob.md) | ✓ | ✓ | ✓ |
| [New-VBRConfigurationBackupScheduleOptions](new-vbrconfigurationbackupscheduleoptions.md) | ✓ | ✓ | ✓ |
| [Set-VBRConfigurationBackupJob](set-vbrconfigurationbackupjob.md) | ✓ | ✓ | ✓ |
| [Start-VBRConfigurationBackupJob](start-vbrconfigurationbackupjob.md) | ✓ | ✓ | ✓ |

SureBackup

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VSBHvApplicationGroup](add-vsbhvapplicationgroup.md) | ✕ | ✓ | ✓ |
| [Add-VSBHvJob](add-vsbhvjob.md) | ✕ | ✓ | ✓ |
| [Add-VSBHvVirtualLab](add-vsbhvvirtuallab.md) | ✕ | ✓ | ✓ |
| [Add-VSBJob](add-vsbjob.md) | ✕ | ✓ | ✓ |
| [Add-VSBViApplicationGroup](add-vsbviapplicationgroup.md) | ✕ | ✓ | ✓ |
| [Add-VSBVirtualLab](add-vsbvirtuallab.md) | ✕ | ✓ | ✓ |
| [Connect-VSBHvVirtualLab](connect-vsbhvvirtuallab.md) | ✕ | ✓ | ✓ |
| [Connect-VSBVirtualLab](connect-vsbvirtuallab.md) | ✕ | ✓ | ✓ |
| [Find-VSBHvVirtualLab](find-vsbhvvirtuallab.md) | ✕ | ✓ | ✓ |
| [Find-VSBVirtualLab](find-vsbvirtuallab.md) | ✕ | ✓ | ✓ |
| [Get-VSBApplicationGroup](get-vsbapplicationgroup.md) | ✕ | ✓ | ✓ |
| [Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md) | ✕ | ✓ | ✓ |
| [Get-VSBJob](get-vsbjob.md) | ✕ | ✓ | ✓ |
| [Get-VSBJobOptions](get-vsbjoboptions.md) | ✕ | ✓ | ✓ |
| [Get-VSBJobScheduleOptions](get-vsbjobscheduleoptions.md) | ✕ | ✓ | ✓ |
| [Get-VSBSession](get-vsbsession.md) | ✕ | ✓ | ✓ |
| [Get-VSBTaskSession](get-vsbtasksession.md) | ✕ | ✓ | ✓ |
| [Get-VSBVirtualLab](get-vsbvirtuallab.md) | ✕ | ✓ | ✓ |
| [New-VSBJobOptions](new-vsbjoboptions.md) | ✕ | ✓ | ✓ |
| [Remove-VSBApplicationGroup](remove-vsbapplicationgroup.md) | ✕ | ✓ | ✓ |
| [Remove-VSBHvVirtualLab](remove-vsbhvvirtuallab.md) | ✕ | ✓ | ✓ |
| [Remove-VSBJob](remove-vsbjob.md) | ✕ | ✓ | ✓ |
| [Remove-VSBVirtualLab](remove-vsbvirtuallab.md) | ✕ | ✓ | ✓ |
| [Reset-VSBJobOptions](reset-vsbjoboptions.md) | ✕ | ✓ | ✓ |
| [Set-VSBJobOptions](set-vsbjoboptions.md) | ✕ | ✓ | ✓ |
| [Set-VSBJobSchedule](set-vsbjobschedule.md) | ✕ | ✓ | ✓ |
| [Set-VSBJobScheduleOptions](set-vsbjobscheduleoptions.md) | ✕ | ✓ | ✓ |
| [Start-VSBJob](start-vsbjob.md) | ✕ | ✓ | ✓ |
| [Stop-VSBJob](stop-vsbjob.md) | ✕ | ✓ | ✓ |

Quick Migration

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Start-VBRQuickMigration](start-vbrquickmigration.md) | ✓ | ✓ | ✓ |

VeeamZIP

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Start-VBRZip](start-vbrzip.md) | ✓ | ✓ | ✓ |

Quick Backup

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Start-VBRQuickBackup](start-vbrquickbackup.md) | ✓ | ✓ | ✓ |

VM Copy

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRCopyJob](add-vbrcopyjob.md) | ✓ | ✓ | ✓ |

VM and Guest OS Files Restore

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Get-VBRRestoreSession](get-vbrrestoresession.md) | ✓ | ✓ | ✓ |
| [Remove-VBRRestoreSession](remove-vbrrestoresession.md) | ✓ | ✓ | ✓ |
| [Start-VBRHvRestoreVM](start-vbrhvrestorevm.md) | ✓ | ✓ | ✓ |
| [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) | ✓ | ✓ | ✓ |
| [Start-VBRRestoreVM](start-vbrrestorevm.md) | ✓ | ✓ | ✓ |
| [Start-VBRRestoreVMFiles](start-vbrrestorevmfiles.md) | ✓ | ✓ | ✓ |
| [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) | ✓ | ✓ | ✓ |
| [Start-VBRWindowsGuestItemRestore](start-vbrwindowsguestitemrestore.md) | ✓ | ✓ | ✓ |
| [Stop-VBRLinuxFileRestore](stop-vbrlinuxfilerestore.md) | ✓ | ✓ | ✓ |
| [Stop-VBRWindowsFileRestore](stop-vbrwindowsfilerestore.md) | ✓ | ✓ | ✓ |

Instant Recovery

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) | ✓ | ✓ | ✓ |
| [Restart-VBRInstantRecovery](restart-vbrinstantrecovery.md) | ✓ | ✓ | ✓ |
| [Start-VBRHvInstantRecovery](start-vbrhvinstantrecovery.md) | ✓ | ✓ | ✓ |
| [Start-VBRHvInstantRecoveryMigration](start-vbrhvinstantrecoverymigration.md) | ✓ | ✓ | ✓ |
| [Start-VBRInstantRecovery](start-vbrinstantrecovery.md) | ✓ | ✓ | ✓ |
| [Start-VBRvCloudInstantRecovery](start-vbrvcloudinstantrecovery.md) | ✓ | ✓ | ✓ |
| [Stop-VBRInstantRecovery](stop-vbrinstantrecovery.md) | ✓ | ✓ | ✓ |

Backups

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Export-VBRBackup](export-vbrbackup.md) | ✓ | ✓ | ✓ |
| [Get-VBRBackup](get-vbrbackup.md) | ✓ | ✓ | ✓ |
| [Get-VBRImportedEncryptedBackup](get-vbrencryptedbackup.md) | ✓ | ✓ | ✓ |
| [Get-VBRImportedEncryptedBackupHint](get-vbrencryptedbackuphint.md) | ✓ | ✓ | ✓ |
| [Import-VBRBackup](import-vbrbackup.md) | ✓ | ✓ | ✓ |
| [Remove-VBRBackup](remove-vbrbackup.md) | ✓ | ✓ | ✓ |
| [Remove-VBRRestorePoint](remove-vbrrestorepoint.md) | ✓ | ✓ | ✓ |
| [Set-VBREncryptedBackupPassword](set-vbrencryptedbackuppassword.md) | ✓ | ✓ | ✓ |

Restore Points

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Get-VBRRestorePoint](get-vbrrestorepoint.md) | ✓ | ✓ | ✓ |
| [Get-VBRFilesInRestorePoint](get-vbrfilesinrestorepoint.md) | ✓ | ✓ | ✓ |

Encryption Keys

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBREncryptionKey](add-vbrencryptionkey.md) | ✓ | ✓ | ✓ |
| [Get-VBREncryptionKey](get-vbrencryptionkey.md) | ✓ | ✓ | ✓ |
| [Set-VBREncryptionKey](set-vbrencryptionkey.md) | ✓ | ✓ | ✓ |
| [Remove-VBREncryptionKey](remove-vbrencryptionkey.md) | ✓ | ✓ | ✓ |

Credentials

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRCredentials](add-vbrcredentials.md) | ✓ | ✓ | ✓ |
| [Get-VBRCredentials](get-vbrcredentials.md) | ✓ | ✓ | ✓ |
| [Remove-VBRCredentials](remove-vbrcredentials.md) | ✓ | ✓ | ✓ |
| [Set-VBRCredentials](set-vbrcredentials.md) | ✓ | ✓ | ✓ |

Sessions

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Get-VBRBackupSession](get-vbrbackupsession.md) | ✓ | ✓ | ✓ |
| [Get-VBRSession](get-vbrsession.md) | ✓ | ✓ | ✓ |
| [Get-VBRTaskSession](get-vbrtasksession.md) | ✓ | ✓ | ✓ |
| [Get-VBRRestoreSession](get-vbrrestoresession.md) | ✓ | ✓ | ✓ |
| [Remove-VBRRestoreSession](remove-vbrrestoresession.md) | ✓ | ✓ | ✓ |

SQL Restore

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Get-VBRApplicationRestorePoint](get-vbrapplicationrestorepoint.md) | ✕ | ✓ | ✓ |
| [Get-VBRSQLDatabase](get-vbrsqldatabase.md) | ✕ | ✓ | ✓ |
| [Get-VBRSQLDatabaseRestoreInterval](get-vbrsqldatabaserestoreinterval.md) | ✕ | ✓ | ✓ |
| [Start-VBRSQLDatabaseRestore](start-vbrsqldatabaserestore.md) | ✕ | ✓ | ✓ |

Oracle Restore

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Get-VBROracleDatabase](get-vbroracledatabase.md) | ✕ | ✓ | ✓ |
| [Get-VBROracleDatabaseRestoreInterval](get-vbroracledatabaserestoreinterval.md) | ✕ | ✓ | ✓ |
| [Start-VBROracleDatabaseRestore](start-vbroracledatabaserestore.md) | ✕ | ✓ | ✓ |

Tape Device Support

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRBackupToTapeJob](add-vbrbackuptotapejob.md) | ✕ | ✓ | ✓ |
| [Add-VBRFileToTapeJob](add-vbrfiletotapejob.md) | ✓ | ✓ | ✓ |
| [Add-VBRTapeGFSMediaPool](add-vbrtapegfsmediapool.md) | ✕ | ✓ | ✓ |
| [Add-VBRTapeMediaPool](add-vbrtapemediapool.md) | ✓ | ✓ | ✓ |
| [Add-VBRTapeServer](add-vbrtapeserver.md) | ✓ | ✓ | ✓ |
| [Add-VBRTapeVault](add-vbrtapevault.md) | ✕ | ✓ | ✓ |
| [Disable-VBRTapeDrive](disable-vbrtapedrive.md) | ✓ | ✓ | ✓ |
| [Disable-VBRTapeProtection](disable-vbrtapeprotection.md) | ✓ | ✓ | ✓ |
| [Eject-VBRTapeMedium](eject-vbrtapemedium.md) | ✓ | ✓ | ✓ |
| [Enable-VBRTapeDrive](enable-vbrtapedrive.md) | ✓ | ✓ | ✓ |
| [Enable-VBRTapeProtection](enable-vbrtapeprotection.md) | ✓ | ✓ | ✓ |
| [Erase-VBRTapeMedium](erase-vbrtapemedium.md) | ✓ | ✓ | ✓ |
| [Export-VBRTapeMedium](export-vbrtapemedium.md) | ✓ | ✓ | ✓ |
| [Get-VBRTapeDrive](get-vbrtapedrive.md) | ✓ | ✓ | ✓ |
| [Get-VBRTapeJob](get-vbrtapejob.md) | ✓ | ✓ | ✓ |
| [Get-VBRTapeLibrary](get-vbrtapelibrary.md) | ✓ | ✓ | ✓ |
| [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) | ✓ | ✓ | ✓ |
| [Get-VBRTapeMedium](get-vbrtapemedium.md) | ✓ | ✓ | ✓ |
| [Get-VBRTapeServer](get-vbrtapeserver.md) | ✓ | ✓ | ✓ |
| [Get-VBRTapeVault](get-vbrtapevault.md) | ✕ | ✓ | ✓ |
| [Import-VBRTapeMedium](import-vbrtapemedium.md) | ✓ | ✓ | ✓ |
| [Move-VBRTapeMedium](move-vbrtapemedium.md) | ✓ | ✓ | ✓ |
| [New-VBRBackupToTapeScheduleOptions](new-vbrbackuptotapescheduleoptions.md) | ✓ | ✓ | ✓ |
| [New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md) | ✓ | ✓ | ✓ |
| [New-VBRFileToTapeObject](new-vbrfiletotapeobject.md) | ✓ | ✓ | ✓ |
| [New-VBRFullBackupToTapePolicy](new-vbrfullbackuptotapepolicy.md) | ✓ | ✓ | ✓ |
| [New-VBRTapeGFSMediaSetPolicy](new-vbrtapegfsmediasetpolicy.md) | ✓ | ✓ | ✓ |
| [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md) | ✓ | ✓ | ✓ |
| [New-VBRTapeMediaPoolRetentionPolicy](new-vbrtapemediapoolretentionpolicy.md) | ✓ | ✓ | ✓ |
| [New-VBRTapeMediaSetCreationPolicy](new-vbrtapemediasetcreationpolicy.md) | ✓ | ✓ | ✓ |
| [Remove-VBRTapeLibrary](remove-vbrtapelibrary.md) | ✓ | ✓ | ✓ |
| [Remove-VBRTapeMediaPool](remove-vbrtapemediapool.md) | ✓ | ✓ | ✓ |
| [Remove-VBRTapeMedium](remove-vbrtapemedium.md) | ✓ | ✓ | ✓ |
| [Remove-VBRTapeServer](remove-vbrtapeserver.md) | ✓ | ✓ | ✓ |
| [Remove-VBRTapeVault](remove-vbrtapevault.md) | ✕ | ✓ | ✓ |
| [Set-VBRBackupToTapeJob](set-vbrbackuptotapejob.md) | ✓ | ✓ | ✓ |
| [Set-VBRFileToTapeJob](set-vbrfiletotapejob.md) | ✓ | ✓ | ✓ |
| [Set-VBRTapeGFSMediaPool](set-vbrtapegfsmediapool.md) | ✓ | ✓ | ✓ |
| [Set-VBRTapeGFSScheduleOptions](set-vbrtapegfsscheduleoptions.md) | ✓ | ✓ | ✓ |
| [Set-VBRTapeLibrary](set-vbrtapelibrary.md) | ✓ | ✓ | ✓ |
| [Set-VBRTapeMediaPool](set-vbrtapemediapool.md) | ✓ | ✓ | ✓ |
| [Set-VBRTapeMedium](set-vbrtapemedium.md) | ✓ | ✓ | ✓ |
| [Set-VBRTapeServer](set-vbrtapeserver.md) | ✓ | ✓ | ✓ |
| [Set-VBRTapeVault](set-vbrtapevault.md) | ✕ | ✓ | ✓ |
| [Start-VBRTapeCatalog](start-vbrtapecatalog.md) | ✓ | ✓ | ✓ |
| [Start-VBRTapeInventory](start-vbrtapeinventory.md) | ✓ | ✓ | ✓ |
| [Sync-VBRBackupToTapeJob](sync-vbrbackuptotapejob.md) | ✓ | ✓ | ✓ |

VMware Cloud Director

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRvCloud](add-vbrvcloud.md) | ✓ | ✓ | ✓ |
| [Add-VBRvCloudBackupCopyJob](add-vbrvcloudbackupcopyjob.md) | ✓ | ✓ | ✓ |
| [Add-VBRvCloudJob](add-vbrvcloudjob.md) | ✓ | ✓ | ✓ |
| [Add-VBRvCloudVC](add-vbrvcloudvc.md) | ✓ | ✓ | ✓ |
| [Find-VBRvCloudEntity](find-vbrvcloudentity.md) | ✓ | ✓ | ✓ |
| [New-VBRvCloudVAppRestoreSettings](new-vbrvcloudvapprestoresettings.md) | ✓ | ✓ | ✓ |
| [Remove-VBRServer](remove-vbrserver.md) | ✓ | ✓ | ✓ |
| [Start-VBRvCloudInstantRecovery](start-vbrvcloudinstantrecovery.md) | ✓ | ✓ | ✓ |
| [Start-VBRvCloudRestoreVApp](start-vbrvcloudrestorevapp.md) | ✓ | ✓ | ✓ |
| [Start-VBRvCloudRestoreVm](start-vbrvcloudrestorevm.md) | ✓ | ✓ | ✓ |

Veeam Cloud Connect - Service Provider

Veeam Cloud Connect cmdlets additionally require a Veeam Cloud Provider license.

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRCloudGateway](add-vbrcloudgateway.md) | ✓ | ✓ | ✓ |
| [Add-VBRCloudGatewayCertificate](add-vbrcloudgatewaycertificate.md) | ✓ | ✓ | ✓ |
| [Add-VBRCloudPublicIP](add-vbrcloudpublicip.md) | ✓ | ✓ | ✓ |
| [Add-VBRCloudSubTenant](add-vbrcloudsubtenant.md) | ✓ | ✓ | ✓ |
| [Add-VBRCloudTenant](add-vbrcloudtenant.md) | ✓ | ✓ | ✓ |
| [Add-VBRHvCloudHardwarePlan](add-vbrhvcloudhardwareplan.md) | ✓ | ✓ | ✓ |
| [Disable-VBRCloudGateway](disable-vbrcloudgateway.md) | ✓ | ✓ | ✓ |
| [Disable-VBRCloudSubTenant](disable-vbrcloudsubtenant.md) | ✓ | ✓ | ✓ |
| [Disable-VBRCloudTenant](disable-vbrcloudtenant.md) | ✓ | ✓ | ✓ |
| [Enable-VBRCloudGateway](enable-vbrcloudgateway.md) | ✓ | ✓ | ✓ |
| [Enable-VBRCloudSubTenant](enable-vbrcloudsubtenant.md) | ✓ | ✓ | ✓ |
| [Enable-VBRCloudTenant](enable-vbrcloudtenant.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudGateway](get-vbrcloudgateway.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudGatewayCertificate](get-vbrcloudgatewaycertificate.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudPublicIP](get-vbrcloudpublicip.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudSubTenant](get-vbrcloudsubtenant.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudTenant](get-vbrcloudtenant.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudTenantNetworkAppliance](get-vbrcloudtenantnetworkappliance.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudVLANConfiguration](get-vbrcloudvlanconfiguration.md) | ✓ | ✓ | ✓ |
| [Get-VBRViVirtualSwitch](get-vbrvivirtualswitch.md) | ✓ | ✓ | ✓ |
| [New-VBRCloudSubTenantResource](new-vbrcloudsubtenantresource.md) | ✓ | ✓ | ✓ |
| [New-VBRCloudTenantHwPlanOptions](new-vbrcloudtenanthwplanoptions.md) | ✓ | ✓ | ✓ |
| [New-VBRCloudTenantReplicationResources](new-vbrcloudtenantreplicationresources.md) | ✓ | ✓ | ✓ |
| [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) | ✓ | ✓ | ✓ |
| [New-VBRCloudVLANConfiguration](new-vbrcloudvlanconfiguration.md) | ✓ | ✓ | ✓ |
| [New-VBRHvCloudHWPlanDatastore](new-vbrhvcloudhwplandatastore.md) | ✓ | ✓ | ✓ |
| [Remove-VBRCloudGateway](remove-vbrcloudgateway.md) | ✓ | ✓ | ✓ |
| [Remove-VBRCloudHardwarePlan](remove-vbrcloudhardwareplan.md) | ✓ | ✓ | ✓ |
| [Remove-VBRCloudPublicIP](remove-vbrcloudpublicip.md) | ✓ | ✓ | ✓ |
| [Remove-VBRCloudSubTenant](remove-vbrcloudsubtenant.md) | ✓ | ✓ | ✓ |
| [Remove-VBRCloudTenant](remove-vbrcloudtenant.md) | ✓ | ✓ | ✓ |
| [Remove-VBRCloudVLANConfiguration](remove-vbrcloudvlanconfiguration.md) | ✓ | ✓ | ✓ |
| [Reset-VBRCloudTenant](reset-vbrcloudtenant.md) | ✓ | ✓ | ✓ |
| [Set-VBRCloudGateway](set-vbrcloudgateway.md) | ✓ | ✓ | ✓ |
| [Set-VBRCloudSubTenant](set-vbrcloudsubtenant.md) | ✓ | ✓ | ✓ |
| [Set-VBRCloudSubTenantResource](set-vbrcloudsubtenantresource.md) | ✓ | ✓ | ✓ |
| [Set-VBRCloudTenant](set-vbrcloudtenant.md) | ✓ | ✓ | ✓ |
| [Set-VBRCloudTenantNetworkAppliance](set-vbrcloudtenantnetworkappliance.md) | ✓ | ✓ | ✓ |
| [Set-VBRCloudTenantResource](set-vbrcloudtenantresource.md) | ✓ | ✓ | ✓ |
| [Set-VBRCloudVLANConfiguration](set-vbrcloudvlanconfiguration.md) | ✓ | ✓ | ✓ |
| [Set-VBRHvCloudHardwarePlan](set-vbrhvcloudhardwareplan.md) | ✓ | ✓ | ✓ |
| [Set-VBRHvCloudHWPlanDatastore](set-vbrhvcloudhwplandatastore.md) | ✓ | ✓ | ✓ |
| [Enable-VBRCloudMaintenanceMode](enable-vbrcloudmaintenancemode.md) | ✓ | ✓ | ✓ |
| [Disable-VBRCloudMaintenanceMode](disable-vbrcloudmaintenancemode.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudInfrastructureState](get-vbrcloudinfrastructurestate.md) | ✓ | ✓ | ✓ |

Veeam Cloud Connect - Cloud User

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRCloudProvider](add-vbrcloudprovider.md) | ✓ | ✓ | ✓ |
| [Add-VBRCloudSubUser](add-vbrcloudsubuser.md) | ✓ | ✓ | ✓ |
| [Add-VBRHvCloudReplicaJob](add-vbrhvcloudreplicajob.md) | ✓ | ✓ | ✓ |
| [Add-VBRViCloudReplicaJob](add-vbrvicloudreplicajob.md) | ✓ | ✓ | ✓ |
| [Disable-VBRCloudSubUser](disable-vbrcloudsubuser.md) | ✓ | ✓ | ✓ |
| [Enable-VBRCloudSubUser](enable-vbrcloudsubuser.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudDatastore](get-vbrclouddatastore.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudProvider](get-vbrcloudprovider.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudProviderNetworkAppliance](get-vbrcloudprovidernetworkappliance.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudServer](get-vbrcloudserver.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudServerNetworkInfo](get-vbrcloudservernetworkinfo.md) | ✓ | ✓ | ✓ |
| [Get-VBRCloudSubUser](get-vbrcloudsubuser.md) | ✓ | ✓ | ✓ |
| [Get-VBRDefaultGatewayConfiguration](get-vbrdefaultgatewayconfiguration.md) | ✓ | ✓ | ✓ |
| [New-VBRCloudFailoverPlanObject](new-vbrcloudfailoverplanobject.md) | ✓ | ✓ | ✓ |
| [New-VBRCloudProviderNetworkAppliance](new-vbrcloudprovidernetworkappliance.md) | ✓ | ✓ | ✓ |
| [New-VBRCloudSubUserResource](new-vbrcloudsubuserresource.md) | ✓ | ✓ | ✓ |
| [New-VBRFailoverPlanPublicIPRule](new-vbrfailoverplanpubliciprule.md) | ✓ | ✓ | ✓ |
| [Remove-VBRCloudProvider](remove-vbrcloudprovider.md) | ✓ | ✓ | ✓ |
| [Remove-VBRCloudSubUser](remove-vbrcloudsubuser.md) | ✓ | ✓ | ✓ |
| [Remove-VBRDefaultGateway](remove-vbrdefaultgateway.md) | ✓ | ✓ | ✓ |
| [Set-VBRCloudFailoverPlanObject](set-vbrcloudfailoverplanobject.md) | ✓ | ✓ | ✓ |
| [Set-VBRCloudProvider](set-vbrcloudprovider.md) | ✓ | ✓ | ✓ |
| [Set-VBRCloudProviderNetworkAppliance](set-vbrcloudprovidernetworkappliance.md) | ✓ | ✓ | ✓ |
| [Set-VBRCloudSubUser](set-vbrcloudsubuser.md) | ✓ | ✓ | ✓ |
| [Set-VBRCloudSubUserResource](set-vbrcloudsubuserresource.md) | ✓ | ✓ | ✓ |
| [Set-VBRDefaultGateway](set-vbrdefaultgateway.md) | ✓ | ✓ | ✓ |
| [Set-VBRDefaultGatewayConfiguration](set-vbrdefaultgatewayconfiguration.md) | ✓ | ✓ | ✓ |
| [Set-VBRHvCloudReplicaJob](set-vbrhvcloudreplicajob.md) | ✓ | ✓ | ✓ |
| [Set-VBRViCloudReplicaJob](set-vbrvicloudreplicajob.md) | ✓ | ✓ | ✓ |

Direct Restore to Microsoft Azure

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBRAzureAccount](add-vbrazureaccount.md) | ✓ | ✓ | ✓ |
| [Deploy-VBRAzureLinuxRestoreAppliance](deploy-vbrazurelinuxrestoreappliance.md) | ✓ | ✓ | ✓ |
| [Get-VBRAzureAccount](get-vbrazureaccount.md) | ✓ | ✓ | ✓ |
| [Get-VBRAzureCloudService](get-vbrazurecloudservice.md) | ✓ | ✓ | ✓ |
| [Get-VBRAzureLinuxRestoreAppliance](get-vbrazurelinuxrestoreappliance.md) | ✓ | ✓ | ✓ |
| [Get-VBRAzureLocation](get-vbrazurelocation.md) | ✓ | ✓ | ✓ |
| [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) | ✓ | ✓ | ✓ |
| [Get-VBRAzureRestoreSession](get-vbrazurerestoresession.md) | ✓ | ✓ | ✓ |
| [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md) | ✓ | ✓ | ✓ |
| [Get-VBRAzureSubscription](get-vbrazuresubscription.md) | ✓ | ✓ | ✓ |
| [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) | ✓ | ✓ | ✓ |
| [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) | ✓ | ✓ | ✓ |
| [Get-VBRAzureVMSize](get-vbrazurevmsize.md) | ✓ | ✓ | ✓ |
| [New-VBRAzureLinuxRestoreAppliance](new-vbrazurelinuxrestoreappliance.md) | ✓ | ✓ | ✓ |
| [Remove-VBRAzureAccount](remove-vbrazureaccount.md) | ✓ | ✓ | ✓ |
| [Set-VBRAzureAccount](set-vbrazureaccount.md) | ✓ | ✓ | ✓ |
| [Set-VBRAzureLinuxRestoreAppliance](set-vbrazurelinuxrestoreappliance.md) | ✓ | ✓ | ✓ |
| [Start-VBRVMRestoreToAzure](start-vbrvmrestoretoazure.md) | ✓ | ✓ | ✓ |
| [Stop-VBRVMRestoreToAzure](stop-vbrvmrestoretoazure.md) | ✓ | ✓ | ✓ |

Veeam Agent for Microsoft Windows

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VBREPBackupCopyJob](add-vbrepbackupcopyjob.md) | ✓ | ✓ | ✓ |
| [Disable-VBREPJob](disable-vbrepjob.md) | ✓ | ✓ | ✓ |
| [Enable-VBREPJob](enable-vbrepjob.md) | ✓ | ✓ | ✓ |
| [Get-VBREPJob](get-vbrepjob.md) | ✓ | ✓ | ✓ |
| [Get-VBREPPermission](get-vbreppermission.md) | ✓ | ✓ | ✓ |
| [Get-VBREPSession](get-vbrepsession.md) | ✓ | ✓ | ✓ |
| [Set-VBREPPermission](set-vbreppermission.md) | ✓ | ✓ | ✓ |
| [Start-VBREpInstantRecovery](start-vbrepinstantrecovery.md) | ✓ | ✓ | ✓ |
| [Start-VBRRestoreVirtualDisks](start-vbrrestorevirtualdisks.md) | ✓ | ✓ | ✓ |

NetApp Storage Systems

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-NetAppHost](add-netapphost.md) | ✓ | ✓ | ✓ |
| [Add-NetAppSnapshot](add-netappsnapshot.md) | ✓ | ✓ | ✓ |
| [Get-NetAppHost](get-netapphost.md) | ✓ | ✓ | ✓ |
| [Get-NetAppSnapshot](get-netappsnapshot.md) | ✓ | ✓ | ✓ |
| [Get-NetAppVolume](get-netappvolume.md) | ✓ | ✓ | ✓ |
| [New-VBRStorageProtocolPolicy](new-vbrstorageprotocolpolicy.md) | ✓ | ✓ | ✓ |
| [Remove-NetAppHost](remove-netapphost.md) | ✓ | ✓ | ✓ |
| [Remove-NetAppSnapshot](remove-netappsnapshot.md) | ✓ | ✓ | ✓ |
| [Set-NetAppHost](set-netapphost.md) | ✓ | ✓ | ✓ |
| [Sync-NetAppHost](sync-netapphost.md) | ✓ | ✓ | ✓ |
| [Sync-NetAppVolume](sync-netappvolume.md) | ✓ | ✓ | ✓ |

HPE 3PAR StoreServ Storage Systems

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-HP3Snapshot](add-hp3snapshot.md) | ✓ | ✓ | ✓ |
| [Add-HP3Storage](add-hp3storage.md) | ✓ | ✓ | ✓ |
| [Get-HP3Snapshot](get-hp3snapshot.md) | ✓ | ✓ | ✓ |
| [Get-HP3Storage](get-hp3storage.md) | ✓ | ✓ | ✓ |
| [Get-HP3Volume](get-hp3volume.md) | ✓ | ✓ | ✓ |
| [Remove-HP3Snapshot](remove-hp3snapshot.md) | ✓ | ✓ | ✓ |
| [Remove-HP3Storage](remove-hp3storage.md) | ✓ | ✓ | ✓ |
| [Set-HP3Storage](set-hp3storage.md) | ✓ | ✓ | ✓ |
| [Sync-HP3Storage](sync-hp3storage.md) | ✓ | ✓ | ✓ |
| [Sync-HP3Volume](sync-hp3volume.md) | ✓ | ✓ | ✓ |

Dell VNX Storage Systems

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-VNXHost](add-vnxhost.md) | ✓ | ✓ | ✓ |
| [Add-VNXSnapshot](add-vnxsnapshot.md) | ✓ | ✓ | ✓ |
| [Get-VNXHost](get-vnxhost.md) | ✓ | ✓ | ✓ |
| [Get-VNXSnapshot](get-vnxsnapshot.md) | ✓ | ✓ | ✓ |
| [Get-VNXVolume](get-vnxvolume.md) | ✓ | ✓ | ✓ |
| [Remove-VNXHost](remove-vnxhost.md) | ✓ | ✓ | ✓ |
| [Remove-VNXSnapshot](remove-vnxsnapshot.md) | ✓ | ✓ | ✓ |
| [Set-VNXHost](set-vnxhost.md) | ✓ | ✓ | ✓ |
| [Sync-VNXHost](sync-vnxhost.md) | ✓ | ✓ | ✓ |
| [Sync-VNXVolume](sync-vnxvolume.md) | ✓ | ✓ | ✓ |

HPE Nimble Storage Systems

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Add-NimbleHost](add-nimblehost.md) | ✓ | ✓ | ✓ |
| [Add-NimbleSnapshot](add-nimblesnapshot.md) | ✓ | ✓ | ✓ |
| [Get-NimbleHost](get-nimblehost.md) | ✓ | ✓ | ✓ |
| [Get-NimbleSnapshot](get-nimblesnapshot.md) | ✓ | ✓ | ✓ |
| [Get-NimbleVolume](get-nimblevolume.md) | ✓ | ✓ | ✓ |
| [Remove-NimbleHost](remove-nimblehost.md) | ✓ | ✓ | ✓ |
| [Remove-NimbleSnapshot](remove-nimblesnapshot.md) | ✓ | ✓ | ✓ |
| [Set-NimbleHost](set-nimblehost.md) | ✓ | ✓ | ✓ |
| [Sync-NimbleHost](sync-nimblehost.md) | ✓ | ✓ | ✓ |
| [Sync-NimbleVolume](sync-nimblevolume.md) | ✓ | ✓ | ✓ |

Universal Storage API Integrated Systems

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Get-VBRStoragePlugin](get-vbrstorageplugin.md) | ✓ | ✓ | ✓ |
| [Get-StoragePluginHost](get-storagepluginhost.md) | ✓ | ✓ | ✓ |
| [Add-StoragePluginHost](add-storagepluginhost.md) | ✓ | ✓ | ✓ |
| [Set-StoragePluginHost](set-storagepluginhost.md) | ✓ | ✓ | ✓ |
| [Sync-StoragePluginHost](sync-storagepluginhost.md) | ✓ | ✓ | ✓ |
| [Remove-StoragePluginHost](remove-storagepluginhost.md) | ✓ | ✓ | ✓ |
| [Get-StoragePluginVolume](get-storagepluginvolume.md) | ✓ | ✓ | ✓ |
| [Sync-StoragePluginVolume](sync-storagepluginvolume.md) | ✓ | ✓ | ✓ |
| [Add-StoragePluginSnapshot](add-storagepluginsnapshot.md) | ✓ | ✓ | ✓ |
| [Get-StoragePluginSnapshot](get-storagepluginsnapshot.md) | ✓ | ✓ | ✓ |
| [Remove-StoragePluginSnapshot](remove-storagepluginsnapshot.md) | ✓ | ✓ | ✓ |

Logs Export

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Export-VBRLogs](export-vbrlogs.md) | ✓ | ✓ | ✓ |

Veeam PowerShell Help

| Cmdlet | Standard Edition | Enterprise Edition | Enterprise Plus Edition |
| --- | --- | --- | --- |
| [Get-VBRCommand](get-vbrcommand.md) | ✓ | ✓ | ✓ |
| [Get-VBRToolkitDocumentation](get-vbrtoolkitdocumentation.md) | ✓ | ✓ | ✓ |

Page updated 8/22/2025

Page content applies to build 13.0.1.1071
