---
title: "Azure Active Directory B2C: Regionale Verfügbarkeit und Datenresidenz | Microsoft-Dokumentation"
description: "Das Thema enthält eine Beschreibung der Typen von Azure Active Directory B2C-Mandanten."
services: active-directory-b2c
documentationcenter: 
author: gsacavdm
manager: mtillman
editor: bryanla
ms.assetid: 8a0644da-b825-4edc-8ce9-541c3c976afb
ms.service: active-directory-b2c
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 04/10/2017
ms.author: gsacavdm
ms.openlocfilehash: 752a98ca7f3c77c434de296461790f2cf37e2d5c
ms.sourcegitcommit: e266df9f97d04acfc4a843770fadfd8edf4fa2b7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2017
---
# <a name="azure-active-directory-b2c-region-availability--data-residency"></a>Azure Active Directory B2C: Regionale Verfügbarkeit und Datenresidenz
Regionale Verfügbarkeit und Datenresidenz sind zwei sehr unterschiedliche Konzepte, die in Azure AD B2C anders als in den restlichen Komponenten von Azure angewendet werden. In diesem Artikel werden die Unterschiede zwischen diesen beiden Konzepten erläutert und ihre Anwendung in Azure und Azure AD B2C miteinander verglichen.

## <a name="summary"></a>Zusammenfassung
Azure AD B2C ist **grundsätzlich weltweit verfügbar**, mit der Option für **Datenresidenz für die USA und Europa**.

## <a name="concepts"></a>Konzepte
* **Regionale Verfügbarkeit** gibt an, wo ein Dienst für die Verwendung verfügbar ist.
* **Datenresidenz** gibt an, wo die Benutzerdaten gespeichert werden.

## <a name="region-availability"></a>Regionale Verfügbarkeit
Azure AD B2C ist über die öffentliche Azure-Cloud weltweit verfügbar. 

Dies unterscheidet sich von dem Modell der meisten anderen Azure-Dienste, in dem Verfügbarkeit und Datenresidenz gekoppelt sind. Beispiele hierfür finden Sie auf der Seite [Verfügbare Produkte nach Region](https://azure.microsoft.com/regions/services/) und der Seite [Azure Active Directory B2C – Preise](https://azure.microsoft.com/pricing/details/active-directory-b2c/) von Azure.

## <a name="data-residency"></a>Datenresidenz
Benutzerdaten von Azure AD B2C werden in den USA oder in Europa gespeichert.

Die Datenresidenz wird basierend auf dem Land/der Region bestimmt, das bzw. die beim [Erstellen eines Azure AD B2C-Mandanten](active-directory-b2c-get-started.md) ausgewählt wird.

![Screenshot eines Vorschaumandanten](./media/active-directory-b2c-reference-tenant-type/data-residency-b2c-tenant.png)

Für die folgenden Länder/Regionen werden die Daten in den USA gespeichert:

> USA, Kanada, Costa Rica, Dominikanische Republik, El Salvador, Guatemala, Mexiko, Panama, Puerto Rico sowie Trinidad und Tobago

Für die folgenden Länder/Regionen werden die Daten in Europa gespeichert:

> Algerien, Ägypten, Aserbaidschan, Bahrain, Belgien, Bulgarien, Dänemark, Deutschland, Estland, Finnland, Frankreich, Griechenland, Irland, Island, Israel, Italien, Jordanien, Kasachstan, Katar, Kenia, Kroatien, Kuwait, Lettland, Libanon, Liechtenstein, Litauen, Luxemburg, Malta, Marokko, Mazedonien (ehem. jugoslawische Republik), Montenegro, Niederlande, Nigeria, Norwegen, Oman, Österreich, Pakistan, Polen, Portugal, Rumänien, Russland, Saudi-Arabien, Schweden, Schweiz, Serbien, Slowakei, Slowenien, Spanien, Südafrika, Tschechische Republik, Tunesien, Türkei, Ukraine, Ungarn, Vereinigte Arabische Emirate, Vereinigtes Königreich, Weißrussland und Zypern.

Derzeit wird die Liste mit den restlichen Länder/Regionen ergänzt.  Sie können vorerst Azure AD B2C verwenden, indem Sie eines bzw. eine der oben genannten Länder/Regionen auswählen.

> Afghanistan, Argentinien, Australien, Brasilien, Chile, Ecuador, Hongkong SAR, Indien, Indonesien, Irak, Japan, Kolumbien, Malaysia, Neuseeland, Paraguay, Peru, Philippinen, Singapur, Sri Lanka, Südkorea, Taiwan, Thailand, Uruguay und Venezuela.

## <a name="preview-tenant"></a>Vorschaumandant
Wenn Sie während des Vorschauzeitraums von Azure AD B2C einen B2C-Mandanten erstellt haben, ist die Wahrscheinlichkeit hoch, dass der **Mandantentyp** auf **Vorschaumandant** festgelegt ist. In diesem Fall können Sie Ihren Mandanten NUR für Entwicklungs- und Testzwecke verwenden, und NICHT für Produktions-Apps.

> [!IMPORTANT]
> Es ist kein Migrationspfad von einem B2C-Vorschaumandanten zu einem B2C-Produktionsmandanten vorhanden. Beachten Sie, dass beim Löschen eines B2C-Vorschaumandanten und erneuten Erstellen eines B2C-Produktionsmandanten mit demselben Domänennamen bekannte Probleme auftreten. Sie müssen einen B2C-Produktionsmandanten mit einem anderen Domänennamen erstellen.


![Screenshot eines Vorschaumandanten](./media/active-directory-b2c-reference-tenant-type/preview-b2c-tenant.png)
