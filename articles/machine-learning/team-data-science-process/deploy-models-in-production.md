---
title: "Bereitstellen von Modellen in der Produktion – Azure Machine Learning | Microsoft-Dokumentation"
description: "Erfahren Sie, wie Sie Modelle in der Produktion bereitstellen, damit sie eine aktive Rolle bei geschäftlichen Entscheidungen spielen können."
documentationcenter: 
author: bradsev
manager: cgronlun
editor: cgronlun
ms.assetid: 
ms.service: machine-learning
ms.workload: data-services
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 11/30/2017
ms.author: bradsev;
ms.openlocfilehash: c7be9eda2d6f37951eb120250861cf4a39b0141b
ms.sourcegitcommit: be0d1aaed5c0bbd9224e2011165c5515bfa8306c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2017
---
# <a name="deploy-models-in-production"></a>Bereitstellen von Modellen in der Produktion

Bei einer Produktionsbereitstellung kann ein Modell eine aktive Rolle in einem Unternehmen spielen. Vorhersagen aus einem bereitgestellten Modell können für Geschäftsentscheidungen verwendet werden.

## <a name="production-platforms"></a>Produktionsplattformen
Es gibt verschiedene Ansätze und Plattformen für das Einführen von Modellen in die Produktion. Hier sind einige Optionen angegeben:


- [Modellentwicklung in Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/model-management-overview)
- [Bereitstellung eines Modells in SQL Server](https://docs.microsoft.com/sql/advanced-analytics/tutorials/sqldev-py6-operationalize-the-model)
- [Microsoft Machine Learning Server](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone)


>[!NOTE]
>Vor der Bereitstellung muss sichergestellt werden, dass bei der Bewertung durch das Modell ausreichend geringe Latenzen für eine Verwendung in der Produktion auftreten.
>


>[!NOTE]
>Informationen zur Bereitstellung mit Azure Machine Learning Studio finden Sie unter [Bereitstellen eines Azure Machine Learning-Webdiensts](../studio/publish-a-machine-learning-web-service.md).
>

## <a name="ab-testing"></a>A/B-Tests
Wenn sich mehrere Modelle in der Produktion befinden, kann es nützlich sein, [A/B-Tests](https://en.wikipedia.org/wiki/A/B_testing) zum Vergleichen der Leistung der Modelle durchzuführen. 

 
## <a name="next-steps"></a>Nächste Schritte

Exemplarische Vorgehensweisen, in denen sämtliche Schritte im Prozess für **bestimmte Szenarien** gezeigt werden, sind ebenfalls verfügbar. Sie sind im Artikel [Exemplarische Vorgehensweisen](walkthroughs.md) aufgeführt und mit Miniaturansichtsbeschreibungen verlinkt. Sie zeigen, wie Cloud- und lokale Tools und Dienste in einem Workflow oder einer Pipeline zum Erstellen einer intelligenten Anwendung kombiniert werden. 
 


