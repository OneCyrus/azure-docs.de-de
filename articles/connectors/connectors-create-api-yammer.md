---
title: "Hinzufügen des Yammer-Connectors zu Ihren Azure-Logik-Apps | Microsoft-Dokumentation"
description: "Übersicht über den Yammer-Connector mit REST-API-Parametern"
services: logic-apps
documentationcenter: 
author: MandiOhlinger
manager: anneta
editor: 
tags: connectors
ms.assetid: b5ae0827-fbb3-45ec-8f45-ad1cc2e7eccc
ms.service: logic-apps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/18/2016
ms.author: mandia; ladocs
ms.openlocfilehash: 37f72d829fc50a0f967f08e068c553f5026f35eb
ms.sourcegitcommit: be9a42d7b321304d9a33786ed8e2b9b972a5977e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/19/2018
---
# <a name="get-started-with-the-yammer-connector"></a>Erste Schritte mit dem Yammer-Connector
Verbinden Sie sich mit Yammer, um auf Konversationen in Ihrem Unternehmensnetzwerk zuzugreifen. Yammer ermöglicht Folgendes:

* Erstellen eines Geschäftsworkflows basierend auf den Daten, die aus Yammer abgerufen werden. 
* Verwenden von Triggern, wenn es eine neue Nachricht in einer Gruppe oder in einem Feed gibt, dem Sie folgen.
* Verwenden Sie Aktionen, um z. : eine Nachricht senden oder alle Nachrichten abzurufen. Diese Aktionen erhalten eine Antwort und stellen anschließend die Ausgabe anderen Aktionen zur Verfügung. Wenn z. B. eine neue Nachricht vorhanden ist, können Sie über Office 365 eine E-Mail senden.

Erstellen Sie zunächst eine Logik-App, wie unter [Erstellen einer Logik-App](../logic-apps/quickstart-create-first-logic-app-workflow.md) beschrieben.

## <a name="create-a-connection-to-yammer"></a>Herstellen einer Verbindung mit Yammer
Stellen Sie zum Verwenden des Yammer-Connectors zunächst eine **Verbindung** her, und geben Sie anschließend die Details für diese Eigenschaften an: 

| Eigenschaft | Erforderlich | BESCHREIBUNG |
| --- | --- | --- |
| Tokenverschlüsselung |Ja |Angeben der Yammer-Anmeldeinformationen |

> [!INCLUDE [Steps to create a connection to Yammer](../../includes/connectors-create-api-yammer.md)]
> 

## <a name="connector-specific-details"></a>Connectorspezifische Details

Zeigen Sie die in Swagger definierten Trigger und Aktionen sowie mögliche Beschränkungen in den [Connectordetails](/connectors/yammer/) an.

## <a name="more-connectors"></a>Weitere Connectors
Gehen Sie zur [Liste der APIs](apis-list.md)zurück.