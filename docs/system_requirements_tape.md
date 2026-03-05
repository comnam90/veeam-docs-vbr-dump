---
title: "Tape"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_tape.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# Tape


Tape

| Specification | Requirement |
| Hardware | The following types of tape libraries (including VTL) and standalone drives are supported:   * LTO3-LTO10 * IBM 3592 (TS1160 and TS1170)   Tape device must be directly attached to the backup server or to a tape proxy server through SAS, FC or iSCSI interface. Note that VMware [does not support](https://knowledge.broadcom.com/external/article/310914/configuring-vendorsupported-tape-drives.html) connecting tape libraries to ESXi for VM pass-through. |
| Software | * Tape devices without device-specific, vendor-supplied OEM drivers for Windows will appear in Windows Device Manager as Unknown or Generic and require enabling native SCSI commands mode.  * If multiple driver installation modes are available for your tape device, use the one that allows for multiple open handles from a host to a drive to exist at the same time. Usually, such drivers are referred to as “non-exclusive”.  * No other backup server must be interacting with the tape device. |

For more information, see the [Tape Device Support](working_with_tapes.md) section.


