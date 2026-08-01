---
title: "New Features"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new_features_v13.1.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New Features


This section contains information on new features introduced in Veeam PowerShell v13.1.

Backup Infrastructure

Application Backup Repository

In this version, you can run new cmdlets to create and manage application backup repositories and perform recovery from application backup snapshots.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Add-VBRApplicationBackupRepository](add-vbrapplicationbackuprepository.md) | Adds an application backup repository. | | [Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md) | Returns application backup repositories. | | [Set-VBRApplicationBackupRepository](set-vbrapplicationbackuprepository.md) | Modifies application backup repository settings. | | [Remove-VBRApplicationBackupRepository](remove-vbrapplicationbackuprepository.md) | Removes an application backup repository from the backup infrastructure. | | [New-VBRApplicationBackupRepositoryPermission](new-vbrapplicationbackuprepositorypermission.md) | Creates a new permission for hosts to access an application backup repository NFS share. | | [New-VBRApplicationBackupRepositoryScheduleOptions](new-vbrapplicationbackuprepositoryscheduleoptions.md) | Creates a snapshot creation schedule for application backup repositories. | | [New-VBRKerberosPermission](new-vbrkerberospermission.md) | Creates a new permission to access an application backup repository NFS share with Kerberos credentials. | | [Start-VBRApplicationBackupRepositoryRescan](start-vbrapplicationbackuprepositoryrescan.md) | Rescans an application backup repository. | | [Get-VBRApplicationBackupSnapshot](get-vbrapplicationbackupsnapshot.md) | Returns application backup snapshots. | | [New-VBRApplicationBackupSnapshot](new-vbrapplicationbackupsnapshot.md) | Creates a new snapshot of the application backup repository. | | [Start-VBRApplicationBackupSnapshotInstantRecovery](start-vbrapplicationbackupsnapshotinstantrecovery.md) | Starts instant recovery from an application backup snapshot. | | [Start-VBRApplicationBackupSnapshotRecovery](start-vbrapplicationbackupsnapshotrecovery.md) | Starts recovery from an application backup repository snapshot. | | [Start-VBRApplicationBackupCopyInstantRecovery](start-vbrapplicationbackupcopyinstantrecovery.md) | Starts instant recovery of the application backup repository data from a backup copy restore point. | | [Stop-VBRApplicationBackupSnapshotInstantRecovery](stop-vbrapplicationbackupsnapshotinstantrecovery.md) | Stops snapshot instant recovery session for an application backup repository. | |

Backup

Application Backup Policies for InterSystems IRIS

In this version, you can run new cmdlets to create and manage application backup policies for InterSystems IRIS and restore IRIS instances.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Add-VBRIrisBackupJob](add-vbririsbackupjob.md) | Creates InterSystems IRIS application backup policies. | | [Set-VBRIrisBackupJob](set-vbririsbackupjob.md) | Modifies InterSystems IRIS application backup policies. | | [Get-VBRIrisInstanceOriginalPath](get-vbririsinstanceoriginalpath.md) | Returns original paths of InterSystems IRIS instance data in a restore point. | | [New-VBRIrisContainer](new-vbririscontainer.md) | Defines containers of InterSystems IRIS servers for protection groups. | | [New-VBRIrisInstancePathMappingRule](new-vbririsinstancepathmappingrule.md) | Defines path mapping rules for InterSystems IRIS instance restore. | | [New-VBRIrisProcessingOptions](new-vbririsprocessingoptions.md) | Defines processing options for discovered InterSystems IRIS instances. | | [Set-VBRIrisProcessingOptions](set-vbririsprocessingoptions.md) | Modifies processing options for discovered InterSystems IRIS instances. | | [Start-VBRIrisInstanceRestore](start-vbririsinstancerestore.md) | Starts restore of InterSystems IRIS instances. | | [Get-VBRSnapshotBackup](get-vbrsnapshotbackup.md) | Returns InterSystems IRIS snapshot backups. | | [Get-VBRSnapshotRestorePoint](get-vbrsnapshotrestorepoint.md) | Returns restore points of InterSystems IRIS snapshot backups. | |

Backup Infrastructure

NetApp NDMP Storage

In this version, you can run new cmdlets to add and manage NetApp NDMP servers.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Add-VBRNetAppNDMPServer](add-vbrnetappndmpserver.md) | Adds NetApp NDMP servers. | | [Get-VBRNetAppNDMPHostedServer](get-vbrnetappndmphostedserver.md) | Returns NetApp NDMP LIFs. | | [Set-VBRNetAppNDMPServer](set-vbrnetappndmpserver.md) | Modifies a NetApp NDMP server. | |

Backup

Tape — Database Plugin Backups

In this version, you can run a new cmdlet to return restore points of database plugin backups stored on tape.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Get-VBRTapeDbPluginRestorePoint](get-vbrtapedbpluginrestorepoint.md) | Returns restore points of database plugin backups stored on tape. | |

Backup Copy

Storage Backup Copy Job

In this version, you can run new cmdlets to create and manage storage backup copy jobs.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Add-VBRStorageCopyJob](add-vbrstoragecopyjob.md) | Creates storage backup copy jobs. | | [Get-VBRStorageCopyJob](get-vbrstoragecopyjob.md) | Returns storage backup copy jobs. | | [Set-VBRStorageCopyJob](set-vbrstoragecopyjob.md) | Modifies storage backup copy jobs. | | [Enable-VBRStorageCopyJob](enable-vbrstoragecopyjob.md) | Enables storage backup copy jobs. | | [Disable-VBRStorageCopyJob](disable-vbrstoragecopyjob.md) | Disables storage backup copy jobs. | | [Remove-VBRStorageCopyJob](remove-vbrstoragecopyjob.md) | Removes storage backup copy jobs from the backup infrastructure. | | [Start-VBRStorageCopyJob](start-vbrstoragecopyjob.md) | Starts storage backup copy jobs. | |

Data Recovery

Microsoft Active Directory Forest Restore

In this version, you can run new cmdlets to restore a Microsoft Active Directory forest.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Get-VBRADForest](get-vbradforest.md) | Returns Microsoft Active Directory forests in your infrastructure. | | [Get-VBRADForestDomain](get-vbradforestdomain.md) | Returns Active Directory domains within a forest or a restore point. | | [Get-VBRADForestDomainController](get-vbradforestdomaincontroller.md) | Returns domain controllers for an Active Directory domain. | | [Get-VBRADForestDomainRestorePoint](get-vbradforestdomainrestorepoint.md) | Returns restore points for an Active Directory domain. | | [Get-VBRADForestRestorePoint](get-vbradforestrestorepoint.md) | Returns restore points for a Microsoft Active Directory forest. | | [Get-VBRADForestRestoreSession](get-vbradforestrestoresession.md) | Returns Microsoft Active Directory forest restore sessions. | | [New-VBRADForestReIpRule](new-vbradforestreiprule.md) | Creates a re-IP rule for a Microsoft Active Directory forest restore. | | [New-VBRHvADForestDomainRestoreSpec](new-vbrhvadforestdomainrestorespec.md) | Creates a Hyper-V domain restore specification for a Microsoft Active Directory forest restore. | | [New-VBRViADForestDomainRestoreSpec](new-vbrviadforestdomainrestorespec.md) | Creates a VMware domain restore specification for a Microsoft Active Directory forest restore. | | [Start-VBRADForestRestore](start-vbradforestrestore.md) | Starts a Microsoft Active Directory forest restore. | |

Microsoft Entra ID Support

Microsoft Entra ID Tenant Backup

In this version, you can run new cmdlets to export Microsoft Entra ID tenant item data to JSON and start a restore session from a backup copy.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Export-VBREntraIDTenantItemToJson](export-vbrentraidtenantitemtojson.md) | Exports Microsoft Entra ID tenant item properties and metadata in the JSON format. | | [New-VBREntraIDTenantItemExportMapping](new-vbrentraidtenantitemexportmapping.md) | Defines an object with a restore point that you want to use when exporting Microsoft Entra ID item data. | | [Start-VBREntraIDTenantCopyRestore](start-vbrentraidtenantcopyrestore.md) | Starts a restore session from a backup copy of a Microsoft Entra ID tenant. | |

Backup Infrastructure

Veeam Software Appliance — Syslog Event Forwarding

In this version, you can run new cmdlets to configure syslog event forwarding and manage advanced filtering rules for the Veeam Software Appliance.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Export-VBRVSAEventForwardingFilteringRule](export-vbrvsaeventforwardingfilteringrule.md) | Exports Veeam Software Appliance syslog event forwarding filtering rules to a file. | | [Import-VBRVSAEventForwardingFilteringRule](import-vbrvsaeventforwardingfilteringrule.md) | Imports Veeam Software Appliance syslog event forwarding filtering rules from a file. | | [New-VBRVSAEventForwardingFilteringRule](new-vbrvsaeventforwardingfilteringrule.md) | Creates an advanced filtering rule for Veeam Software Appliance syslog event forwarding. | | [Set-VBRVSAEventForwardingFilteringRule](set-vbrvsaeventforwardingfilteringrule.md) | Returns an updated copy of an advanced filtering rule for Veeam Software Appliance syslog event forwarding. | | [Get-VBRVSAEventForwardingOptions](get-vbrvsaeventforwardingoptions.md) | Returns Veeam Software Appliance syslog event forwarding settings. | | [Set-VBRVSAEventForwardingOptions](set-vbrvsaeventforwardingoptions.md) | Modifies Veeam Software Appliance syslog event forwarding settings. | |

Veeam Software Appliance — Node Exporter Metrics

In this version, you can run new cmdlets to manage node exporter metrics for Veeam appliances.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Get-VBRNodeExporterOptions](get-vbrnodeexporteroptions.md) | Returns node exporter metrics for Veeam appliances. | | [Set-VBRNodeExporterOptions](set-vbrnodeexporteroptions.md) | Modifies node exporter metrics for Veeam appliances. | |

Roles and Access Control

In this version, you can run a new cmdlet to return roles configured in Veeam Backup & Replication.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Get-VBRRoleEntity](get-vbrroleentity.md) | Returns roles configured in Veeam Backup & Replication. | |

Veeam Agent Management

Discovered Computer Backup Access

In this version, you can run new cmdlets to allow or revoke a discovered computer's access to a backup.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Attach-VBRDiscoveredComputerBackup](attach-vbrdiscoveredcomputerbackup.md) | Allows a discovered computer to access a backup. | | [Detach-VBRDiscoveredComputerBackup](detach-vbrdiscoveredcomputerbackup.md) | Revokes a discovered computer's access to a backup. | | [Get-VBRDiscoveredComputerBackup](get-vbrdiscoveredcomputerbackup.md) | Returns backups of discovered computers. | |

Discovered Computers

In this version, you can run new cmdlets to uninstall Veeam components from discovered computers and validate Veeam Recovery Media.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Uninstall-VBRDiscoveredComputerComponents](uninstall-vbrdiscoveredcomputercomponents.md) | Uninstalls Veeam components from discovered computers. | | [Validate-VBRDiscoveredComputerRecoveryMedia](validate-vbrdiscoveredcomputerrecoverymedia.md) | Verifies that Veeam Recovery Media is valid. | |

Data Recovery

Unstructured Data — Cold Storage Retrieval

In this version, you can run new cmdlets to retrieve archived object storage data from cold storage and manage active retrieval operations.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Get-VBRUnstructuredBackupRetrieval](get-vbrunstructuredbackupretrieval.md) | Returns active unstructured data retrieval operations. | | [Set-VBRUnstructuredBackupRetrieval](set-vbrunstructuredbackupretrieval.md) | Modifies the availability period of an active unstructured data retrieval operation. | | [New-VBRUnstructuredBackupRetrievalSettings](new-vbrunstructuredbackupretrievalsettings.md) | Defines retrieval policy settings for archive object storage repositories. | |

Malware Detection

Encrypted Data and Unstructured Backup Scans

In this version, you can run new cmdlets to start an analysis of an encrypted data malware event and start an antivirus or YARA scan of file and object storage backups.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Start-VBREncryptionAnalysis](start-vbrencryptionanalysis.md) | Starts an analysis of an encrypted data malware event. | | [Start-VBRScanUnstructuredBackup](start-vbrscanunstructuredbackup.md) | Starts a scan of file backups and object storage backups with antivirus or YARA scan. | |

Backup Infrastructure

High Availability (HA) Cluster

In this version, you can run a new cmdlet to modify settings of an HA cluster.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Set-VBRHighAvailabilityCluster](set-vbrhighavailabilitycluster.md) | Modifies settings of an HA cluster. | |

Backup

VMware vSphere

In this version, you can run a new cmdlet to return VMs available on a vCenter Server.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Get-VBRViVM](get-vbrvivm.md) | Returns VMs available on a vCenter Server. | |

Backup Infrastructure

Azure Backup Appliance

In this version, you can run a new cmdlet to rescan the Azure Backup Appliance template in the backup infrastructure.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Rescan-VBRAzureApplianceTemplate](rescan-vbrazureappliancetemplate.md) | Rescans the Azure Backup Appliance template in the backup infrastructure. | |

Backup

Backup Termination Window

In this version, you can run a new cmdlet to define a schedule with a backup termination window for Unix jobs.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Set-VBRUnixScheduleOptions](set-vbrunixscheduleoptions.md) | Modifies schedule for Unix jobs. | |

Page updated 2026-07-29

