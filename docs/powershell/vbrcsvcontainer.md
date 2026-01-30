---
title: "VBRCSVContainer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcsvcontainer.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCSVContainer


Contains a scope of computers listed in a CSV file.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Path | string | The path to the CSV file. |
| MasterCredentials | CCredentials | Master account credentials for authenticating with all computers listed in a CSV file. |
| NetworkCredentials | CCredentials | Credentials for authenticating with the shared folder. Used if a CSV file is located on a file share. |
| UseCustomCredentials | bool | Indicates if custom credentials are used for authenticating with some computers listed in a CSV file. |
| CustomCredentials | [VBRCSVCustomCredentials[]](vbrcsvcustomcredentials.md) | Custom credentials for authenticating with associated computers. |

Related Commands

[New-VBRCSVContainer](new-vbrcsvcontainer.md)


