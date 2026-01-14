---
title: "veorlinuxcredential"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/veorlinuxcredential.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains a Linux credential record used connect to a machine with Oracle.

| Property | Type | Description |
| --- | --- | --- |
| Account | String | Account that will be used to connect to the target Linux server. |
| UseKeyFile | Bool | If True, a private key is used to connect to the target Linux server. |
| PrivateKeyFilePath | String | Path for the private key. |
| ElevateAccountToRoot | Bool | If True, the account is elevated to root. |
| AddToSudoers | Bool | If True, the account is added to the sudoers file. |
| UseSuIfSudoUnavailable | Bool | If True, the su command is used instead of the sudo command. |

Related Commands

[New-VEORLinuxCredential](new-veorlinuxcredential.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
