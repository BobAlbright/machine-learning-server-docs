---
# required metadata
title: "Windows command line installation for Machine Learning Server "
description: "How to install Machine Learning Server for Windows on the command line."
keywords: ""
author: "HeidiSteen"
ms.author: "heidist"
manager: "cgronlun"
ms.date: "02/16/2018"
ms.topic: "article"
ms.prod: "mlserver"

# optional metadata
#ROBOTS: ""
#audience: ""
#ms.devlang: ""
#ms.reviewer: ""
#ms.suite: ""
#ms.tgt_pltfrm: ""
#ms.technology: ""
#ms.custom: ""

---

# Command line install for Machine Learning Server for Windows

**Applies to:  Machine Learning Server 9.2.1 | 9.3**

This article provides syntax and examples for running Machine Learning Server **ServerSetup.exe** from the command line. You can use command line parameters for an internet-connected or offline installation. A command line installation requires administrator permissions.

Before you start, review  [Install Machine Learning Server on Windows](machine-learning-server-windows-install.md) for:

+ System and operational requirements
+ Download and file extraction information
+ A summary of what is installed
+ Steps for validating your installation

This article assumes you have already downloaded and extracted the setup program.

## Command line options

You can run ServerSetup.exe from the command line with options to expose or hide the wizard, set an install mode, or specify options for adding features or using custom folder locations.

**User Interaction Options**

| Parameter | Description |
|-----------|-------------|
| `/full` | Invokes the wizard. |
| `/quiet` | Hides the wizard, running a silent installation with no interaction or prompts. EULA acceptance is automatic for both the server and all open-source distributions of R and Python. |
| `/passive` | Equivalent to `/quiet` in this release. |

 
**Install Modes**

| Parameter | Description |
|-----------|-------------|
| `/install` | Runs ServerSetup.exe in install mode, used to add R_SERVER, PYTHON_SERVER, or the [pre-trained machine learning models](microsoftml-install-pretrained-models.md)|
| `/uninstall` | Removes an existing installation of any component previously installed. |
| `/modify` | Runs ServerSetup.exe in modify mode. Setup looks for an existing installation and offers options for changing an installation (for example, you could add the pre-trained models). Use this option if you want to rerun (or repair) an installation. |

 
**Install Options**

| Parameter | Description |
|-----------|-------------|
| `/offline` | Instructs setup to find [.cab files](#cab-files) on the local system in the `mediadir` location. This option requires that the server is disconnected from the internet.|
| `/installdir=""` | Specifies the installation directory. By default, this is C:\Program Files\Microsoft\R Server\R_SERVER. |
| `/cachedir=""` | A download location for the .cab files. By default, setup uses `%temp%` for the local admin user. Assuming an online installation scenario, you can set this parameter to have setup download the .cabs to the folder you specify. |
| `/mediadir=""` | The .cab file location setup uses to find .cab files in an offline installation. By default, setup uses `%temp%` for local admin. |
| `/models` | Adds the [pre-trained machine learning models](microsoftml-install-pretrained-models.md). Use with `/install`.|


## Default installation

A default installation includes R and Python, but not the pre-trained models. You must explicitly add `/models` to an installation to add this feature.

The command line equivalent of a double-click invocation of ServerSetup.exe is `serversetup.exe /install /full`.

## Examples

1. Run setup in unattended mode with no prompts or user interaction, to install everything. R Server is implicit. It does not have a parameter to explicitly include or exclude it. Arguments exist for Python and the pre-trained models.

   `serversetup.exe /quiet /models`

2. Add the [pre-trained machine learning models](microsoftml-install-pretrained-models.md) to an existing installation. You cannot install them as a standalone component. The models require R or Python. During installation, the pre-trained models are inserted into the MicrosoftML (R) and microsoftml (Python) libraries, or both if you add both languages. Once installed, you cannot incrementally remove them. Removal will require uninstall and reinstall of Python or R Server. 

   `serversetup.exe /install /models`

3. Uninstall the software in unattended mode.

  `serversetup.exe /quiet /uninstall`  

4. Offline install requires .cab files that provide open-source distributions and other dependencies. The `/offline` parameter instructs setup to look for the .cab files on the local system. By default, setup looks for the .cab files in the `%temp%` directory of local admin, but you could also set the media directory if the .cab files are in a different folder. For more information and .cab download links, see [Offline installation](machine-learning-server-windows-offline.md).

  `rserversetup.exe /offline /mediadir="D:/Public/CABS` 

<a name="cab-files"></a>

### CAB files for offline installation

| Component | Download | Used for | 
|-----------|----------|----------|
|NameForMLM |[MLM_9.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=852727) | Pre-trained models, R or Python |
|Microsoft R Open |[SRO_3.4.4.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=852724) | R |
|Microsoft Python Open |[SPO_9.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=852723) | Python |
|Microsoft Python Server |[SPS_9.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=852726) | Python |

## Next steps

We recommend continuing with any Quickstart tutorial listed in the contents pane. 

## See also

+ [Install Machine Learning Server](r-server-install.md)
+ [What's new in Machine Learning Server](../whats-new-in-machine-learning-server.md)
+ [Supported platforms](r-server-install-supported-platforms.md)  
+ [Known Issues](../resources-known-issues.md)  
+ [Configure Machine Learning Server to operationalize your analytics](../what-is-operationalization.md)