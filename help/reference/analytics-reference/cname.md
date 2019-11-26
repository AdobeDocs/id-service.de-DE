---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: Datenerfassungs-CNAMEs und domänenübergreifendes Tracking
title: Datenerfassungs-CNAMEs und domänenübergreifendes Tracking
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 989b5f537848a7506a96e2eac17409f8b0307217

---


# Datenerfassung und -identität{#data-collection-and-identity}

In der Analyse gibt es drei Möglichkeiten, Besucher zu identifizieren.

- Verwenden des [Besucher-ID-Service](https://docs.adobe.com/content/help/en/id-service/using/home.md)
- Verwenden der [alten Analytics-Besucher-ID](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-overview.md)
- Geben Sie ihre eigene Identität an

## Using the Visitor ID Service{#using-the-visitor-id-service}

Der Besucher-ID-Service ist die empfohlene Methode zur Identifizierung von Besuchern. Er basiert auf zwei Komponenten

- Erstanbieter-ID - Eine Erstanbieter-ID, mit der Besucher Ihrer eigenen Website gemessen werden können. Diese ID wird in der ersten Partry-ID gespeichert und sowohl in einem clientseitigen Cookie als auch in einem serverseitigen Cookie (mit einem CNAME).
- Drittanbieter-ID (optional) - Eine auf demdex.net gespeicherte separate Drittanbieter-ID, die zur Besuchermessung über mehrere Domänen hinweg verwendet werden kann (z. B. example.com und example.net)

Analytics verwendet die Erstanbieter-ID, es sei denn, Drittanbieter-IDs sind aktiviert. Wenn Browser dies zulassen, wird diese ID verwendet. Die Drittanbieter-ID wird vor dem Kunden benannt, sodass ein Kunde keine Daten mit einem anderen Kunden in Analytics kombinieren kann.

## Ältere Analytics-Domänen

Vor dem Start des Adobe Besucher-ID-Diensts verwendeten viele Kunden die nativen Analytics-Domänen, um die ID-Cookies zu setzen. Dazu gehören `omtrdc.net`die Domäne `2o7.net` CNAMEd. `omtrdc.net`, `2o7.net`in einigen Fällen wurde eine CNAME-Domäne verwendet, um Drittanbieter-Cookies zu speichern. Die so eingestellten Cookies waren auf einen einzigen Kunden beschränkt, sodass Kunden ihre Daten nicht mit Daten anderer Kunden kombinieren konnten. Drittanbieter-CNAMED-Domänen, manchmal auch als benutzerfreundliche Drittanbieter-Domänen bezeichnet, wurden verwendet, wenn Kunden Benutzer über Websites hinweg verfolgen möchten, deren Inhaber sie sind (z. B. example.com, example.co.jp). Diese Methode oder die Verwendung von CNAME zur Unterstützung benutzerfreundlicher Drittanbieter-Domänen wird nicht mehr unterstützt, um den robusteren und datenschutzfreundlicheren Besucher-ID-Service zu ermöglichen. Kunden sollten so bald wie möglich mit einem CNAME pro Domäne zum Besucher-ID-Service wechseln.

## Eigene Identität angeben

Wenn ein Kunde entscheidet, dass er das Identifizierungssystem von Adobe vollständig umleiten und eine eigene implementieren kann, indem er eine [benutzerdefinierte Besucher-ID](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md)bereitstellt. Es gibt einige Dinge, die man beachten muss, wenn man diese Route wählt.

- Sie müssen die Opt-out-Regelung und geeignete Datenschutzkontrollen implementieren
- Diese ID gilt nur für Analytics
- Sie sind für die Beibehaltung dieser ID verantwortlich

## Datenerfassungs-CNAMEN

Adobe empfiehlt weiterhin die Verwendung eines CNAME in Verbindung mit dem Besucher-ID-Service. Auf diese Weise kann die Besucher-ID des Erstanbieters mithilfe von HTTP-Cookies beibehalten werden, wodurch die Cookies haltbarer werden.

## OPTOUT

Adobe stellt Kunden die APIs zur Verfügung, um Ausschluss-Signale an unsere Systeme weiterzugeben, sodass Kunden wiederum die Möglichkeit haben, die Verfolgung abzuwählen. Wir geben detaillierte Anweisungen, wie Kunden die richtigen Kontrollen implementieren können, um die Benutzerauswahl zu unterstützen. entweder die [Ausschluss-API](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md) oder Optionen, um zu [verhindern, dass Cookies ausgelöst](https://docs.adobe.com/content/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md) werden, bis die Zustimmung eingeholt wird

## Aktivierung der CNAME-Unterstützung mit dem Experience Cloud Identity-Dienst {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Die CNAME-Unterstützung des Datenerfassungsservers [aktiviert die Einrichtung eines CNAME](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.md) und die Einstellung der `visitor.marketingCloudServerSecure` Variablen im Experience Cloud-Identitätsdienst sowie die Einstellung `s.trackingServerSecure` in AppMeasurement.
