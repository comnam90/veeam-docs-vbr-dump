---
title: "Tape Servers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tape_servers.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---

# Tape Servers


When you have deployed a tape server and connected the tape device to it, you need to add the tape server to the Veeam backup server. To do so, you must assign the role of the tape server to a Windows or Linux server that is already added to the list of managed servers. For the tape server system requirements, see [System Requirements](system_requirements.md#tape_server).

|  |
| --- |
| Note |
| The tape server role requires root access rights. For this reason, Veeam Software Appliance, Veeam Infrastructure Appliance and hardened repository cannot be used as the tape server. |

You can add multiple tape servers to the same installation of Veeam Backup & Replication. But note that you cannot add one tape library to two different tape servers and write data to it from both tape servers.

Related Topics

* [Adding Tape Servers](adding_tape_server.md)
* [Removing Tape Servers](remove_tapeserver.md)
* [Updating Tape Servers](updating_tapeserver.md)
* [Rescanning Tape Servers](rescan_tape_server.md)
* [Modifying Tape Servers](managing_tapeservers.md)
* [Replacing Tape Servers](replacing_tape_servers.md)


