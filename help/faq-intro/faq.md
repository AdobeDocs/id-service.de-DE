---
description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich des ID-Diensts.
keywords: ID Service
seo-description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich des ID-Diensts.
seo-title: Häufig gestellte Fragen zum ID-Dienst
title: Häufig gestellte Fragen zum ID-Dienst
uuid: e8d8f819-3d73-4fa2-864c-4867071c14ee
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Häufig gestellte Fragen zum ID-Dienst{#id-service-faqs}

Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich des ID-Diensts.

## Funktionalität {#section-659e89f8b9a74cb8afff35587dc96836}

**Welche Art von Funktionalität oder Funktionen bietet der ID-Dienst?**

Siehe  [Übersicht](../introduction/overview.md).

**Warum ruft der ID-Dienst nicht zum Abrufen der Experience Cloud ID auf?**

Das kann schwer zu diagnostizieren sein. Sie können die Kopfzeilen der Sicherheitsrichtlinien für Inhalte auf Ihrer Site überprüfen. Wenn Sie über eine strikte Sicherheitsrichtlinie verfügen, können diese Einstellungen die vom ID-Dienst ausgeführten Drittanbieteraufrufe blockieren. See [Content Security Policies and the Experience Cloud Identity Service](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3).

**Datenspeicherung der Datei VisitorAPI.js**

Möglicherweise treten Probleme auf, wenn Sie die Datei VisitorAPI.js als lokale Datei in mobilen Apps hosten. Es wird empfohlen, die Datei auf einem Webserver zu hosten.

## Seitenladezeiten und Latenz {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**Wie wirkt sich die Platzierung der ID-Dienstbibliothek VisitorAPI.js auf die Seitenladezeiten aus?**

Platzieren Sie die Bibliothek VisitorAPI.js oben auf der Seite in den `<head>` Abschnitt Ihres Codes. Dadurch stellen Sie sicher, dass der Aufruf an eine ID gesendet wird, bevor der Seitentext geladen wird, und die Wahrscheinlichkeit, dass eine ID erfolgreich zurückgegeben wird, erhöht sich.

The ID service call is asynchronous and is the only call to the [demdex.net domain](https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/reference/demdex-calls.html). Der Aufruf des ID-Diensts verhindert nicht, dass andere Elemente auf der Seite geladen werden.

Für [!DNL Target]-Kunden kann die Platzierung von ID-Dienst-Code in `<body>` der Seite die Wahrscheinlichkeit erhöhen, dass ein [!DNL Target]-Aufruf blockiert wird. Wenn Sie ID-Dienst-Code im Haupttext Ihrer Seite platzieren müssen, dann sollten Sie ihn nach dem öffnenden `<body>`-Tag einfügen.

**Führt der ID-Dienst bei jedem Laden der Seite einen Server-Aufruf durch?**

Nein, dieser Aufruf erfolgt nur beim ersten Rendern der Seite und danach alle 7 Tage. In der Zwischenzeit sind keine Server-Aufrufe erforderlich. Der ID-Dienst arbeitet im clientseitigen Modus und muss keinen Server-Aufruf durchführen, um eine ID zurückzugeben.

Siehe [Übersicht](../introduction/overview.md).

**Was kann bei Verwendung des ID-Diensts zu langsamen Seitenladezeiten oder zu Beeinträchtigungen der Benutzererfahrung führen?**

Es ist schwierig, alle möglichen Bedingungen zu katalogisieren. Milliarden von Kunden verbinden sich mit unseren Dienstleistungen und der enormen Vielfalt, wo und wie sie sich verbinden, beeinflussen die Leistung. Beispiel:

* Die Geschwindigkeit variiert stark in den Mobilfunknetzen. Diese Netzwerke leiden auch unter Signal- und Daten- oder Sprachpaketverlust.
* Die Konnektivität leidet unter verschiedenen Bedingungen an Geräten, die über WiFi verbunden sind. Beispielsweise treten Packet-Loss- und Geschwindigkeitsprobleme häufig an öffentlichen Orten wie Coffeeshops oder in anderen Umgebung wie Flugzeugen auf, wo die Pakete über einen Satelliten springen müssen, bevor sie zu terrestrischen Netzwerken gelangen.
* Schlecht konfigurierte lokale Netzwerke können die Konnektivität und Geschwindigkeit negativ beeinflussen.
* Client-Geräte haben möglicherweise eigene Probleme, wie z. B. niedrigen Arbeitsspeicher, übermäßiges Disk-Swapping oder eingeschränkte CPU-Leistung im Verhältnis zu aktuellen Arbeitslasten.
* Browser stellen Remote-Server-Aufrufe in Warteschlange und führen sie aus und verarbeiten die Antworten sogar mit unterschiedlichen Regeln, je nach Browser und Version. Dieses Verhalten beeinflusst Geschwindigkeit und Leistung.

**Können Sie einige Verbesserungen benennen, die Sie vorgenommen haben, um die Seitenladezeit zu verkürzen?**

Beispiel: Thread-Ergebnisse. Wir haben Thread-Ergebnisse bei mehreren ID-Synchronisierungsanforderungen eingeführt. Aus Laborberichten haben wir festgestellt, dass die Benutzeroberfläche für Kunden, die mehrere ID-Syncs ausführen, blockiert wird, da eine Menge kontinuierlicher CPU-Berechnungen stattfindet. Infolgedessen haben wir Thread eingeführt, der die ID-Synchronisierungsanforderungen um jeweils 100 msec voneinander trennt.

Diese Änderung verbessert die Leistung von Kunden, die Besucher 2.3.0+ und DIL 6.10+ verwenden. Die Verbesserungen bei den Seitenladezeiten sind in der folgenden Abbildung dargestellt:

![](assets/id_sync_improvements_copy.png)

**Beeinflussen Browseranforderungen mit CORS im Vergleich zu JSON-P die Seitenleistung?**

Ressourcenanforderungen mit CORS sind im Allgemeinen besser geeignet als mit JSONP. Bei JSONP weisen einige Browser Anforderungen eine geringere Priorität zu als anderen synchronen und asynchronen Abrufen, wenn sie diese in die Warteschlange stellen. CORS hilft sicherzustellen, dass diese Anforderungen mit einer höheren Priorität im Browseraufrufstapel behandelt werden.

Siehe [CORS-Unterstützung im Experience Cloud Identity-Dienst](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## Sicherheit {#section-b176b8492fbe4acfb79ebb30ec902f98}

**Unterstützt der ID-Dienst CORS?**

Ja. Siehe [CORS-Unterstützung im Experience Cloud Identity-Dienst](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Was ist CORS?**

*`Cross-Origin Resource Sharing`* oder CORS ist eine Methode, mit der Browser Ressourcen anfordern. Der ID-Dienst fordert immer Ressourcen mit CORS in Browsern an, die ihn unterstützen. Der ID-Dienst fordert Ressourcen mit JSON-P in älteren Browsern an, die CORS nicht unterstützen. Weitere Informationen finden Sie unter [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Was geschieht, wenn meine Sicherheitsanforderungen so streng sind, dass ich JSONP nie verwenden möchte?**

Wenn Sie strenge Sicherheitsanforderungen haben, legen Sie in der Konfiguration der ID-Dienst-API `useCORSOnly: true` fest. Sie sollten diesen Modus nur aktivieren, wenn Sie sicher sind, dass Ihre Site-Besucher Browser verwenden, die CORS unterstützen.

See [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) and [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORELIKETHIS]
>
>* [Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html)

