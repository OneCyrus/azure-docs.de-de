---
title: Referenz zu Azure Container Registry-Webhookschemas
description: "Referenz zur JSON-Nutzlast von Webhookanforderungen für Azure Container Registry."
services: container-registry
author: mmacy
manager: timlt
ms.service: container-registry
ms.topic: article
ms.date: 12/02/2017
ms.author: marsma
ms.openlocfilehash: 84f0277a7b1a5bd7dfe2178f78f34140b1dd2642
ms.sourcegitcommit: a48e503fce6d51c7915dd23b4de14a91dd0337d8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2017
---
# <a name="azure-container-registry-webhook-reference"></a>Referenz zu Azure Container Registry-Webhooks

Sie können für Ihre Containerregistrierung [Webhooks konfigurieren](container-registry-webhook.md), die Ereignisse generieren, wenn dafür bestimmte Aktionen durchgeführt werden. Beispielsweise können Sie Webhooks aktivieren, die bei den Vorgängen `push` und `delete` für Containerimages ausgelöst werden. Wenn ein Webhook ausgelöst wird, sendet Azure Container Registry eine HTTP- oder HTTPS-Anforderung mit Informationen zum Ereignis an einen von Ihnen angegebenen Endpunkt. Ihr Endpunkt kann den Webhook dann verarbeiten und entsprechend agieren.

In den folgenden Abschnitten wird das Schema von Webhookanforderungen, die von unterstützten Ereignissen generiert werden, ausführlich beschrieben. Die Ereignisabschnitte enthalten das Nutzlastschema für den Ereignistyp, eine Beispiel-Anforderungsnutzlast und mindestens einen Beispielbefehl zum Auslösen des Webhooks.

Informationen zur Konfiguration von Webhooks für Ihre Azure Container Registry finden Sie unter [Verwenden von Azure Container Registry-Webhooks](container-registry-webhook.md).

## <a name="webhook-requests"></a>Webhookanforderungen

### <a name="http-request"></a>HTTP-Anforderung

Ein ausgelöster Webhook sendet eine HTTP-`POST`-Anforderung an den URL-Endpunkt, den Sie beim Konfigurieren des Webhooks angegeben haben.

### <a name="http-headers"></a>HTTP-Header

Webhookanforderungen enthalten als `Content-Type` die Angabe `application/json`, wenn Sie keinen benutzerdefinierten `Content-Type`-Header für Ihren Webhook angegeben haben.

Über die benutzerdefinierten Header hinaus, die Sie für den Webhook ggf. angeben, werden der Anforderung keine weiteren Header hinzugefügt.

## <a name="push-event"></a>Push-Ereignis

Auslösung per Webhook, wenn ein Containerimage per Pushvorgang in ein Repository übertragen wird.

### <a name="push-event-payload"></a>Nutzlast des Push-Ereignisses

|Element|Typ|Beschreibung|
|-------------|----------|-----------|
|`id`|String|Die ID des Webhookereignisses.|
|`timestamp`|DateTime|Der Zeitpunkt, zu dem das Webhookereignis ausgelöst wurde.|
|`action`|String|Die Aktion, die das Webhookereignis ausgelöst hat.|
|[Ziel](#target)|Komplexer Typ|Das Ziel des Ereignisses, von dem das Webhookereignis ausgelöst wurde.|
|[Anforderung](#request)|Komplexer Typ|Die Anforderung, die das Webhookereignis generiert hat.|

### <a name="target"></a>Ziel

|Element|Typ|Beschreibung|
|------------------|----------|-----------|
|`mediaType`|String|Der MIME-Typ des Objekts, auf das verwiesen wird.|
|`size`|Int32|Die Byte-Anzahl des Inhalts. Entspricht dem Feld „Length“ (Länge).|
|`digest`|String|Zusammenfassung des Inhalts gemäß Definition in der HTTP-API-Spezifikation der Registrierung (V2).|
|`length`|Int32|Die Byte-Anzahl des Inhalts. Entspricht dem Feld „Size“ (Größe).|
|`repository`|String|Der Name des Repositorys.|
|`tag`|String|Der Tagname des Images.|

### <a name="request"></a>request

|Element|Typ|Beschreibung|
|------------------|----------|-----------|
|`id`|String|Die ID der Anforderung, die das Ereignis initiiert hat.|
|`host`|String|Der extern zugängliche Hostname der Registrierungsinstanz, der im HTTP-Hostheader von eingehenden Anforderungen angegeben ist.|
|`method`|String|Die Anforderungsmethode, die das Ereignis generiert hat.|
|`useragent`|String|Der Benutzer-Agent-Header der Anforderung.|

### <a name="payload-example-push-event"></a>Nutzlastbeispiel: Push-Ereignis

```JSON
{
  "id": "cb8c3971-9adc-488b-bdd8-43cbb4974ff5",
  "timestamp": "2017-11-17T16:52:01.343145347Z",
  "action": "push",
  "target": {
    "mediaType": "application/vnd.docker.distribution.manifest.v2+json",
    "size": 524,
    "digest": "sha256:80f0d5c8786bb9e621a45ece0db56d11cdc624ad20da9fe62e9d25490f331d7d",
    "length": 524,
    "repository": "hello-world",
    "tag": "v1"
  },
  "request": {
    "id": "3cbb6949-7549-4fa1-86cd-a6d5451dffc7",
    "host": "myregistry.azurecr.io",
    "method": "PUT",
    "useragent": "docker/17.09.0-ce go/go1.8.3 git-commit/afdb6d4 kernel/4.10.0-27-generic os/linux arch/amd64 UpstreamClient(Docker-Client/17.09.0-ce \\(linux\\))"
  }
}
```

Beispiel: [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)-Befehl, mit dem der **Push**-Ereignis-Webhook ausgelöst wird:

```bash
docker push myregistry.azurecr.io/hello-world:v1
```

## <a name="delete-event"></a>Ereignis löschen

Wird per Webhook ausgelöst, wenn ein Repository oder Manifest gelöscht wird. Wird nicht ausgelöst, wenn ein Tag gelöscht wird.

### <a name="delete-event-payload"></a>Ereignisnutzlast löschen

|Element|Typ|Beschreibung|
|-------------|----------|-----------|
|`id`|String|Die ID des Webhookereignisses.|
|`timestamp`|DateTime|Der Zeitpunkt, zu dem das Webhookereignis ausgelöst wurde.|
|`action`|String|Die Aktion, die das Webhookereignis ausgelöst hat.|
|[Ziel](#delete_target)|Komplexer Typ|Das Ziel des Ereignisses, von dem das Webhookereignis ausgelöst wurde.|
|[Anforderung](#delete_request)|Komplexer Typ|Die Anforderung, die das Webhookereignis generiert hat.|

### <a name="delete_target"></a> Ziel

|Element|Typ|Beschreibung|
|------------------|----------|-----------|
|`mediaType`|String|Der MIME-Typ des Objekts, auf das verwiesen wird.|
|`digest`|String|Zusammenfassung des Inhalts gemäß Definition in der HTTP-API-Spezifikation der Registrierung (V2).|
|`repository`|String|Der Name des Repositorys.|

### <a name="delete_request"></a> Anforderung

|Element|Typ|Beschreibung|
|------------------|----------|-----------|
|`id`|String|Die ID der Anforderung, die das Ereignis initiiert hat.|
|`host`|String|Der extern zugängliche Hostname der Registrierungsinstanz, der im HTTP-Hostheader von eingehenden Anforderungen angegeben ist.|
|`method`|String|Die Anforderungsmethode, die das Ereignis generiert hat.|
|`useragent`|String|Der Benutzer-Agent-Header der Anforderung.|

### <a name="payload-example-delete-event"></a>Nutzlastbeispiel: Ereignis löschen

```JSON
{
    "id": "afc359ce-df7f-4e32-bdde-1ff8aa80927b",
    "timestamp": "2017-11-17T16:54:53.657764628Z",
    "action": "delete",
    "target": {
      "mediaType": "application/vnd.docker.distribution.manifest.v2+json",
      "digest": "sha256:80f0d5c8786bb9e621a45ece0db56d11cdc624ad20da9fe62e9d25490f331d7d",
      "repository": "hello-world"
    },
    "request": {
      "id": "3d78b540-ab61-4f75-807f-7ca9ecf559b3",
      "host": "myregistry.azurecr.io",
      "method": "DELETE",
      "useragent": "python-requests/2.18.4"
    }
  }
```

Beispiel: [Azure CLI 2.0](/cli/azure/acr)-Befehle, mit denen ein **delete**-Ereignis-Webhook ausgelöst wird:

```azurecli
# Delete repository
az acr repository delete -n MyRegistry --repository MyRepository

# Delete manifest
az acr repository delete -n MyRegistry --repository MyRepository --tag MyTag --manifest
```

## <a name="next-steps"></a>Nächste Schritte

[Verwenden von Azure Container Registry-Webhooks](container-registry-webhook.md)