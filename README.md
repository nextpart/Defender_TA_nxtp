## Technical Add-On for Windows Defender

[![Build Status](https://dev.azure.com/NEXTPART/Splunking/_apis/build/status/Defender%20TA?repoName=Defender_TA_nxtp&branchName=main)](https://dev.azure.com/NEXTPART/Splunking/_build/latest?definitionId=169&repoName=Defender_TA_nxtp&branchName=main)
[![image](https://img.shields.io/badge/Maintained%20in-Azure%20DevOps-1f425f.svg?logo=Azure%20DevOps)](https://dev.azure.com/NEXTPART/Splunking)
[![image](https://img.shields.io/badge/Contact-NEXTPART-1abc9c.svg)](mailto:info@nextpart.io)

This extension for [Splunk®](https://www.splunk.com/) is a rewrite of the Add-on already
created by [pdoconnell](https://github.com/pdoconnell)
([TA-microsoft-windefender](https://github.com/pdoconnell/TA-microsoft-windefender))
that we adapt to our needs and requirements. At this point we would like to thank
Patrick for the great work he has done with his project and from which we could learn a
lot as well as all the other members of the
[Splunk Community](https://community.splunk.com/t5/Community/ct-p/en-us) who publish
their work. You are heroes :clap:

#### Author information

- Author: Nextpart Security Intelligence GmbH
- Version: `X.X.X` (dynamic)
- Creation: May 22, 2020

#### Using this Application

Source: `XmlWinEventLog` Sourcetype: `XmlWinEventLog:Defender`

This add-on is intended as a complement to the
[Splunk Add-on for Microsoft Windows](https://splunkbase.splunk.com/app/742/), which
also manages the basic operations of the field extraction from the xml or raw events. If
you have
[installed](https://docs.splunk.com/Documentation/WindowsAddOn/latest/User/Install) that
add-on you can also use this one to extract more information and present it according to
[CIM](https://docs.splunk.com/Documentation/CIM/latest/User/Overview).

###### Upgrade

Remove the app using splunk plugin tool

```bash
$SPLUNK_HOME/bin/splunk remove app Defender_TA_nxtp
```

###### Install the app

```bash
$SPLUNK_HOME/bin/splunk install app Defender_TA_nxtp_<version>.tgz
```

###### Forwarding Data

Once you have installed the Technical Add-On you can start sending data. In order to do
so you need Windows instances running
[Windows Defender AntiVirus](https://docs.microsoft.com/en-gb/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)
and the
[Splunk Universal Forwarder](https://www.splunk.com/en_us/download/universal-forwarder.html)
with the according configuration for you environment. Then you can also use this add-on
on your endpoints and activate forwarding by adding the following content to the
`inputs.conf` file in the `local` directory:

```
## Custom Inputs.conf for microsoft windows defender events

[WinEventLog://Microsoft-Windows-Windows Defender/Operational]
disabled = false
blacklist = 1001, 1150, 2011, 2000, 2001, 2002, 2010
```

#### Update History

- `0.3.X` October 05, 2020: Detection results will be extracted with multiple fields if
  more details are provided and the source has been adapted for general use outside the
  dev environment and should work well for general usage.

- `0.2.X` August 25, 2020: First possible field extractions according to the CIM event
  types malware and IDS alerts with documentation of these.

- `0.1.X` July 28, 2020: Template Application from Add-on Builder with specification of
  Index, Source and Sourcetype.

- `0.0.X` May 22, 2020: Initialization of the repository with first specifications in
  the documentation.

#### Copyright & License

Copyright © 2019 Nextpart Security Intelligence GmbH

This program is free software; you can redistribute it and/or modify it under the terms
of the GNU General Public License as published by the Free Software Foundation; either
version 2 of the License, or (at your option) any later version.

Find more information about this on the [LICENSE](./LICENSE) file.
