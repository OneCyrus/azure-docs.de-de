---
title: 'Azure Active Directory Domain Services: Beheben von Problemen bei der Konfiguration von Secure LDAP | Microsoft-Dokumentation'
description: "Beheben von Problemen mit Secure LDAP für Azure AD Domain Services"
services: active-directory-ds
documentationcenter: 
author: eringreenlee
manager: 
editor: 
ms.assetid: 81208c0b-8d41-4f65-be15-42119b1b5957
ms.service: active-directory-ds
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 01/17/2018
ms.author: ergreenl
ms.openlocfilehash: ad98f3fb1ddb753976be627764d34864e5bf3d50
ms.sourcegitcommit: f1c1789f2f2502d683afaf5a2f46cc548c0dea50
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2018
---
# <a name="azure-ad-domain-services---troubleshooting-secure-ldap-configuration"></a>Azure Active Directory Domain Services: Beheben von Problemen bei der Konfiguration von Secure LDAP

Dieser Artikel bietet Lösungen für häufiger auftretende Probleme bei der [Konfiguration von Secure LDAP](active-directory-ds-admin-guide-configure-secure-ldap.md) für Azure AD Domain Services.

## <a name="aadds101-secure-ldap-network-security-group-configuration"></a>AADDS101: Konfiguration der Netzwerksicherheitsgruppe für Secure LDAP

**Warnmeldung:**

*Secure LDAP über das Internet ist für die verwaltete Domäne aktiviert. Der Zugriff auf Port 636 ist jedoch nicht über eine Netzwerksicherheitsgruppe gesperrt. Dies kann Brute-Force-Kennwortangriffe auf Benutzerkonten in der verwalteten Domäne möglich machen.*

### <a name="secure-ldap-port"></a>Secure LDAP-Port

Wenn Secure LDAP aktiviert ist, wird das Erstellen zusätzlicher Regeln empfohlen, die eingehenden LDAPS-Zugriff nur von bestimmten IP-Adressen zulassen. Diese Regeln schützen Ihre Domäne vor Brute-Force-Angriffen, die ein Sicherheitsrisiko darstellen können. Port 636 erlaubt den Zugriff auf Ihre verwaltete Domäne. So aktualisieren Sie die NSG für das Zulassen des Zugriffs für Secure LDAP

1. Navigieren Sie im Azure-Portal zur Registerkarte [Netzwerksicherheitsgruppen](https://portal.azure.com/#blade/HubsExtension/Resources/resourceType/Microsoft.Network%2FNetworkSecurityGroups).
2. Wählen Sie in der Tabelle die NSG aus, die Ihrer Domäne zugeordnet ist.
3. Klicken Sie auf **Eingangssicherheitsregeln**.
4. Erstellen der Regel für Port 636
   1. Klicken Sie auf der oberen Navigationsleiste auf **Hinzufügen**.
   2. Wählen Sie **IP-Adressen** für die Quelle aus.
   3. Geben Sie die Quellportbereiche für diese Regel an.
   4. Geben Sie als Zielportbereich „636“ ein.
   5. Das Protokoll ist **TCP**.
   6. Fügen Sie der Regel einen geeigneten Namen, eine Beschreibung und eine Priorität hinzu. Die Priorität der Regel sollte größer als die der Regel „Alle verweigern“ (sofern vorhanden) sein.
   7. Klicken Sie auf **OK**.
5. Überprüfen Sie, ob die Regel erstellt wurde.
6. Überprüfen Sie in zwei Stunden die Integrität Ihrer Domäne, um sicherzustellen, dass Sie die Schritte ordnungsgemäß abgeschlossen haben.


## <a name="contact-us"></a>Kontakt
Wenden Sie sich an das Produktteam der Azure Active Directory Domain Services, um [Feedback zu geben oder Support zu erhalten](active-directory-ds-contact-us.md).
