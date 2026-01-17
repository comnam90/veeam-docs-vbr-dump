---
title: "VEMDBLinuxCredentials"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vemdblinuxcredentials.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# VEMDBLinuxCredentials


Contains a Linux credential record used connect to a machine with MongoDB.

| Property | Type | Description |
| --- | --- | --- |
| Account | String | Account that will be used to connect to the target Linux server. |
| UseKeyFile | Bool | If True, a private key is used to connect to the target Linux server. |
| PrivateKeyFilePath | String | Path for the private key. |
| ElevateAccountToRoot | Bool | If True, the account is elevated to root. |
| AddToSudoers | Bool | If True, the account is added to the sudoers file. |
| UseSuIfSudoUnavailable | Bool | If True, the su command is used instead of the sudo command. |

Related Commands

[New-VEMDBLinuxCredentials](new-vemdblinuxcredentials.md)


