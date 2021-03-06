---
title: "Funktionen zum Erstellen von Benutzeroberflächendefinitionen in verwalteten Azure-Anwendungen | Microsoft-Dokumentation"
description: "Hier werden die Funktionen beschrieben, mit denen Benutzeroberflächendefinitionen für verwaltete Azure-Anwendungen erstellt werden."
services: azure-resource-manager
documentationcenter: na
author: tfitzmac
manager: timlt
editor: tysonn
ms.service: azure-resource-manager
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/12/2017
ms.author: tomfitz
ms.openlocfilehash: 23e407bf93bc51116ca45339bffcb801d69290f0
ms.sourcegitcommit: 3ab5ea589751d068d3e52db828742ce8ebed4761
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="createuidefinition-elements"></a>CreateUiDefinition-Elemente
In diesem Artikel werden das Schema und die Eigenschaften für alle unterstützten Elemente eines CreateUiDefinition-Elements beschrieben. Diese Elemente verwenden Sie beim [Erstellen einer verwalteten Azure-Anwendung](publish-service-catalog-app.md). Das Schema für die meisten Elemente ist wie folgt:

```json
{
  "name": "element1",
  "type": "Microsoft.Common.TextBox",
  "label": "Some text box",
  "defaultValue": "foobar",
  "toolTip": "Keep calm and visit the [Azure Portal](portal.azure.com).",
  "constraints": {},
  "options": {},
  "visible": true
}
```

| Eigenschaft | Erforderlich | Beschreibung |
| -------- | -------- | ----------- |
| Name | Ja | Ein interner Bezeichner für den Verweis auf eine bestimmte Instanz eines Elements. Am häufigsten wird der Elementname in `outputs` verwendet. Dabei werden die Ausgabewerte der angegebenen Elemente den Parametern der Vorlage zugeordnet. Sie können mit ihm auch den Ausgabewert eines Elements an `defaultValue` eines anderen Elements binden. |
| Typ | Ja | Das Benutzeroberflächensteuerelement, das für das Element gerendert werden soll. Eine Liste der unterstützten Typen finden Sie unter [Elemente](#elements). |
| label | Ja | Der Anzeigetext des Elements. Einige Elementtypen enthalten mehrere Bezeichnungen. Der Wert kann also ein Objekt sein, das mehrere Zeichenfolgen enthält. |
| defaultValue | Nein | Der Standardwert des Elements. Einige Elementtypen unterstützen komplexe Standardwerte. Der Wert kann also ein Objekt sein. |
| toolTip | Nein | Der Text, der in der QuickInfo des Elements angezeigt werden soll. Ähnlich wie bei `label` unterstützen einige Elemente mehrere QuickInfo-Zeichenfolgen. Inlinelinks können mithilfe von Markdownsyntax eingebettet werden.
| constraints | Nein | Eigenschaften, die zum Anpassen des Überprüfungsverhaltens des Elements verwendet werden. Die unterstützten Eigenschaften für Einschränkungen variieren je nach Elementtyp. Einige Elementtypen unterstützen die Anpassung des Überprüfungsverhaltens nicht und enthalten daher keine constraints-Eigenschaft. |
| options | Nein | Zusätzliche Eigenschaften, die das Verhalten des Elements anpassen. Ähnlich wie bei `constraints` variieren die unterstützten Eigenschaften je nach Elementtyp. |
| visible | Nein | Gibt an, ob das Element angezeigt wird. Ist `true` angegeben, werden das Element und entsprechende untergeordnete Elemente angezeigt. Standardwert: `true`. Verwenden Sie [logische Funktionen](create-uidefinition-functions.md#logical-functions), um den Wert dieser Eigenschaft dynamisch zu steuern.

## <a name="elements"></a>Elemente

Die Dokumentation für die einzelnen Elemente enthält ein Benutzeroberflächenbeispiel, ein Schema, Hinweise zum Verhalten des Elements (in der Regel in Bezug auf Überprüfung und unterstützte Anpassung) und eine Beispielausgabe.

- [Microsoft.Common.DropDown](microsoft-common-dropdown.md)
- [Microsoft.Common.FileUpload](microsoft-common-fileupload.md)
- [Microsoft.Common.OptionsGroup](microsoft-common-optionsgroup.md)
- [Microsoft.Common.PasswordBox](microsoft-common-passwordbox.md)
- [Microsoft.Common.Section](microsoft-common-section.md)
- [Microsoft.Common.TextBox](microsoft-common-textbox.md)
- [Microsoft.Compute.CredentialsCombo](microsoft-compute-credentialscombo.md)
- [Microsoft.Compute.SizeSelector](microsoft-compute-sizeselector.md)
- [Microsoft.Compute.UserNameTextBox](microsoft-compute-usernametextbox.md)
- [Microsoft.Network.PublicIpAddressCombo](microsoft-network-publicipaddresscombo.md)
- [Microsoft.Network.VirtualNetworkCombo](microsoft-network-virtualnetworkcombo.md)
- [Microsoft.Storage.MultiStorageAccountCombo](microsoft-storage-multistorageaccountcombo.md)
- [Microsoft.Storage.StorageAccountSelector](microsoft-storage-storageaccountselector.md)

## <a name="next-steps"></a>Nächste Schritte
* Eine Einführung in verwaltete Anwendungen finden Sie in der [Übersicht über verwaltete Azure-Anwendungen](overview.md).
* Eine Einführung zum Erstellen von Benutzeroberflächendefinitionen finden Sie unter [Erste Schritte mit „CreateUiDefinition“](create-uidefinition-overview.md).
