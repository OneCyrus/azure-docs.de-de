---
title: "Übersicht über die Nachrichtenverarbeitungsarchitektur von Azure Service Bus | Microsoft-Dokumentation"
description: "Hier erfahren Sie mehr über die Nachrichtenverarbeitungsarchitektur von Azure Service Bus."
services: service-bus-messaging
documentationcenter: na
author: sethmanheim
manager: timlt
editor: 
ms.assetid: baf94c2d-0e58-4d5d-a588-767f996ccf7f
ms.service: service-bus-messaging
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/21/2017
ms.author: sethm
ms.openlocfilehash: c3bf541c14e6d869f77ca7d7a6e520bd3489fcad
ms.sourcegitcommit: 6f33adc568931edf91bfa96abbccf3719aa32041
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="service-bus-architecture"></a>Service Bus-Architektur

In diesem Artikel wird die Nachrichtenverarbeitungsarchitektur von [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) beschrieben.

## <a name="service-bus-scale-units"></a>Service Bus-Skalierungseinheiten

Service Bus ist nach *Skalierungseinheiten*strukturiert. Eine Skalierungseinheit ist eine Bereitstellungseinheit und umfasst alle Komponenten, die zum Ausführen des Diensts erforderlich sind. Jede Region stellt mindestens eine Service Bus-Skalierungseinheit bereit.

Ein Service Bus-Namespace wird einer Skalierungseinheit zugeordnet. Die Skalierungseinheit verarbeitet alle Arten von Service Bus-Entitäten (Warteschlangen, Themen, Abonnements). Eine Service Bus-Skalierungseinheit besteht aus folgenden Komponenten:

* **Eine Gruppe von Gatewayknoten.** Gatewayknoten authentifizieren eingehende Anforderungen. Jeder Gatewayknoten besitzt eine öffentliche IP-Adresse.
* **Eine Sammlung von Messagingbrokerknoten.** Messagingbrokerknoten verarbeiten Anforderungen, die Messagingentitäten betreffen.
* **Ein Gatewayspeicher.** Der Gatewayspeicher enthält die Daten für jede Entität, die in dieser Skalierungseinheit definiert ist. Der Implementierung des Gatewayspeichers liegt eine SQL-Datenbank-Instanz zugrunde.
* **Mehrere Messagingspeicher.** Die Messagingspeicher enthalten die Nachrichten aller Warteschlangen, Themen und Abonnements, die in dieser Skalierungseinheit definiert sind. Auch sämtliche Abonnementdaten sind darin enthalten. Eine Warteschlange oder ein Thema ist immer einem einzelnen Messagingspeicher zugeordnet, es sei denn, das [Partitionieren von Messagingentitäten](service-bus-partitioning.md) ist aktiviert. Abonnements werden im gleichen Messagingspeicher gespeichert wie ihr übergeordnetes Thema. Mit Ausnahme des [Premium-Messagings](service-bus-premium-messaging.md) von Service Bus werden die Messagingspeicher auf der Grundlage von [SQL-Datenbank](https://azure.microsoft.com/services/sql-database/)-Instanzen implementiert.

## <a name="containers"></a>Container

Jeder Messagingentität wird ein bestimmter Container zugewiesen. Ein Container ist ein logisches Konstrukt, für das ein Messagingspeicher verwendet wird, um alle relevanten Daten für diesen Container zu speichern. Jeder Container wird einem Messagingbrokerknoten zugewiesen. In der Regel übersteigt die Anzahl der Container die Anzahl der Messagingbrokerknoten. Daher lädt jeder Messagingbrokerknoten mehrere Container. Die Verteilung von Containern auf einen Messagingbrokerknoten wird so gestaltet, dass alle Messagingbrokerknoten gleichmäßig ausgelastet sind. Wenn sich die Auslastung verändert (beispielsweise, weil einer der Container besonders stark ausgelastet ist) oder ein Messagingbrokerknoten vorübergehend nicht verfügbar ist, wird die Verteilung der Container entsprechend angepasst.

## <a name="processing-of-incoming-messaging-requests"></a>Verarbeiten eingehender Messaginganforderungen

Wenn ein Client eine Anforderung an Service Bus sendet, wird diese vom Azure Load Balancer an einen der Gatewayknoten weitergeleitet. Der Gatewayknoten autorisiert die Anforderung. Wenn die Anforderung eine Messagingentität (Warteschlange, Thema, Abonnement) betrifft, sucht der Gatewayknoten die Entität im Gatewayspeicher und ermittelt den Messagingspeicher, in dem sich die Entität befindet. Anschließend wird der Messagingbrokerknoten ermittelt, der momentan für den Container zuständig ist, und die Anforderung wird an diesen Messagingbrokerknoten gesendet. Der Messagingbrokerknoten verarbeitet die Anforderung und aktualisiert den Entitätszustand im Containerspeicher. Anschließend sendet der Messagingbrokerknoten die Antwort an den Gatewayknoten zurück, der wiederum eine entsprechende Antwort an den Client sendet, von dem die ursprüngliche Anforderung stammte.

![Verarbeiten eingehender Messaginganforderungen](./media/service-bus-architecture/ic690644.png)

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie sich einen Überblick über die Service Bus-Architektur verschafft haben, finden Sie unter den folgenden Links weitere Informationen:

* [Übersicht über Service Bus-Messaging](service-bus-messaging-overview.md)
* [Service Bus – Grundlagen](service-bus-fundamentals-hybrid-solutions.md)
* [Erste Schritte mit Service Bus-Warteschlangen](service-bus-dotnet-get-started-with-queues.md)


