---
title: "Veeam PowerShell Enumerations"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enums.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Veeam PowerShell Enumerations


In this section you can find enumerations used by Veeam PowerShell.

EVmssState

Mount state.

| Member | Description |
| --- | --- |
| 0 | Mounting |
| 1 | Mounted |
| 2 | Mount Failed |
| 3 | Unmounting |
| 4 | Unmount Failed |
| 5 | Unmounted |

EVBRHighAvailablityClusterNodeStatus

The role of the high availability cluster node.

| Member | Description |
| --- | --- |
| Primary | Primary node. |
| Secondary | Secondary node. |

EVBRHighAvailabilityClusterNodeRole

The status of the high availability cluster node.

| Member | Description |
| --- | --- |
| Online | Node is online. |
| Offline | Node is offline. |

VBRAmazonIpAddressType

Type of a private IP address for an Amazon EC2 instance.

| Member | Description |
| --- | --- |
| Dynamic | Private dynamic IP address. |
| Static | Private static IP address. |

VBRAmazonRegionType

Type of Amazon region.

| Member | Description |
| --- | --- |
| Global | Global region. |
| Government | Government region. |
| China | China region. |

VBRAmazonServiceType

Type of Amazon object storage.

| Member | Description |
| --- | --- |
| ExternalRepository | External repository. |
| CapacityTier | Capacity tier, object storage repository. |
| ArchiveTier | Archive tier |

VBRArchiveExtentStatus

Status of archive extent.

| Member | Description |
| --- | --- |
| 0 | Normal |
| 1 | Pending |
| 2 | Maintenance |
| 8 | Sealed |

VBRArchiveObjectStorageRepositoryType

| Member | Description |
| --- | --- |
| AzureArchive | Microsoft Azure Archive Storage. |
| AmazonS3Glacier | Amazon S3 Glacier Storage |
| S3GlacierCompatible | S3 compatible Glacier Storage |

VBRActivitySeverity

Malware states.

| Member | Description |
| --- | --- |
| Clean | Clean |
| Suspicious | Suspicious |
| Infected | Infected |

VBRActivityState

Malware status.

| Member | Description |
| --- | --- |
| Created | Clean |
| FalsePositive | False positive event |

VBRApplicationBackupAuthenticationMode

Types of authentication methods to access Oracle hosts and databases.

| Member | Description |
| --- | --- |
| OSAuth | Connection to the Oracle host and database with OS authentication. |
| SplitAuth | Uses OS and database credentials simultaneously to connect to the Oracle host and database. |

VBRAzureBlobRegionType

Type of Azure regions.

| Member | Description |
| --- | --- |
| Global | Global region |
| China | China region |
| Government | Government region |

VBRAzureDiskType

Azure disk type.

| Member | Description |
| --- | --- |
| StandardHDD | Standard HDD |
| StandardSSD | Standard SSD |
| PremiumSSD | Premium SSD |

VBRAzureModelType

Microsoft Azure subscription type.

| Member | Description |
| --- | --- |
| ResourceManager | Microsoft Azure Resource Manager subscription type |
| Classic | Microsoft Azure Classic subscription type |

VBRAzureServiceType

| Member | Description |
| --- | --- |
| ExternalRepository | External repository |
| CapacityTier | Capacity tier, object storage repository |
| ArchiveTier | Archive tier |

VBRAgentLicenseMode

Agent license mode.

| Member | Description |
| --- | --- |
| Workstation | Workstation mode |
| Server | Server mode |

VBRBackupToTapePolicyType

Job schedule settings.

| Member | Description |
| --- | --- |
| AfterJob | Job starts after a selected job. |
| AfterNewBackup | Job starts when a new backup appear. |
| Daily | Job starts on selected days of week. |
| Monthly | Job starts on selected days of month. |

VBRBestPracticeStatus

Status of Security and Compliance Analyzer check.

| Member | Description |
| --- | --- |
| None | The check not applicable. |
| Analyzing | The check is not finished. |
| Ok | The check passed. |
| Violation | The check failed. |
| Suppressed | The check is disabled. |
| UnableToCheck | The check cannot be performed. |

VBRBestPracticeType

Type of Security and Compliance Analyzer check.

| Member | Description |
| --- | --- |
| BackupServerInProductionDomain | The backup server should be in a workgroup. |
| VbrAndEmOnDifferentMachines | Not used. |
| BiosUEFIMode | Not used. |
| SecureBootEnable | Not used. |
| SMBSigningEnabled | If SMB shares are used in the backup infrastructure, SMB signing and encryption should be enabled to prevent NTLMv2 relay attacks. For more information, see these Microsoft articles: [Configure SMB Signing with Confidence](https://techcommunity.microsoft.com/t5/storage-at-microsoft/configure-smb-signing-with-confidence/ba-p/2418102), [SMB security enhancements](https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-security). |
| WDigestNotStorePasswordsInMemory | WDigest credentials caching stores cleartext credentials in Windows RAM. To reduce the risk of credential dumping attacks, the setting should be disabled with a registry value. For more information, see [this Microsoft article](https://support.microsoft.com/en-us/topic/microsoft-security-advisory-update-to-improve-credentials-protection-and-management-may-13-2014-93434251-04ac-b7f3-52aa-9f951c14b649). |
| WebProxyAutoDiscoveryDisabled | The Web Proxy Auto-Discovery (WPAD) protocol provides automatic discovery of web proxy configuration. If this feature is not used in the backup infrastructure, the WinHTTP Web Proxy Auto-Discovery Service should be disabled to prevent man-in-the-middle (MITM) attacks. |
| TLS1Disabled | TLS 1.0 should be disabled if it is not needed. For more information, see [NIST guidelines](https://csrc.nist.gov/pubs/sp/800/52/r2/final). |
| TLS1\_1Disabled | TLS 1.1 should be disabled if it is not needed. For more information, see [NIST guidelines](https://csrc.nist.gov/pubs/sp/800/52/r2/final). |
| SSLv2Disabled | SSL 2.0 should be disabled as it has well-known security vulnerabilities and is not NIST-approved. For more information, see [NIST guidelines](https://csrc.nist.gov/pubs/sp/800/52/r2/final). |
| SSLv3Disabled | SSL 3.0 should be disabled as it has well-known security vulnerabilities and is not NIST-approved. For more information, see [NIST guidelines](https://csrc.nist.gov/pubs/sp/800/52/r2/final). |
| WindowsScriptHostDisabled | Windows Script Host should be disabled to prevent script-based malware attacks. |
| SMB1ProtocolDisabled | Outdated network protocol SMB 1.0 should be disabled as it has a number of serious security vulnerabilities including remote code execution. For more information, see [this Microsoft article](https://techcommunity.microsoft.com/blog/filecab/stop-using-smb1/425858). |
| LLMNRDisabled | Outdated broadcast protocol Link-Local Multicast Name Resolution (LLMNR) should be disabled to prevent spoofing and man-in-the-middle (MITM) attacks. |
| SMBEncryptionEnabled | If SMB shares are used in the backup infrastructure, SMB signing and encryption should be enabled to prevent NTLMv2 relay attacks. For more information, see these Microsoft articles: [Configure SMB Signing with Confidence](https://techcommunity.microsoft.com/t5/storage-at-microsoft/configure-smb-signing-with-confidence/ba-p/2418102), [SMB security enhancements](https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-security). |
| OutdatedSslAndTlsDisabled | Outdated network protocols SSL 2.0 and 3.0 should be disabled as they have well-known security vulnerabilities and are not NIST-approved. Also, TLS 1.0 and 1.1 should be disabled if they are not needed. For more information, see [NIST guidelines](https://csrc.nist.gov/pubs/sp/800/52/r2/final). |
| CSmbSigningAndEncryptionEnabled | If SMB shares are used in the backup infrastructure, SMB signing and encryption should be enabled to prevent NTLMv2 relay attacks. For more information, see these Microsoft articles: [Configure SMB Signing with Confidence](https://techcommunity.microsoft.com/t5/storage-at-microsoft/configure-smb-signing-with-confidence/ba-p/2418102), [SMB security enhancements](https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-security). |
| CredentialsGuardConfigured | Not used. |
| LsassProtectedProcess | The protection for the Local Security Authority (LSA) process should be configured properly to prevent code injection and credential theft attacks. For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/windows-server/security/credentials-protection-and-management/configuring-additional-lsa-protection). |
| NetBiosDisabled | NetBIOS should be disabled to reduce the risk of data theft attacks through shared folders. |
| RemoteDesktopServiceDisabled | Remote services should be disabled if they are not needed. Note that for the Veeam Cloud Connect infrastructure, this parameter must be enabled if the SP uses Remote Desktop Protocol (RDP) to connect to the tenant backup server. |
| RemotePowerShellDisabled | Remote services should be disabled if they are not needed. |
| RemoteRegistryDisabled | Remote services should be disabled if they are not needed. |
| SMB1Disabled | Outdated network protocol SMB 1.0 should be disabled as it has a number of serious security vulnerabilities including remote code execution. |
| FirewallEnabled | Microsoft Defender Firewall with Advanced Security should be turned on. Also, rules for inbound and outbound connections should be configured according to your infrastructure and Microsoft best practices. For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/best-practices-configuring). |
| WinRmServiceDisabled | Remote services should be disabled if they are not needed. |
| MfaEnabledInBackupConsole | Multi-factor authentication (MFA) should be enabled for the Veeam Backup & Replication console to protect user accounts with additional user verification. |
| ImmutableOrOfflineMediaPresence | Immutable repositories should be used to protect backup files from being modified or deleted.  Offline media should be used to keep backup files in addition to virtual storage devices. |
| LossProtectionEnabled | Password loss protection should be enabled on Veeam Backup Enterprise Manager to provide an alternative way to decrypt the data if a password for encrypted backup or tape is lost. |
| ConfigurationBackupEnabled | Configuration backup should be enabled to reduce the risk of data loss and manage the Veeam Backup & Replication configuration database easier |
| ConfigurationBackupEncryptionEnabled | Data encryption for configuration backup should be enabled to secure sensitive data stored in the configuration database. |
| EmailNotificationsEnabled | Email notifications should be enabled to monitor job statuses. |
| ContainBackupCopies | To be compliant with the 3-2-1 rule, at least one backup copy job should be created, or a scale-out backup repository with the copy mode or archive tier should be added. |
| ReverseIncrementalInUse | The reverse incremental backup method should not be used as it produces the heaviest I/O impact on the backup storage compared to other backup methods. |
| PublicCloudTargetJobEncrypted | To reduce the cloud attack surface, job-level encryption should be enabled. |
| CloudConnectTargetJobEncrypted | To reduce the cloud attack surface, job-level encryption should be enabled. |
| ManualLinuxHostAuthentication | Untrusted Linux VMs and Linux servers must be allowed to connect to the backup server only using manual SSH fingerprint verification. |
| ConfigurationBackupRepositoryNotLocal | The configuration backup must not be stored on the backup server or on the default backup repository to be able to recover its configuration in case of failure. |
| ViProxyTrafficEncrypted | If a VMware backup proxy uses the Network transport mode, it is recommended to transfer VM data over an encrypted TLS connection. |
| HardenedRepositoryNotVirtual | To reduce the attack surface, the hardened repository should be hosted on a physical machine with local storage. |
| TrafficEncryptionEnabled | Network traffic encryption should be enabled in the backup network to ensure secure communication of sensitive data not only between public networks but also between private ones. |
| LinuxServersUsingSSHKeys | Key-based SSH authentication is generally considered more secure than password-based authentication. The private key is not passed to the server and cannot be captured even if a user connects to a fake server and accepts a bad fingerprint. This helps avert man-in-the-middle (MITM) attacks. |
| BackupServicesUnderLocalSystem | The account used to run Veeam services should be a LocalSystem account. |
| ConfigurationBackupEnabledAndEncrypted | Configuration backup should be enabled to reduce the risk of data loss and manage the Veeam Backup & Replication configuration database easier.  Data encryption for configuration backup should be enabled to secure sensitive data stored in the configuration database. |
| PasswordsRotation | For all user accounts added to the [Credentials Manager](https://helpcenter.veeam.com/docs/vbr/userguide/credentials_manager.html?ver=13), [Cloud Credentials Manager](https://helpcenter.veeam.com/docs/vbr/userguide/cloud_credentials.html?ver=13) and [Password Manager](https://helpcenter.veeam.com/docs/vbr/userguide/password_manager.html?ver=13), passwords should be changed at least once a year. |
| HardenedRepositorySshDisabled | SSH connection is necessary only for the deployment of Veeam Data Mover. For security purposes, after adding the hardened repository to the backup infrastructure, the SSH connection should be disabled for the user account used to connect to the Linux server or for the server itself. |
| OsBucketsInComplianceMode | The Compliance retention mode should be used for object storage repositories with immutability enabled. This is a more secure option compared to the Governance retention mode. For more information about retentions modes, see [this Amazon article](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock-overview.html#object-lock-retention-modes). |
| JobsTargetingCloudRepositoriesEncrypted | To reduce the cloud attack surface, job-level encryption should be enabled. |
| BackupServerUpToDate | Veeam Backup & Replication should be updated regularly. Major releases and cumulative patches usually contain bug fixes, performance enhancements, and new features. |
| PostgreSqlUseRecommendedSettings | PostgreSQL should have optimal run-time settings to operate correctly. |
| HardenedRepositoryNotContainsNBDProxies | A VMware backup proxy requires VMware VDDK components to be installed. To reduce the risk of attacks through VMware VDDK vulnerabilities, a hardened repository should have only one role assigned. |
| EncryptionPasswordsComplexityRules | Using strong encryption passwords minimizes the risk of unauthorized access. |
| CredentialsPasswordsComplexityRules | Using strong passwords for third-party services added to Veeam Backup & Replication minimizes the risk of unauthorized access. |
| BackupServerHighAvailabilityEnabled | Not used. |
| LinuxSshPasswordAuthenticationDisabled | Key-based SSH authentication is generally considered more secure than password-based authentication. The private key is not passed to the server and cannot be captured even if a user connects to a fake server and accepts a bad fingerprint. This helps averting man-in-the-middle (MITM) attacks. |
| LinuxPreventRootLogin | Not used. |
| LinuxUseIntrusionDetection | Not used. |
| LinuxUseSecurityModule | The Security-Enhanced Linux (SELinux) module should be enabled to ensure the integrity of the system and reduce the risk of compromise. |
| LinuxAuditdConfigured | To ensure that the system is properly monitored, the Linux audit system should be enabled and configured with log forwarding. |
| LinuxOsIsFipsEnabled | The Linux operating system should run in a FIPS-compliant operation mode. |
| LinuxOsHasVaRandomization | To reduce the risk of compromise, program data should be stored in random memory locations. |
| LinuxOsUsesTcpSyncookies | SYN cookies should be used to reduce the impact of SYN flood denial-of-service attacks. They allow the system to accept valid connections, even if the half-open connection queue is full. |
| LinuxWorldDirectoriesPermissions | World-writable directories should not be executable as they can be modified by any user on the system and are vulnerable to malicious actors. |
| LinuxDisableProblematicServices | The rlogin, telnetd, and rsh-server services should be disabled as they have a number of known security vulnerabilities. |
| LinuxUsePasswordPolicy | Using strong passwords minimizes the risk of unauthorized access. |
| LinuxUseAntivirus | Not used. |
| LinuxUseSecureBoot | To reduce the risk of rootkits compromising the system, the UEFI Secure Boot should be enabled on the machine where Veeam Backup & Replication is installed. |
| LinuxGrubPasswordSet | Not used. |
| LinuxAuditBinariesOwnerIsRoot | Access to the audit binaries should be restricted to prevent unauthorized changes that may affect system performance or result in incomplete event logging. |
| LinuxAuditLogDirectoriesOwnerIsRoot | Access to the audit binaries should be restricted to prevent unauthorized changes that may affect system performance or result in incomplete event logging. |

VBRCapacityExtentStatus

The status of a capacity extent in the scale-out backup repository.

| Member | Description |
| --- | --- |
| 0 | Normal |
| 1 | Pending |
| 2 | Maintenance |
| 4 | Evacuating |
| 8 | Sealed |
| 16 | ResyncRequired |
| 32 | TenantEvacuating |

VBRCloudConnectedLicenseMode

Cloud Connect license options.

| Member | Description |
| --- | --- |
| Enabled | Cloud Connect license enabled. |
| Disabled | Cloud Connect license disabled. |
| Enterprise | Cloud Connect for the Enterprise |

VBRCloudGatewaySelectionType

Type of gateway for the tenant.

| Member | Description |
| --- | --- |
| StandaloneGateways | A gateway that is not added to a gateway pool. |
| GatewayPool | A gateway that is added to a gateway pool. |

VBRCloudInfrastructureState

The state of the cloud infrastructure.

| Member | Description |
| --- | --- |
| Active | Cloud infrastructure is in working state. |
| Maintenance | Cloud infrastructure is in Maintenance mode. |

VBRCompressionLevel

The level of compression.

| Member | Description |
| --- | --- |
| None | Compression is disabled. |
| Dedupe-friendly | The dedupe-friendly compression level. |
| Optimal | The optimal compression level. |
| High | The high compression level. |
| Extreme | The extreme compression level. |

VBRConfigurationBackupScheduleType

Configuration backup job schedule type.

| Member | Description |
| --- | --- |
| Daily | Job starts on selected days of week. |
| Monthly | Job starts on selected days of month. |

VBRDailyOptionsType

Daily basis job schedule type.

| Member | Description |
| --- | --- |
| Everyday | Job runs everyday. |
| WeekDays | Job runs Monday to Friday. |
| SelectedDays | Job runs on selected days. |

VBRDayNumberInMonth

Day in month in job schedule, for example, "the first" (Sunday).

| Member | Description |
| --- | --- |
| First | Job runs every first day of month. |
| Second | Job runs every second day of month. |
| Third | Job runs every third day of month. |
| Fourth | Job runs every fourth day of month. |
| Last | Job runs every last day of month. |
| OnDay | Job runs on selected day of month. |

VBRDetectionEngine

Type of scan engine.

| Member | Description |
| --- | --- |
| External | Third-party antivirus software. |
| VeeamThreatHunter | Veeam signature-based scan engine. |

VBRDiscoveredMongoDBEntityType

| Member | Description |
| --- | --- |
| ReplicaSet | Specific MongoDB replica set. |
| ReplicaSetNode | Specific node within a MongoDB replica set. |

VBRDiscoveredSAPHANAEntityType

| Member | Description |
| --- | --- |
| ScaleOutSystem | Multiple-host SAP system distributed across several servers. |
| Server | Protected server. |
| SAPSystem | Single SAP system installed on one server. |
| Database | Protected database. |

VBREntraIdLogsBackupShortTermRetentionType

Retention period type.

| Member | Description |
| --- | --- |
| 0 | Restore points are removed after the specified amount of days. |
| 1 | Restore points are removed after the specified amount of months. |
| 2 | Restore points are removed after the specified amount of years. |

VBREntraIDTenantItemType

Type of a Microsoft Entra ID item.

|  | Description |
| --- | --- |
| User | Entra ID user. |
| Group | Entra ID group. |
| AdminUnit | Entra ID administrative unit. |
| Role | Entra ID role. |
| Application | Entra ID application or service principal. |
| DeviceConfiguration | Entra ID Intune policy. |
| ConditionalAccessPolicy | Entra ID Conditional Access policy. |

VBREPPermissionType

User access permissions to repositories for Veeam Agent for Microsoft Windows backups.

| Member | Description |
| --- | --- |
| Everyone | Everyone has permission. |
| NoOne | No one has permission. |
| OnlySelectedUsers | Selected users have permission. |

VBREpThrottlingAgentType

| Member | Description |
| --- | --- |
| Workstations | Throttle Veeam Agent on workstations. |
| Servers | Throttle Veeam Agent on servers |
| AllHosts | Throttle Veeam Agent on all computers. |

VBRExportRetentionPeriod

A retention period of exported backup files.

| Member | Description |
| --- | --- |
| Never | Veeam Backup & Replication never deletes exported backup files. |
| In1Month | Veeam Backup & Replication will delete exported backup files in 1 month. |
| In3Months | Veeam Backup & Replication will delete exported backup files in 3 months. |
| In6Months | Veeam Backup & Replication will delete exported backup files in 6 months. |
| In1Year | Veeam Backup & Replication will delete exported backup files in 1 year. |
| In2Years | Veeam Backup & Replication will delete exported backup files in 2 years. |
| In3Years | Veeam Backup & Replication will delete exported backup files in 3 years. |
| In5Years | Veeam Backup & Replication will delete exported backup files in 5 years. |
| In7Years | Veeam Backup & Replication will delete exported backup files in 7 years. |

VBRFailoverPlanType

Failover plan type.

| Member | Description |
| --- | --- |
| Local | Non-cloud failover plan |
| Cloud | Cloud failover plan on cloud user side |
| Tenant | Cloud failover plan of a tenant on cloud provider side |

VBRFileToTapeBackupPolicyType

File to tape job schedule type.

| Member | Description |
| --- | --- |
| Daily | Job starts on selected days of week. |
| Monthly | Job starts on selected days of month. |

VBRFullBackupToTapePolicyType

Virtual full backup schedule type.

| Member | Description |
| --- | --- |
| Monthly | Virtual full is created on selected days of month. |
| WeeklyOnDays | Virtual full is created on selected days of week. |

VBRGatewayMode

| Member | Description |
| --- | --- |
| Automatic | Automatic gateway selection. |
| SelectedGateway | Manual gateway selection. |

VBRGatewayNetworkMode

Network mode for cloud gateways. The network mode defines how the cloud gateway communicates with the Veeam backup server on the tenant side.

| Member | Description |
| --- | --- |
| Direct | Direct network mode. |
| NAT | NAT network mode. |

VBRGFSMonthlyKind

Monthly basis job schedule type.

| Member | Description |
| --- | --- |
| DayOfWeek | Job runs on a selected day in month, for example, the first Sunday of month. |
| DayOfMonth | Job runs on a selected date, for example, on the 1st (of January). |

VBRGoogleCloudComputeDiskType

Google Cloud compute engine disk type.

| Member | Description |
| --- | --- |
| BalancedPersistent | Balanced persistent disk type for Google Cloud Compute Engine VM. |
| SSDPersistent | SSD persistent disk type for Google Cloud Compute Engine VM. |
| StandardPersistent | Standard persistent disk type for Google Cloud Compute Engine VM. |

VBRGoogleCloudComputeVirusDetectionAction

Action that Veeam Backup & Replication will perform if detecting a virus when scanning the VM with antivirus software before restoring it to Google Compute Engine.

| Member | Description |
| --- | --- |
| ConnectToIsolatedNetwork | Restore the VM to an isolated Google Cloud network. |
| AbortRecovery | Cancel the VM restore session. |

VBRGoogleCloudServiceType

Type of the Google Cloud object storage repository added to the backup infrastructure.

| Member | Description |
| --- | --- |
| ExternalRepository | External repository. |
| CapacityTier | Extent of the capacity tier. |
| ArchiveTier | Extent of the archive tier. |

VBRGuestOsType

Oracle database guest OS type.

| Member | Description |
| --- | --- |
| Unknown | Oracle database runs on VM with unknown OS. |
| Windows | Oracle database runs on Windows-based VM. |
| Linux | Oracle database runs on Linux-based VM. |
| Other | Oracle database runs on VM with other OS. |

VBRRepositoryImmutabilityMode

Immutability mode settings.

| Member | Description |
| --- | --- |
| RepositoryRetention | Repository retention. |
| BackupRetention | Backup retention. |

VBRInfrastructureValidationErrorType

Validation errors.

| Member | Description |
| --- | --- |
| AddedByIPAddress | Contains IPv4. |
| HasIPv6Config | Contains IPv6. |

VBRInstanceLicenseObjectType

Types of instance licensed workloads.

| Member | Description |
| --- | --- |
| VM | Protected VM. |
| Server | Protected server. |
| Workstation | Protected workstation. |
| Application | Protected software. |
| AHVVM | Protected VMs that reside on Nutanix AHV clusters. |
| CloudMachine | Protected machine. |
| CloudConnectBackupVM | Protected Cloud Connect VMs |
| CloudConnectBackupWorkstation | Protected Cloud Connect Workstations. |
| CloudConnectBackupServer | Protected Cloud Connect Servers. |
| CloudConnectReplicationVM | Protected Cloud Connect Replicas. |
| FileShare | Protected file share. |
| UnlicensedAgent | Protected non-licensed Veeam Agents. |

VBRJobType

Job type.

| Member | Description |
| --- | --- |
| Backup | Backup job. |
| BackupSync | Backup copy job. |
| BackupToTape | Backup to tape job. |
| ConfigurationBackup | Configuration backup job. |
| EndpointBackup | Veeam Agent for Microsoft Windows backup job. |
| FileToTape | File to tape job. |
| TapeCatalog | Tape cataloging. |
| TapeEject | Tape ejecting. |
| TapeErase | Tape erasing. |
| TapeExport | Tape exporting. |
| TapeImport | Tape importing. |
| TapeInventory | Tape inventorying. |
| TapeRescan | Tape rescanning. |

VBRLicenseEdition

License edition.

| Member | Description |
| --- | --- |
| Community | Community edition. |
| Standard | Standard edition. |
| Enterprise | Enterprise edition. |
| EnterprisePlus | EnterprisePlus edition. |
| Unspecified | Not specified edition. |

VBRLicenseUsageReportType

Type of a report file.

| Member | Description |
| --- | --- |
| HTML | HTML type. |
| PDF | PDF type. |
| JSON | JSON type. |

VBRLicenseStatus

License status.

| Member | Description |
| --- | --- |
| Valid | Valid. |
| Expired | Expired. |
| Invalid | Invalid. |

VBRLicenseType

License type.

| Member | Description |
| --- | --- |
| Rental | Rental type. |
| Perpetual | Perpetual type. |
| Subscription | Subscription type. |
| Evaluation | Evaluation type. |
| Free | Free type. |
| Empty | Empty type. |
| NFR | NFR type. |

VBRLinuxAgentPackageType

Type of Veeam Agent for Linux packages.

| Member | Description |
| --- | --- |
| Standard | Veeam Agent for Linux packages with kernel module for creating snapshots. |
| Nosnap | Veeam Agent for Linux packages without kernel module for creating snapshots. |

VBRLogStatus

Log entry status.

| Member | Description |
| --- | --- |
| None | Job session status not applicable. |
| Success | Job session finished with success. |
| Warning | Job session finished with warning. |
| Failed | Job session failed. |

VBRMongoDBDeploymentType

Type of MongoDB deployment.

| Member | Description |
| --- | --- |
| ReplicaSet | MongoDB replica set type deployment. |

VBRMongoDBOplogRetentionPolicy

Types of retention policy options for MongoDB oplog backups .

| Member | Description |
| --- | --- |
| KeepLastDays | Retains oplog backup for a specified number of days, regardless of the state of the corresponding full backup. |
| KeepWithBackup | Retains oplog backup simultaneously with the corresponding full backup. |

VBRObjectStorageRepositoryType

Types of object storage repositories.

| Member | Description |
| --- | --- |
| AmazonS3 | Amazon S3. |
| AmazonS3Compatible | S3 compatible |
| AzureBlob | Azure Blob |
| AzureDataBox | Azure Data Box |
| GoogleCloudStorage | Google Cloud |
| Wasabi | Wasabi Cloud Storage |
| DataCloudVault | Veeam Data Cloud Vault |
| ElevenEleven | 11:11 Cloud Object Storage |

VBROracleDatabaseRecoveryModel

Oracle database recovery mode.

| Member | Description |
| --- | --- |
| ArchiveLog | ARCHIVELOG mode is enabled for the Oracle database. |
| NoArchiveLog | ARCHIVELOG mode is not enabled for the Oracle database. |

VBROrganizationvDCAllocationModel

Allocation model.

| Member | Description |
| --- | --- |
| PayAsYouGo | Pay-as-you-go allocation model. |
| AllocationPool | Allocation pool allocation model. |
| ReservationPool | Reservation pool allocation model. |

VBRPeriodicityType

Script run mode.

| Member | Description |
| --- | --- |
| Cycles | Script runs after a set number of job runs (for example, every second job run). |
| Days | Script runs on selected days. |

VBRPlatform:

Virtualization platform.

| Member | Description |
| --- | --- |
| VMware | VMware virtualization platform. |
| Hyper-V | Hyper-V virtualization platform. |

VBRRansomwareScanningSensitivity

Malware index settings.

| Member | Description |
| --- | --- |
| Low | Low |
| BetweenLowAndNormal | Between low and normal |
| Normal | Normal |
| BetweenNormalAndExtreme | Between normal and extreme |
| Extreme | Extreme |

VBRReplicaStatus

Status of replica VM.

| Member | Description |
| --- | --- |
| Ready | Ready |
| Processing | Processing |
| SureBackup | SureBackup |
| Failover | Failover |
| FailedFailover | Failed failover |
| PermanentFailover | Permanent failover |
| Failback | Failback |

VBRRepositoryConnectionType

Connection type to object storage repository.

| Member | Description |
| --- | --- |
| Direct | Direct connection using proxy. |
| Gateway | Connection using gateway server. |

VBRRepositoryExtentStatus

Scale-out backup repository status.

| Member | Description |
| --- | --- |
| Unknown | Extent is not added to any scale-out repository. |
| Normal | Extent is in working mode. |
| Pending | Extent is in process of switching to Maintenance mode. |
| Maintenance | Extent is in Maintenance mode. |
| Evacuate | Extent is in Maintenance mode and is evacuating backups. |

VBRRestorePointType

Restore point type.

| Member | Description |
| --- | --- |
| Full | Restore point is a VBK file (full backup). |
| Rollback | Restore point is a VRB file (reverse incremental backup). |
| Increment | Restore point is a VIB file (forward incremental backup). |
| Different | Restore point is not identified. |
| Snapshot | Restore point is a snapshot. |

VBRScaleOutBackupRepositoryPolicyType

Scale-out backup repository policy.

| Member | Description |
| --- | --- |
| DataLocality | Data locality policy. |
| Performance | Performance policy. |

VBRSessionResult

Session result. Indicates the state with which a job run or a task session finished.

| Member | Description |
| --- | --- |
| None | The result is N/A. |
| Success | The session finished successfully. |
| Warning | The session finished with warnings. |
| Failed | The session failed. |

VBRSessionState

Job or task current state.

| Member | Description |
| --- | --- |
| ActionRequired | [For move or copy backups operation]  The job is stopped with an error and requires an action (for example, job retry or undo). |
| Idle | The job is idle. The job is in idle state between the scheduled job runs. |
| Pausing | The job is pausing. |
| Pending | The job is pending. |
| Postprocessing | The job performs post processing tasks. |
| Resuming | The job resumes after a pause. |
| Starting | The job is starting. |
| Stopped | The job is stopped.  Note: This state displays for any type of the stopped job and does not depend on the way the job was stopped (manually, according to a schedule, and so on). |
| Stopping | The job got a command to stop and currently is stopping. |
| WaitingRepository | The job is waiting for the repository to become available. |
| WaitingSlot | [ Used for offload sessions to capacity tier ]  The job is waiting for backup repository resources. |
| WaitingTape | The job is waiting for tape (tape jobs). |
| Working | The job is running. |

VBRSocketLicenseObjectType

Types of socket licensed workloads.

| Member | Description |
| --- | --- |
| HyperV | Protected HyperV workloads. |
| vSphere | Protected vSphere workloads. |
| Nutanix | Protected Nutanix workloads. |
| Universal | Protected VUL workloads. |
| Unlicensed | Unlicensed workloads. |

VBRSpeedUnit

| Member | Description |
| --- | --- |
| MbitPerSec | Megabit per second unit. |
| MbytePerSec | Megabyte per second unit. |
| KbytePerSec | Kilobyte per second unit. |

VBRS3CompatibleAccessControlPolicyType

| Member | Description |
| --- | --- |
| AllowAll | Direct access insecure. |
| VBRManaged | Access using gateway server. |
| S3CompatibleManaged | Direct access using token. |

VBRTapeDriveState

Tape drive state.

| Member | Description |
| --- | --- |
| Loaded | Tape drive is loaded. |
| Empty | Tape drive is empty. |

VBRTapeLibraryState

Tape library state.

| Member | Description |
| --- | --- |
| Online | Tape library is online. |
| Offline | Tape library is offline. |

VBRTapeLibraryType

Tape library type.

| Member | Description |
| --- | --- |
| Automated | Tape library is automated tape device. |
| StandaloneDrive | Tape library is standalone tape drive. |

VBRTapeMediaPoolRetentionType

Tape retention period type.

| Member | Description |
| --- | --- |
| Never | Data on tape is never overwritten. |
| Periodic | Data on tape is protected for selected period of time. |
| Cyclic | Data on tape is not protected. |

VBRTapeMediaPoolType

Media pool type.

| Member | Description |
| --- | --- |
| Unrecognized | Unrecognized media pool. |
| Free | Free media pool. |
| Retired | Retired media pool. |
| Custom | Standard media pool. |
| Imported | Imported media pool. |
| Gfs | GFS media pool. |

VBRTapeMediaPoolPeriod

Tape retention measure unit.

| Member | Description |
| --- | --- |
| None | Tape data is not protected. |
| Days | Tape data retention period is measured in days. |
| Weeks | Tape data retention period is measured in weeks. |
| Months | Tape data retention period is measured in months. |

VBRTapeMediaSetCreationPolicyType

Policy for creating media sets.

| Member | Description |
| --- | --- |
| Never | New media sets are not created. |
| Always | New media set is created for each tape job session. |
| Daily | New media set is created on particular days. |
| Monthly | Not supported. |

VBRViNetworkInfoType

Network type.

| Member | Description |
| --- | --- |
| Cloud | Cloud network. |
| Hv | Hyper-V network. |
| ViDVS | VMware network connected to distributed virtual switch (DVS). |
| ViSimple | VMware network connected to standard switch. |

VBRVirtualSwitchType

Virtual switch type.

| Member | Description |
| --- | --- |
| DVS | Distributed virtual switch (DVS). |
| Simple | Standard switch. |

VBRUpdateSourceRepositoryType

Update source repository type.

| Member | Description |
| --- | --- |
| Official | Veeam update repository. |
| Custom | Local mirror of Veeam update repository. |

VBRUpdateType

Update type.

| Member | Description |
| --- | --- |
| SecurityOnly | Security updates are installed. |
| SecurityAndOptional | Security and optional updates are installed. |


