---
title: Konfigurieren eines Azure-Clouddienstprojekts mit Visual Studio | Microsoft-Dokumentation
description: "In diesem Artikel erfahren Sie, wie Sie ein Azure-Clouddienstprojekt abhängig von den Anforderungen für dieses Projekt in Visual Studio konfigurieren."
services: visual-studio-online
documentationcenter: na
author: kraigb
manager: ghogen
editor: 
ms.assetid: 609d6965-05cc-47b1-82dc-c76a92d4f295
ms.service: multiple
ms.devlang: dotnet
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: multiple
ms.date: 03/06/2017
ms.author: kraigb
ms.openlocfilehash: 799715093bd1a8c8e77e6cdb7168670dc263dfa5
ms.sourcegitcommit: 6699c77dcbd5f8a1a2f21fba3d0a0005ac9ed6b7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2017
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Konfigurieren eines Azure-Clouddienstprojekts mit Visual Studio
Sie können ein Azure-Clouddienstprojekt abhängig von den Anforderungen für dieses Projekt konfigurieren. Sie können für die folgenden Kategorien Eigenschaften für das Projekt festlegen:

- **Veröffentlichen eines Clouddiensts in Azure**: Sie können eine Eigenschaft festlegen, um sicherzustellen, dass ein bereits in Azure bereitgestellter Clouddienst nicht versehentlich gelöscht wird.
- **Ausführen oder Debuggen eines Clouddiensts auf dem lokalen Computer**: Sie können die zu verwendende Dienstkonfiguration auswählen und angeben, ob der Azure-Speicheremulator gestartet werden soll.
- **Überprüfen eines Clouddienstpakets bei der Erstellung**: Sie können festlegen, dass alle Warnungen als Fehler behandelt werden, um zu gewährleisten, dass sich das Clouddienstpaket ohne Probleme bereitstellen lässt. 

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Schritte zum Konfigurieren eines Azure-Clouddienstprojekts
1. Öffnen oder Erstellen eines Clouddienstprojekts in Visual Studio

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie im Kontextmenü die Option **Eigenschaften** aus.
   
1. Wählen Sie auf der Eigenschaftenseite des Projekts die Registerkarte **Entwicklung** aus.

    ![Menü „Projekteigenschaften“](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. Legen Sie **Eingabeaufforderung vor dem Löschen einer vorhandenen Bereitstellung** auf **True** fest. Mit dieser Einstellung können Sie gewährleisten, dass eine vorhandene Bereitstellung in Azure nicht versehentlich gelöscht wird.

1. Wählen Sie die gewünschte **Dienstkonfiguration** aus, die beim lokalen Ausführen oder Debuggen des Clouddiensts verwendet werden soll. Weitere Informationen zum Ändern einer Dienstkonfiguration für eine Rolle finden Sie unter [Konfigurieren der Rollen für einen Azure-Clouddienst mit Visual Studio](./vs-azure-tools-configure-roles-for-cloud-service.md).

1. Legen Sie die Einstellung **Azure-Speicheremulator starten** auf **True** fest, um beim lokalen Ausführen oder Debuggen Ihres Clouddiensts den Azure-Speicheremulator zu starten.

1. Um sicherzustellen, dass bei Paketvalidierungsfehlern keine Veröffentlichung möglich ist, legen Sie **Warnungen als Fehler behandeln** als **True** fest.

1. Legen Sie **Webprojektports verwenden** auf **True** fest, um sicherzustellen, dass die Webrolle bei jedem lokalen Start in IIS Express den gleichen Port verwendet.

1. Wählen Sie auf der Symbolleiste von Visual Studio **Speichern** aus.

## <a name="next-steps"></a>Nächste Schritte
- [Konfigurieren eines Azure-Projekts mit mehreren Dienstkonfigurationen](vs-azure-tools-multiple-services-project-configurations.md)

