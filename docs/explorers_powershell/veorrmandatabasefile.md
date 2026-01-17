---
title: "VEORRMANDatabaseFile"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/veorrmandatabasefile.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---

# VEORRMANDatabaseFile


Contains details about a database file of a database backed up with Veeam Plug-in for Oracle RMAN.

| Property | Type | Description |
| --- | --- | --- |
| Path | String | Path to the database file. |
| Type | VEORRMANDatabaseFileType | Database file type. Possible values:   * Controlfile * Datafile * Logfile * Tempfile * FastRecoveryArea |

Related Commands

[Get-VEORRMANDatabaseFile](get-veorrmandatabasefile.md)


