---
title: Herunterladen von Azure Stack-Tools von GitHub | Microsoft-Dokumentation
description: "Erfahren Sie, wie Sie Tools herunterladen, die für die Arbeit mit Azure Stack benötigt werden."
services: azure-stack
documentationcenter: 
author: mattbriggs
manager: femila
editor: 
ms.assetid: 28F360AD-789A-488D-965F-FC6E6CCF3329
ms.service: azure-stack
ms.workload: na
pms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/10/2017
ms.author: mabrigg
ms.openlocfilehash: d4f8a8d73f8e2ea321cb6cc1deda2301033b249d
ms.sourcegitcommit: a5f16c1e2e0573204581c072cf7d237745ff98dc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2017
---
# <a name="download-azure-stack-tools-from-github"></a>Herunterladen von Azure Stack-Tools von GitHub

„AzureStack-Tools“ ist ein GitHub-Repository, das PowerShell-Module hostet, die Sie zum Verwalten und Bereitstellen von Ressourcen für Azure Stack verwenden können. Sie können diese PowerShell-Module in das Azure Stack Development Kit oder in einen Windows-basierten externen Client herunterladen und verwenden, wenn Sie planen, die VPN-Konnektivität einzurichten. Um diese Tools zu erhalten, klonen Sie das GitHub-Repository, oder laden Sie den Ordner „AzureStack-Tools“ herunter. Führen Sie dazu das folgende Skript aus:

```PowerShell
# Change directory to the root directory 
cd \

# Download the tools archive
invoke-webrequest `
  https://github.com/Azure/AzureStack-Tools/archive/master.zip `
  -OutFile master.zip

# Expand the downloaded files
expand-archive master.zip `
  -DestinationPath . `
  -Force

# Change to the tools directory
cd AzureStack-Tools-master

```

## <a name="functionalities-provided-by-the-modules"></a>Von den Modulen bereitgestellte Funktionen

Das Repository „AzureStack-Tools“ umfasst PowerShell-Module, die die folgenden Funktionen für Azure Stack unterstützen:  

| Funktionalität | Beschreibung | Wer kann dieses Modul verwenden? |
| --- | --- | --- |
| [Cloudfunktionen](azure-stack-validate-templates.md) | Verwenden Sie dieses Modul, um die Cloudfunktionen einer Cloud zu nutzen. Beispielsweise können Sie mithilfe dieses Moduls Cloudfunktionen für Azure Stack und Azure-Clouds nutzen. Zu diesen Funktionen zählen z.B. die API-Version, Azure Resource Manager-Ressourcen, VM-Erweiterungen usw. | Cloudadministratoren und -benutzer. |
| [Resource Manager-Richtlinie für Azure Stack](azure-stack-policy-module.md) | Verwenden Sie dieses Modul zum Konfigurieren eines Azure-Abonnements oder einer Azure-Ressourcengruppe mit der gleichen Versionsverwaltung und Dienstverfügbarkeit wie Azure Stack. | Cloudadministratoren und -benutzer |
| [Herstellen einer Verbindung mit Azure Stack](azure-stack-connect-azure-stack.md) | Verwenden Sie dieses Modul zum Herstellen einer Verbindung mit einer Azure Stack-Instanz über PowerShell und zum Konfigurieren der VPN-Konnektivität mit Azure Stack. | Cloudadministratoren und -benutzer |
| [Validierungssteuerelement für Vorlagen](azure-stack-validate-templates.md) | Verwenden Sie dieses Modul, um zu überprüfen, ob eine vorhandene oder eine neue Vorlage für Azure Stack bereitgestellt werden kann. | Cloudadministratoren und -benutzer |


## <a name="next-steps"></a>Nächste Schritte
* [Konfigurieren der PowerShell-Umgebung des Azure Stack-Benutzers](azure-stack-powershell-configure-user.md)   
* [Connect to Azure Stack Development Kit over a VPN (Herstellen einer Verbindung mit dem Azure Stack Development Kit über VPN)](azure-stack-connect-azure-stack.md)  
