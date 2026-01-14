---
title: "VBRIndividualComputerCustomCredentials"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrindividualcomputercustomcredentials.html"
last_updated: "2/11/2025"
product_version: "13.0.1.1071"
---

# VBRIndividualComputerCustomCredentials

In this article

Contains a method for authenticating individual computers.

Properties

| Property | Type | Description |
| --- | --- | --- |
| HostName | string | DNS-name or IP address of the computer. |
| Credentials | CCredentials | Credentials for authenticating the computer. |
| UseTemporaryCertificate | Bool | Temporary certificate for computer authentication. |
| UseTemporarySSHCredentials | Bool | Single-use credentials to access Linux-based computers. |

Related Commands

[New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md)

Page updated 2/11/2025

Page content applies to build 13.0.1.1071
