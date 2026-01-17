---
title: "VEORIRDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/veorirdatabase.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# VEORIRDatabase


Contains details about a Oracle database published during an instant recovery session.

| Property | Type | Description |
| --- | --- | --- |
| Session | [VEIRSessionID](veirsessionid.md) | Contains details about the instant recovery session. |
| RestorePoint | GUID | Restore point ID. |
| DatabaseName | String | Name of the database on the target server. |
| OracleSid | String | Oracle System Identifier (SID) of the database on the target server. |
| OracleHome | String | Oracle Home path. |
| ServerName | String | DNS name or IP address of the target server. |
| ToDateTime | DateTime | Date and time in the UTC format of the state to which the database is recovered. |
| FileStatus | String | Recovery status of the file. |
| TargetPath | String[] | Target paths for the database files. |
| Log | [VEORInstantRecoveryLogItem](veorinstantrecoverylogitem.md)[] | Instant recovery log items. |
| Status | String | Status of the instant recovery operation. |
| SwitchOverOptions | [VEORIRSchedule](veorirschedule.md) | Switchover options for the instant recovery operation. |

Related Commands

* [Get-VEORIRDatabase](get-veorirdatabase.md)
* [Set-VEORIRDatabase](set-veorirdatabase.md)
* [Switch-VEORIRDatabase](switch-veorirdatabase.md)
* [Stop-VEORInstantRecovery](stop-veorinstantrecovery.md)


