---
title: Verwalten von Azure Cosmos DB in Azure Storage-Explorer
description: Erfahren Sie, wie Sie Azure Cosmos DB in Azure Storage-Explorer verwalten.
Keywords: Azure Cosmos DB, Azure Storage Explorer, MongoDB
services: cosmos-db
documentationcenter: 
author: jejiang
manager: omafnan
editor: 
tags: Azure Cosmos DB
ms.assetid: 
ms.service: cosmos-db
ms.custom: Azure Cosmos DB active
ms.workload: big-data
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: tutorial
ms.date: 09/19/2017
ms.author: Jejiang
ms.openlocfilehash: baa7eee614159f9c6af493aff74b27773471f7d7
ms.sourcegitcommit: 5ac112c0950d406251551d5fd66806dc22a63b01
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="manage-azure-cosmos-db-in-azure-storage-explorer-preview"></a>Verwalten von Azure Cosmos DB in Azure Storage-Explorer (Vorschau)

Mit der Verwendung von Azure Cosmos DB in Azure Storage-Explorer können Benutzer Azure Cosmos DB-Entitäten verwalten, Daten bearbeiten und gespeicherte Prozeduren und Trigger zusammen mit anderen Azure-Entitäten wie Speicherblobs und Warteschlangen aktualisieren. Nun können Sie mit demselben Tool Ihre verschiedenen Azure-Entitäten an einem Ort verwalten. Derzeit unterstützt Azure Storage-Explorer SQL-<!--and MongoDB-->-Konten. Azure Storage-Explorer kann nicht in Kombination mit dem lokalen Azure Cosmos DB-Emulator verwendet werden. 

In diesem Artikel erfahren Sie, wie Sie Storage-Explorer zum Verwalten von Azure Cosmos DB verwenden.


## <a name="prerequisites"></a>Voraussetzungen

Ein Azure Cosmos DB-Konto für die SQL-API <!--or MongoDB API-->. Wenn Sie kein Konto besitzen, können Sie im Azure-Portal ein Konto erstellen, wie unter [Azure Cosmos DB: Erstellen einer SQL-API-Web-App mit .NET und dem Azure-Portal](create-sql-api-dotnet.md) beschrieben.

## <a name="installation"></a>Installation

Hier können Sie die neuesten Komponenten von Azure-Speicher-Explorer installieren: [Azure-Speicher-Explorer](https://azure.microsoft.com/features/storage-explorer/). Nun werden Versionen für Windows, Linux und MAC unterstützt.

## <a name="connect-to-an-azure-subscription"></a>Herstellen einer Verbindung mit einem Azure-Abonnement

1. Klicken Sie nach dem Installieren von **Azure Storage-Explorer** auf das Symbol **Plug-In** auf der linken Seite, wie in der folgenden Abbildung dargestellt.
       
   ![Plug-In-Symbol](./media/storage-explorer/plug-in-icon.png)
 
2. Wählen Sie **Azure-Konto hinzufügen** aus, und klicken Sie dann auf **Anmelden**.

   ![Herstellen einer Verbindung mit einem Azure-Abonnement](./media/storage-explorer/connect-to-azure-subscription.png)

2. Wählen Sie im Dialogfeld **Azure-Anmeldung** die Option **Anmelden** aus, und geben Sie Ihre Azure-Anmeldeinformationen ein.

    ![Anmelden](./media/storage-explorer/sign-in.png)

3. Wählen Sie Ihr Abonnement in der Liste aus, und klicken Sie dann auf **Anwenden**.

    ![Anwenden](./media/storage-explorer/apply-subscription.png)

    Der Explorer-Bereich wird aktualisiert und zeigt die Konten im ausgewählten Abonnement an.

    ![Kontoliste](./media/storage-explorer/account-list.png)

    Sie haben nun Ihr **Azure Cosmos DB-Konto** mit Ihrem Azure-Abonnement verbunden.

## <a name="connect-to-azure-cosmos-db-by-using-a-connection-string"></a>Herstellen einer Verbindung mit Azure Cosmos DB mithilfe einer Verbindungszeichenfolge

Eine alternative Möglichkeit zum Herstellen einer Verbindung mit einer Azure Cosmos DB ist die Verwendung einer Verbindungszeichenfolge. Gehen Sie folgendermaßen vor, um eine Verbindung mithilfe einer Verbindungszeichenfolge herzustellen.

1. Suchen Sie in der linken Struktur nach **Lokal und angefügt**, klicken Sie mit der rechten Maustaste auf **Azure Cosmos DB-Konten**, und wählen Sie **Mit Azure-Cosmos-Datenbank verbinden** aus.

    ![Herstellen einer Verbindung mit Azure Cosmos DB mithilfe einer Verbindungszeichenfolge](./media/storage-explorer/connect-to-db-by-connection-string.png)

2. Wählen Sie die passende **Standardoberfläche** für Ihren Kontotyp aus, <!--either--> **DocumentDB** <!--or **MongoDB**-->. Fügen Sie Ihre **Verbindungszeichenfolge** ein, und klicken Sie dann auf **OK**, um eine Verbindung mit dem Azure Cosmos DB-Konto herzustellen. Informationen zum Abrufen der Verbindungszeichenfolge finden Sie unter [Abrufen der Verbindungszeichenfolge](https://docs.microsoft.com/azure/cosmos-db/manage-account#get-the--connection-string).

    ![Verbindungszeichenfolge](./media/storage-explorer/connection-string.png)

## <a name="azure-cosmos-db-resource-management"></a>Azure Cosmos DB-Ressourcenverwaltung

Sie können ein Azure Cosmos DB-Konto über die folgenden Vorgänge verwalten:
* Öffnen des Kontos im Azure-Portal
* Hinzufügen der Ressource zur Schnellzugriffsliste
* Suchen und Aktualisieren von Ressourcen
* Erstellen und Löschen von Datenbanken
* Erstellen und Löschen von Sammlungen
* Erstellen, Bearbeiten, Löschen und Filtern von Dokumenten
* Verwalten von gespeicherten Prozeduren, Triggern und benutzerdefinierten Funktionen

### <a name="quick-access-tasks"></a>Schnellzugriffsaufgaben

Indem Sie mit der rechten Maustaste auf ein Abonnement im Explorer-Bereich klicken, können Sie viele schnelle Aktionen ausführen:

* Wenn Sie mit der rechten Maustaste auf ein Azure Cosmos DB-Konto oder eine Datenbank klicken, können Sie **Im Portal öffnen** auswählen und die Ressource über den Browser im Azure-Portal verwalten.

     ![Im Portal öffnen](./media/storage-explorer/open-in-portal.png)

* Sie können auch die Azure Cosmos DB-Konten, Datenbanken oder Sammlungen als **Schnellzugriff** hinzufügen.
* **Ab hier suchen** ermöglicht eine Schlüsselwortsuche unter dem ausgewählten Pfad.

    ![Ab hier suchen](./media/storage-explorer/search-from-here.png) 

### <a name="database-and-collection-management"></a>Datenbank- und Sammlungsverwaltung
#### <a name="create-a-database"></a>Erstellen einer Datenbank 
Klicken Sie mit der rechten Maustaste auf das Azure Cosmos DB-Konto, wählen Sie **Datenbank erstellen** aus, geben Sie den Datenbanknamen ein, und drücken Sie zum Abschluss die **Eingabetaste**.

![Erstellen einer Datenbank](./media/storage-explorer/create-database.png) 

#### <a name="delete-a-database"></a>Löschen einer Datenbank
Klicken Sie mit der rechten Maustaste auf die Datenbank, klicken Sie auf **Datenbank löschen**, und klicken Sie im Popupfenster auf **Ja**. Der Datenbankknoten wird gelöscht, und das Azure Cosmos DB-Konto wird automatisch aktualisiert.

![database1 löschen](./media/storage-explorer/delete-database1.png)  

![database2 löschen](./media/storage-explorer/delete-database2.png) 

#### <a name="create-a-collection"></a>Erstellen einer Sammlung
Klicken Sie mit der rechten Maustaste auf die Datenbank, wählen Sie **Sammlung erstellen** aus, und geben Sie dann die benötigten Informationen ein, z.B. **Sammlungs-ID**, **Speicherkapazität** usw. Klicken Sie auf **OK**, um den Vorgang abzuschließen. Informationen über Partitionsschlüsseleinstellungen finden Sie unter [Entwerfen für Partitionierung](partition-data.md#designing-for-partitioning).

Wenn zum Erstellen einer Sammlung ein Partitionsschlüssel verwendet wird, kann der Partitionsschlüsselwert für die Auflistung nach Abschluss der Erstellung nicht mehr geändert werden.

![collection1 erstellen](./media/storage-explorer/create-collection.png)

![collection2 erstellen](./media/storage-explorer/create-collection2.png) 

#### <a name="delete-a-collection"></a>Löschen einer Sammlung
Klicken Sie mit der rechten Maustaste auf die Sammlung, klicken Sie auf **Sammlung löschen**, und klicken Sie dann im Popupfenster auf **Ja**. 

Der Sammlungsknoten wird gelöscht, und die Datenbank wird automatisch aktualisiert.  

![Sammlung löschen](./media/storage-explorer/delete-collection.png) 

### <a name="document-management"></a>Dokumentverwaltung

#### <a name="create-and-modify-documents"></a>Erstellen und Ändern von Dokumenten
Um ein neues Dokument zu erstellen, öffnen Sie im linken Fenster **Dokumente**, klicken Sie auf **Neues Dokument**. Bearbeiten Sie den Inhalt im rechten Bereich, und klicken Sie auf **Speichern**. Sie können auch ein vorhandenes Dokument aktualisieren und dann auf **Speichern** klicken. Änderungen können durch Klicken auf **Verwerfen** verworfen werden.

![Dokument](./media/storage-explorer/document.png)

#### <a name="delete-a-document"></a>Löschen eines Dokuments
Klicken Sie auf die Schaltfläche **Löschen**, um das ausgewählte Dokument zu löschen.
#### <a name="query-for-documents"></a>Abfragen von Dokumenten
Bearbeiten Sie den Dokumentfilter durch Eingeben einer [SQL-Abfrage](sql-api-sql-query.md), und klicken Sie dann auf **Anwenden**.

![Filter](./media/storage-explorer/filter.png)

### <a name="manage-stored-procedures-triggers-and-udfs"></a>Verwalten von gespeicherten Prozeduren, Triggern und UDFs
* Um eine gespeicherte Prozedur zu erstellen, klicken Sie in der linken Struktur mit der rechten Maustaste auf **Gespeicherte Prozedur**, wählen Sie **Gespeicherte Prozedur erstellen** aus, geben Sie links einen Namen ein, geben Sie die Skripts für die gespeicherte Prozedur im rechten Fenster ein, und klicken Sie dann auf **Erstellen**. 
* Sie können auch vorhandene gespeicherte Prozeduren bearbeiten, indem Sie doppelklicken, die Aktualisierung vornehmen und dann auf **Aktualisieren** klicken, um sie zu speichern, oder auf **Verwerfen**, um die Änderungen zu verwerfen.

![Gespeicherte Prozedur](./media/storage-explorer/stored-procedure.png)

* Die Vorgänge für **Trigger** und **UDFs** ähneln denen für **Gespeicherte Prozeduren**.

## <a name="next-steps"></a>Nächste Schritte

* Im folgenden Video erfahren Sie, wie Sie Azure Cosmos DB in Azure Storage-Explorer verwenden: [Azure Cosmos DB in Azure Storage Explorer](https://www.youtube.com/watch?v=iNIbg1DLgWo&feature=youtu.be).
* Weitere Informationen zum Speicher-Explorer sowie zum Herstellen einer Verbindung mit weiteren Diensten finden Sie unter [Erste Schritte mit dem Speicher-Explorer (Vorschau)](https://docs.microsoft.com/azure/vs-azure-tools-storage-manage-with-storage-explorer).

