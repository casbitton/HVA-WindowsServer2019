## Overview

Deploy new Windows Server 2019 virtual machines on demand while you drink a beer.

This is a highly opinionated base install specific to my Intel NUC [lab](#Further-Notes). You might find it useful.

Gremlins may appear after dark if used in production environments.

Cheers! 🍻

---

## Prerequisites:
* A host Server running - Windows Server 2019 Datacenter with [Hyper-V Role](https://docs.microsoft.com/en-us/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)
* Adequate storage and memory for builds
* 3 Virtual Switches configured via [Hyper-V Manager](https://docs.microsoft.com/en-us/windows-server/virtualization/hyper-v/get-started/create-a-virtual-switch-for-hyper-v-virtual-machines). Each Virtual Switch will be named:
  * External Switch
  * Internal Switch
  * Private Switch
* Windows Server 2019 ISO from [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server)

#### Optional Cloud Enhancement ☁️🚀🛰
* This can be paired with [GitLab](https://about.gitlab.com/) or [Azure DevOps](https://azure.microsoft.com/en-us/services/devops/) to yield some fantastic results
* Install a runner from your favorite CI/CD platform of choice, and the deployment process can be performed entirely from any browser 👌

---

## Supported Operating Systems:
* Windows Server 2019 Datacenter Evaluation - ServerDatacenterCor
* Windows Server 2019 Datacenter Evaluation (Desktop Experience) - ServerDatacenter

## Each new build includes:
* Built from Source each run
* Automatic virtual machine activation
* Configured for use with 
  * [Ansible](https://github.com/ansible/ansible)
  * [Chocolatey](https://github.com/chocolatey/choco)
* Lightning fast deploy on modern hardware
  * Desktop Experience , ~10 Minutes
  * Core , ~5 Minutes

---

## Getting Started

This is short and sweet, enjoy 😀

`New-WindowsServer2019VM.ps1` has minimal options, this may be expanded upon in the future. 

- Name
- CPU
- Memory
- Storage
- SwitchName
- WindowsISO
- WindowsEdition
- AdminPassword (Optional)

**Security Note:** _The administrator password will be generated for you if not selected. This will be output to you in plaintext upon build completion in either scenario._

## Example Build

```
.\New-WindowsServer2019VM.ps1 -Name Server01415077 -CPU 2 -Memory 4GB -Storage 40GB -SwitchName 'External Switch' -WindowsISO C:\Temp\17763.737.190906-2324.rs5_release_svc_refresh_SERVER_EVAL_x64FRE_en-us_1.iso -WindowsEdition 'Windows Server 2019 Datacenter Evaluation'
```

_A few moments later_

```
[415077964] - 02/01/2020 20:33:11 - Build Start
[415077964] - 02/01/2020 20:33:11 - Finding Answers
[415077964] - 02/01/2020 20:33:11 - Mixing Server01415077 with Windows Server 2019 Datacenter Evaluation
[415077964] - 02/01/2020 20:35:30 - Setting up Server01415077
[415077964] - 02/01/2020 20:35:30 - Enabling Ansible Management on Server01415077
[415077964] - 02/01/2020 20:35:43 - Installing Chocolatey on Server01415077
[415077964] - 02/01/2020 20:35:53 - Converting Windows Server Evaluation to Full
[415077964] - 02/01/2020 20:36:14 - Restarting Server01415077
[415077964] - 02/01/2020 20:37:18 - Setting AVMA Key on Server01415077
[415077964] - 02/01/2020 20:37:26 - Cleaning up Server01415077
[415077964] - 02/01/2020 20:37:46 - Restarting Server01415077
[415077964] - 02/01/2020 20:37:46 - Server01415077 is now ready
[415077964] - 02/01/2020 20:37:46 - Credentials: Administrator\p/!xPaw6lfIK{g3QLTc(h8S<
[415077964] - 02/01/2020 20:37:46 - Build End
[415077964] - 02/01/2020 20:37:46 - Completed in 4 Minutes
```

---

### Further Notes

* [1] Tested on NUC7i7BNH with NVMe Storage
* Microsoft [Virtualization-Documentation](https://github.com/MicrosoftDocs/Virtualization-Documentation)