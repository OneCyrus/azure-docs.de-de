---
title: "Azure Event Grid – Übermittlung und Wiederholung"
description: "Beschreibt, wie Azure Event Grid Ereignisse übermittelt und wie nicht übermittelte Nachrichten verarbeitet werden."
services: event-grid
author: tfitzmac
manager: timlt
ms.service: event-grid
ms.topic: article
ms.date: 01/30/2018
ms.author: tomfitz
ms.openlocfilehash: cdf6a4e999d55196e8f4eac5695163a7e5a933de
ms.sourcegitcommit: 9d317dabf4a5cca13308c50a10349af0e72e1b7e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="event-grid-message-delivery-and-retry"></a>Event Grid – Übermittlung und Wiederholung von Nachrichten 

In diesem Artikel wird beschrieben, wie Azure Event Grid Ereignisse verarbeitet, wenn die Übermittlung nicht bestätigt wird.

Event Grid bietet permanente Übermittlung. Jede Nachricht wird für jedes Abonnement mindestens einmal übermittelt. Ereignisse werden sofort an den registrierten Webhook des jeweiligen Abonnements gesendet. Wenn ein Webhook den Eingang eines Ereignisses nicht innerhalb von 60 Sekunden nach dem ersten Übermittlungsversuch bestätigt, wiederholt Event Grid die Übermittlung des Ereignisses.

## <a name="message-delivery-status"></a>Nachrichtenübermittlungsstatus

Event Grid verwendet HTTP-Antwortcodes zum Bestätigen des Eingangs von Ereignissen. 

### <a name="success-codes"></a>Erfolgscodes

Die folgenden HTTP-Antwortcodes geben an, dass ein Ereignis erfolgreich an den Webhook übermittelt wurde. Die Übermittlung gilt dann in Event Grid als abgeschlossen.

- 200 – OK
- 202 – Akzeptiert

### <a name="failure-codes"></a>Fehlercodes

Die folgenden HTTP-Antwortcodes geben an, dass bei der Übermittlung eines Ereignisses ein Fehler aufgetreten ist. Event Grid versucht erneut, das Ereignis zu senden. 

- 400 – Ungültige Anforderung
- 401 – Nicht autorisiert
- 404 – Nicht gefunden
- 408 – Anforderungstimeout
- 414 – URI zu lang
- 500 Interner Serverfehler
- 503 Dienst nicht verfügbar
- 504 Gateway-Timeout

Alle anderen Antwortcodes oder eine fehlende Antwort geben einen Fehler an. Event Grid wiederholt die Übermittlung. 

## <a name="retry-intervals"></a>Wiederholungsintervalle

Event Grid verwendet exponentiell ansteigende Wartezeiten für Wiederholungsversuche für die Ereignisübermittlung. Wenn der Webhook nicht antwortet oder einen Fehlercode zurückgibt, wiederholt Event Grid die Übermittlung nach folgendem Zeitplan:

1. 10 Sekunden
2. 30 Sekunden
3. 1 Minute
4. 5 Minuten
5. 10 Minuten
6. 30 Minuten
7. 1 Stunde

Event Grid fügt allen Wiederholungsintervallen eine geringfügige zufällige Anordnung hinzu. Nach einer Stunde wird die Ereignisübermittlung erneut versucht. Der Versuch wird jede Stunde wiederholt.

## <a name="retry-duration"></a>Wiederholungszeitraum

Azure Event Grid markiert alle Ereignisse als abgelaufen, die nicht innerhalb von 24 Stunden übermittelt werden.

## <a name="next-steps"></a>Nächste Schritte

* Informationen zum Anzeigen des Status von Ereignisübermittlungen finden Sie unter [Überwachen der Event Grid-Nachrichtenübermittlung](monitor-event-delivery.md).
* Eine Einführung in Event Grid finden Sie unter [Informationen zu Event Grid](overview.md).
* Um sich schnell mit der Verwendung von Event Grid vertraut zu machen, lesen Sie [Erstellen und Weiterleiten benutzerdefinierter Ereignisse mit Azure Event Grid](custom-event-quickstart.md).