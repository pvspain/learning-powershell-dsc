# learning-powershell-dsc

## Resources

- Books
  - [Learning PowerShell DSC - Second Edition][2]
  - [Windows Server 2016 Automation with PowerShell Cookbook - Second Edition][3]
- Microsoft Virtual Academy
  - [Getting Started with Powershell Desired State Configuration][1]

## Overview

**Desired State Configuration (DSC)** is a management platform for the Windows, Linux and macOS operating systems.
It is implemented as part of *PowerShell*. DSC enables you to define a computer's desired
state *declaratively* and have PowerShell ensure the computer is configured accordingly and
remains in that state. It is an essential part of Microsoft's DevOps strategy.

- Microsoft is a late starter in the DevOps market with DSC.
- Similar to other cross-platform, declarative management products such as [Puppet][4], [Chef][5] and [Ansible][6].
- Can run in both **push** (Ansible) or **pull** (Puppet, Chef) modes.
- DSC is available as part of *Windows PowerShell* and *PowerShell Core*.
- DSC version numbers match the related PowerShell version.
- **Windows PowerShell**
  - First released in version 4 of the [Windows Management Framework][7], in October 2013.
  - Bundled with *Windows Server 2012 R2+* and *Windows 8.1+*.
  - Dependent upon the Windows [*.NET Framework*][11] (FullCLR).
  - Latest and final Windows-only version is 5.1 (August 2, 2016). 
    - Critical bug-fixes only beyond that date.
- **PowerShell Core** 
  - An [open-source][8], cross-platform (Windows, Linux and macOS) version of PowerShell, [generally available (GA) from January 2018][10].
  - Dependent upon the cross-platform [*.NET Core*][12] framework (CoreCLR).
  - Latest GA version is 6.1.3 (February 19, 2019)


[1]: https://mva.microsoft.com/en-US/training-courses/getting-started-with-powershell-desired-state-configuration-dsc-8672?l=ZwHuclG1_2504984382
[2]: https://www.packtpub.com/networking-and-servers/learning-powershell-dsc-second-edition
[3]: https://www.packtpub.com/networking-and-servers/windows-server-2016-automation-powershell-cookbook-second-edition
[4]: https://puppet.com/
[5]: https://www.chef.io/chef/
[6]: https://www.ansible.com/
[7]: https://docs.microsoft.com/en-us/powershell/wmf/overview
[8]: https://github.com/powershell/powershell
[10]: https://devblogs.microsoft.com/powershell/powershell-core-6-0-generally-available-ga-and-supported/
[11]: https://en.wikipedia.org/wiki/.NET_Framework
[12]: https://en.wikipedia.org/wiki/.NET_Core