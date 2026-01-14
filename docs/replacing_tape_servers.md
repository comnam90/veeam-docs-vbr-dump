---
title: "Replacing Tape Servers"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/replacing_tape_servers.html"
last_updated: "2/19/2024"
product_version: "13.0.1.1071"
---

# Replacing Tape Servers

In this article

You can replace the tape server with another tape server and continue to use the existing libraries and tapes with it.

To correctly replace a tape server:

1. Physically disconnect libraries from the old tape server or disable the tape changer device and drives in the Device Manager on this tape server.
2. Remove the old tape server from the tape infrastructure, as described in section [Removing Tape Servers](remove_tapeserver.md).
3. Connect your existing tape devices to the new tape server, as described in section [Connecting Tape Devices](connecting_tape_devices.md).
4. Add a new tape server, as described in section [Adding Tape Servers](adding_tape_server.md).

All the information about existing tapes will be preserved after switching to the new tape server.

Page updated 2/19/2024

Page content applies to build 13.0.1.1071
