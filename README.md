# learning-powershell-dsc

## Content

- [learning-powershell-dsc](#learning-powershell-dsc)
  - [Content](#content)
  - [Resources](#resources)
  - [Overview](#overview)
  - [Architecture](#architecture)
  - [Glossary](#glossary)
  - [Push and Pull modes](#push-and-pull-modes)
    - [Pull](#pull)
    - [Push](#push)
  
## Resources

- Books
  - [Learning PowerShell DSC - Second Edition][2]
  - [Windows Server 2016 Automation with PowerShell Cookbook - Second Edition][3]
- Microsoft Virtual Academy
  - [Getting Started with Powershell Desired State Configuration][1]
  - [Advanced PowerShell Desired State Configuration (DSC) and Custom Resources][16]
- Utilities
  - [ReverseDSC package][15]
    - This DSC module is used to extract the DSC Configuration of existing environments

## Overview

**Desired State Configuration (DSC)** is a management platform for the Windows, Linux and macOS operating systems.
It is implemented as part of *PowerShell*. DSC enables you to define a computer's desired
state *declaratively* and have PowerShell ensure the computer is configured accordingly and
remains in that state. It is an essential part of Microsoft's DevOps strategy.

- Microsoft is a late starter in the DevOps market with DSC.
- Similar to other cross-platform, declarative management products such as [Puppet][4], [Chef][5] and [Ansible][6].
- Can run in both **push** or **pull** modes, like the other products mentioned above.
- DSC is available as part of *Windows PowerShell* and *PowerShell Core*.
- DSC version numbers match the related Windows PowerShell version.
- **Windows PowerShell**
  - First released in version 4 of the [Windows Management Framework][7], in October 2013.
  - Bundled with *Windows Server 2012 R2+* and *Windows 8.1+*.
  - Dependent upon the Windows [*.NET Framework*][11] (FullCLR).
  - Latest and final Windows-only version is 5.1 (August 2, 2016). 
    - Critical bug-fixes only beyond that date.
- **PowerShell Core** 
  - An [open-source][8], cross-platform (Windows, Linux and macOS) version of PowerShell, [generally available (GA) from January 2018][10].
  - Dependent upon the cross-platform [*.NET Core*][12] framework (CoreCLR).
  - [Latest GA version][13] is 6.1.3 (February 19, 2019)
- [**PowerShell DSC for Linux**][14]
  - Supports a Linux-based *Local Configuration Manager (LCM)*, and Linux-based *Resources*.
  - *Pull Server* must be Windows-based.
  - Latest release is v1.1.1-926 (January 9, 2019)

## Architecture

By its simplest definition, DSC is:
-  a Windows service, 
-  a set of configuration files, and 
-  a set of PowerShell modules and scripts. 

there is more to this: 
- push and pull modes, 
- MOF compilation, and 
- module packaging

## Glossary 

| Term                   | Description                                                                                                                |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Idempotent             | An operation that can be performed multiple times with the same result.                                                    |
| DSC configuration file | A PowerShell script file that contains the DSC DSL syntax and list of DSC resources to execute.                            |
| DSC configuration data | A PowerShell data file or separate code block that defines data that can change on target nodes.                           |
| DSC resource           | A PowerShell module that contains idempotent functions that brings a target node to a desired state.                       |
| DSC cmdlets            | PowerShell cmdlets specially made for DSC operations.                                                                      |
| MOF file               | Contains the machine-readable version of a DSC configuration file.                                                         |
| LCM                    | The DSC engine that controls the entire execution of DSC configurations.                                                   |
| CM                     | The process of managing configuration on the servers in your environment.                                                  |
| Drift                  | A bucket term to indicate the difference between the desired state of a machine and the current state.                     |
| Compilation            | Generally a programming term, in this case, it refers to the process of turning a DSC configuration file into an MOF file. |
| Metadata               | Data that describes other data. Summarizes basic information about other data in a machine-readable format.                |

## Push and Pull modes

The more established CM products available on the market have coalesced into two approaches: **push** and **pull**. These refer to the directions and methods used to move information from the place where it is stored to the **target nodes**.

### Pull

Most CM products primarily use the *pull* method, which means they rely on **agents** to schedule, distribute, and rectify configurations on *target nodes*,  but have a central **server** that holds configuration information and data. 

The *server* maintains the current state of all the *target* nodes, while the *agent* periodically executes configuration runs on the target nodes. This is a simplistic but effective approach, as it enables several highly important features. Because the server has the state of every machine:
- A queryable record of all servers exists.
- You can see the state of your entire infrastructure.
- Configuration runs can be executed on demand against a set of nodes or all nodes.

Popular CM products that primarily use this model are [Puppet][4] and [Chef][5].

### Push

[Ansible][6] primarily uses the *push* model, where a single workstation or user calls the *agent* directly. The user is solely responsible for scheduling executions and resolving all dependencies that the agent needs. It's a loose but flexible network as it allows the agents to operate even if there isn't a central server to report status. This is called a *master-less deployment*. 

The benefit of this model largely depends on your specific use cases. 
- Some environments need granularity in scheduling and a high level of control over how and when agents perform actions. 
- They choose when to check for drift, and when to correct drift on a server-to-server basis or an entire environment.
- Common uses for this approach are test and QA environments, where software configurations change frequently and there is a high expectation of customization.
  
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
[13]: https://github.com/PowerShell/PowerShell/releases
[14]: https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases
[15]: https://www.powershellgallery.com/packages/ReverseDSC/
[16]: https://mva.microsoft.com/en-US/training-courses/advanced-powershell-desired-state-configuration-dsc-and-custom-resources-8702?l=3DnsS2H1_1504984382

