---
title: "Überschreiben des HTTP-Verhaltens mithilfe des Azure CDN-Regelmoduls | Microsoft-Dokumentation"
description: "Mit dem Regelmodul können Sie anpassen, wie HTTP-Anforderungen von Azure CDN behandelt werden, z.B. Sperren der Übermittlung bestimmter Inhaltstypen, Definieren einer Zwischenspeicherungsrichtlinie oder Ändern von HTTP-Headern."
services: cdn
documentationcenter: 
author: zhangmanling
manager: erikre
editor: 
ms.assetid: 625a912b-91f2-485d-8991-128cc194ee71
ms.service: cdn
ms.workload: tbd
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 01/23/2017
ms.author: mazha
ms.openlocfilehash: abfe283476206b181018d187675b47112dc5ad2f
ms.sourcegitcommit: 6699c77dcbd5f8a1a2f21fba3d0a0005ac9ed6b7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2017
---
# <a name="override-http-behavior-using-the-azure-cdn-rules-engine"></a>Überschreiben des HTTP-Verhaltens mithilfe des Azure CDN-Regelmoduls
[!INCLUDE [cdn-premium-feature](../../includes/cdn-premium-feature.md)]

## <a name="overview"></a>Übersicht
Mit dem Regelmodul können Sie anpassen, wie HTTP-Anforderungen behandelt werden, z. B. Sperren der Übermittlung bestimmter Inhaltstypen, Definieren einer Zwischenspeicherungsrichtlinie oder Ändern von HTTP-Headern.  In diesem Tutorial wird die Erstellung einer Regel erläutert, die das Zwischenspeicherungsverhalten von CDN-Assets ändert.  Im Abschnitt „[Siehe auch](#see-also)“ sind außerdem Videoinhalte verfügbar.

   > [!TIP] 
   > Eine ausführliche Referenz der Syntax finden Sie unter [Regelmodul – Referenz](cdn-rules-engine-reference.md).
   > 


## <a name="tutorial"></a>Lernprogramm:
1. Klicken Sie auf dem Blatt „CDN-Profil“ auf die Schaltfläche **Verwalten** .
   
    ![Schaltfläche „Verwalten“ auf dem CDN-Profilblatt](./media/cdn-rules-engine/cdn-manage-btn.png)
   
    Das CDN-Verwaltungsportal wird geöffnet.
2. Klicken Sie auf die Registerkarte **HTTP Large** und dann auf **Regelmodul**.
   
    Die Optionen für eine neue Regel werden angezeigt.
   
    ![Optionen für neue CDN-Regeln](./media/cdn-rules-engine/cdn-new-rule.png)
   
   > [!IMPORTANT]
   > Die Reihenfolge, in der mehrere Regeln aufgelistet sind, beeinflusst deren Verarbeitung. Eine Regel kann die von einer vorherigen Regel angegebenen Aktionen überschreiben.
   > 
   > 
3. Geben Sie einen Namen in das Textfeld **Name/Beschreibung** ein.
4. Ermitteln Sie die Anforderungstypen, auf die die Regel angewendet wird.  In der Standardeinstellung ist die Übereinstimmungsbedingung **Immer** ausgewählt.  Für dieses Tutorial verwenden Sie **Immer** , lassen Sie die Option also ausgewählt.
   
   ![CDN-Übereinstimmungsbedingung](./media/cdn-rules-engine/cdn-request-type.png)
   
   > [!TIP]
   > In der Dropdownliste sind viele Typen von Übereinstimmungsbedingungen verfügbar.  Durch Klicken auf das blaue Informationssymbol links neben der Übereinstimmungsbedingung wird die derzeit ausgewählte Bedingung ausführlicher erläutert.
   > 
   >  Eine vollständige Liste der bedingten Ausdrücke finden Sie unter [Regelmodul – Bedingte Ausdrücke](cdn-rules-engine-reference-match-conditions.md).
   >  
   > Eine vollständige Liste der Übereinstimmungsbedingungen finden Sie unter [Regelmodul – Übereinstimmungsbedingungen](cdn-rules-engine-reference-match-conditions.md).
   > 
   > 
5. Klicken Sie auf die Schaltfläche **+** neben **Features**, um ein neues Feature hinzuzufügen.  Wählen Sie in der Dropdownliste auf der linken Seite **Force Internal Max-Age**aus.  Geben Sie **300**in das angezeigte Textfeld ein.  Belassen Sie die übrigen Werte in ihrer Standardeinstellung.
   
   ![CDN-Feature](./media/cdn-rules-engine/cdn-new-feature.png)
   
   > [!NOTE]
   > Wie bei den Übereinstimmungsbedingungen können Sie durch Klicken auf das blaue Informationssymbol links neben dem neuen Feature Informationen zu diesem anzeigen lassen.  Im Fall von **Force Internal Max-Age** überschreiben wir die Header **Cache-Control** und **Expires** des Assets, um zu steuern, wann der CDN-Edgeknoten das Asset aus dem Ursprung aktualisiert.  Unser Beispiel von 300 Sekunden gibt an, dass der CDN-Edgeknoten das Asset für 5 Minuten zwischenspeichert, bevor es aus seinem Ursprung aktualisiert wird.
   > 
   > Eine vollständige Liste der Features finden Sie unter [Regelmodul – Featuredetails](cdn-rules-engine-reference-features.md).
   > 
   > 
6. Klicken Sie auf die Schaltfläche **Hinzufügen** , um die neue Regel zu speichern.  Die neue Regel wartet jetzt auf ihre Genehmigung. Sobald sie genehmigt wurde, wird der Status von **Pending XML** in **Active XML** geändert.
   
   > [!IMPORTANT]
   > Es kann bis zu 90 Minuten dauern, Regeländerungen über das CDN weiterzugeben.
   > 
   > 

## <a name="see-also"></a>Siehe auch
* [Übersicht über das Azure CDN](cdn-overview.md)
* [Regelmodul – Referenz](cdn-rules-engine-reference.md)
* [Regelmodul – Übereinstimmungsbedingungen](cdn-rules-engine-reference-match-conditions.md)
* [Regelmodul – Bedingte Ausdrücke](cdn-rules-engine-reference-conditional-expressions.md)
* [Regelmodul – Features](cdn-rules-engine-reference-features.md)
* [Überschreiben des HTTP-Standardverhaltens mithilfe des Regelmoduls](cdn-rules-engine.md)
* [Azure Friday: Azure CDN's powerful new Premium Features](https://azure.microsoft.com/documentation/videos/azure-cdns-powerful-new-premium-features/) (Die leistungsstarken neuen Premium-Features von Azure CDN) (Video)