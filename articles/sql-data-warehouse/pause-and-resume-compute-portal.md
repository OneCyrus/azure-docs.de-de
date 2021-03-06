---
title: "Schnellstart: Anhalten und Fortsetzen von Computeressourcen in Azure SQL Data Warehouse – Azure-Portal | Microsoft-Dokumentation"
description: "Erfahren Sie, wie Sie über Azure-Portalaufgaben Computeressourcen für ein Azure SQL Data Warehouse anhalten, um Kosten einzusparen. Setzen Sie die Computeressourcen fort, wenn Sie das Data Warehouse verwenden möchten."
services: sql-data-warehouse
documentationcenter: NA
author: barbkess
manager: jhubbard
editor: 
ms.service: sql-data-warehouse
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: data-services
ms.custom: manage
ms.date: 01/23/2018
ms.author: barbkess
ms.openlocfilehash: f8b4e29595c6a71696cf2c4939ad4c6c096a28b5
ms.sourcegitcommit: 9d317dabf4a5cca13308c50a10349af0e72e1b7e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="quickstart-pause-and-resume-compute-for-an-azure-sql-data-warehouse-in-the-azure-portal"></a>Schnellstart: Anhalten und Fortsetzen von Computeressourcen für ein Azure SQL Data Warehouse im Azure-Portal
Halten Sie Computeressourcen für ein Azure SQL Data Warehouse an, um Kosten zu sparen. Setzen Sie die Computeressourcen fort, wenn Sie das Data Warehouse verwenden möchten.

Wenn Sie kein Azure-Abonnement besitzen, können Sie ein [kostenloses Konto](https://azure.microsoft.com/free/) erstellen, bevor Sie beginnen.

## <a name="sign-in-to-the-azure-portal"></a>Melden Sie sich auf dem Azure-Portal an.

Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an.

## <a name="before-you-begin"></a>Voraussetzungen

Verwenden Sie [Erstellen und Verbinden – Portal](create-data-warehouse-portal.md), um ein Data Warehouse namens **mySampleDataWarehouse** zu erstellen. 

## <a name="pause-compute"></a>Anhalten von Computeressourcen
Um Kosten zu sparen, können Sie Computeressourcen bei Bedarf anhalten und fortsetzen. Wenn Sie die Datenbank z.B. nachts oder am Wochenende nicht verwenden, können Sie sie während dieser Zeiträume anhalten und während des Tages wieder fortsetzen. Computeressourcen werden Ihnen nicht in Rechnung gestellt, während die Datenbank angehalten ist. Allerdings wird Ihnen der Speicherplatz weiter in Rechnung gestellt. 

Führen Sie die folgenden Schritte aus, um ein SQL Data Warehouse anzuhalten.

1. Klicken Sie auf der linken Seite im Azure-Portal auf **SQL-Datenbanken**.
2. Wählen Sie auf der Seite **SQL-Datenbanken** den Eintrag **mySampleDataWarehouse** aus. Hierdurch wird das Data Warehouse geöffnet. 
3. Beachten Sie, dass auf der Seite **mySampleDataWarehouse** für **Status** der Wert **Online** angezeigt wird.

    ![Computerressourcen online](media/pause-and-resume-compute-portal/compute-online.png)

4. Um das Data Warehouse anzuhalten, klicken Sie auf die Schaltfläche **Anhalten**. 
5. Sie werden in einer Meldung aufgefordert, das Fortsetzen des Vorgangs zu bestätigen. Klicken Sie auf **Ja**.
6. Warten Sie einen Moment, und beachten Sie, dass der **Status** als **Wird angehalten** angezeigt wird.

    ![Status „Wird angehalten“](media/pause-and-resume-compute-portal/pausing.png)

7. Wenn der Anhaltevorgang abgeschlossen wurde, wechselt der Status in den Wert **Angehalten**, und die Bezeichnung der Optionsschaltfläche lautet **Starten**.
8. Die Computeressourcen für das Data Warehouse sind jetzt offline. Ihnen werden erst wieder Computeressourcen in Rechnung gestellt, wenn Sie den Dienst fortsetzen.

    ![Computeressourcen offline](media/pause-and-resume-compute-portal/compute-offline.png)


## <a name="resume-compute"></a>Fortsetzen von Computeressourcen
Führen Sie die folgenden Schritte aus, um ein SQL Data Warehouse fortzusetzen.

1. Klicken Sie auf der linken Seite im Azure-Portal auf **SQL-Datenbanken**.
2. Wählen Sie auf der Seite **SQL-Datenbanken** den Eintrag **mySampleDataWarehouse** aus. Hierdurch wird das Data Warehouse geöffnet. 
3. Beachten Sie, dass auf der Seite **mySampleDataWarehouse** für **Status** der Wert **Angehalten** angezeigt wird.

    ![Computeressourcen offline](media/pause-and-resume-compute-portal/compute-offline.png)

4. Klicken Sie auf **Starten**, um das Data Warehouse fortzusetzen. 
5. Sie werden in einer Meldung aufgefordert, den Startvorgang zu bestätigen. Klicken Sie auf **Ja**.
6. Beachten Sie, dass der **Status** als **Wird fortgesetzt** angezeigt wird.

    ![Status „Wird fortgesetzt“](media/pause-and-resume-compute-portal/resuming.png)

7. Wenn das Data Warehouse wieder online ist, lautet der Status **Online**, und die Bezeichnung der Optionsschaltfläche lautet **Anhalten**.
8. Die Computeressourcen für das Data Warehouse sind jetzt online, und Sie können den Dienst verwenden. Es fallen wieder Kosten für die Computeressourcen an.

    ![Computerressourcen online](media/pause-and-resume-compute-portal/compute-online.png)

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Ihnen werden Gebühren für Ihre Data Warehouse-Einheiten und die in Ihrem Data Warehouse gespeicherte Daten in Rechnung gestellt. Diese Compute- und Speicherressourcen werden separat in Rechnung gestellt. 

- Wenn Sie die Daten im Speicher beibehalten möchten, halten Sie die Computeressourcen an.
- Wenn zukünftig keine Gebühren anfallen sollen, können Sie das Data Warehouse löschen. 

Führen Sie die folgenden Schritte aus, um Ressourcen nach Wunsch zu bereinigen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an, und klicken Sie auf Ihr Data Warehouse.

    ![Bereinigen von Ressourcen](media/load-data-from-azure-blob-storage-using-polybase/clean-up-resources.png)

1. Zum Anhalten von Computeressourcen klicken Sie auf die Schaltfläche **Anhalten**. Wenn das Data Warehouse angehalten ist, wird die Schaltfläche **Starten** angezeigt.  Klicken Sie zum Fortsetzen der Computeressourcen auf **Starten**.

2. Wenn Sie das Data Warehouse entfernen möchten, damit keine Gebühren für Compute- oder Speicherressourcen anfallen, klicken Sie auf **Löschen**.

3. Um die erstellte SQL Server-Instanz zu entfernen, klicken Sie auf **mynewserver-20171113.database.windows.net** und anschließend auf **Löschen**.  Seien Sie bei diesem Löschvorgang vorsichtig, da beim Löschen des Servers auch alle Datenbanken gelöscht werden, die dem Server zugewiesen sind.

4. Zum Entfernen der Ressourcengruppe klicken Sie auf **myResourceGroup**, und klicken Sie dann auf **Ressourcengruppe löschen**.


## <a name="next-steps"></a>Nächste Schritte
Sie haben die Computeressourcen für Ihr Data Warehouse angehalten und fortgesetzt. Weitere Informationen zu Azure SQL Data Warehouse erhalten Sie im Tutorial zum Laden von Daten.

> [!div class="nextstepaction"]
>[Laden von Daten in ein SQL Data Warehouse](load-data-from-azure-blob-storage-using-polybase.md)
