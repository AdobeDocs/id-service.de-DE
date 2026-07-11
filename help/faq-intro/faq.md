---
description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich des Besucher-ID-Service.
keywords: Besucher-ID-Service
title: Häufig gestellte Fragen zum Besucher-ID-Service
exl-id: 4dd2220c-8a9d-4e27-838b-be5ad357cb3e
TQID: https://experienceleague.adobe.com/FxgL8UXSmoJM1oFr47yCAgYGcTa2PqKvSNM4bHjTw1M
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 824
ht-degree: 54%

---

# Häufig gestellte Fragen zum Besucher-ID-Service{#id-service-faqs}

Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich des Besucher-ID-Service.

## Funktionalität {#section-659e89f8b9a74cb8afff35587dc96836}

**Welche Funktionen bietet der Besucher-ID-Dienst?**

Siehe [Übersicht](../introduction/overview.md).

**Warum führt der Besucher-ID-Service keinen Aufruf zum Abrufen der ECID durch?**

Das kann schwer zu diagnostizieren sein. Sie können die Header der Inhaltssicherheitsrichtlinien auf Ihrer Site überprüfen. Wenn Sie über eine strikte Sicherheitsrichtlinie verfügen, können diese Einstellungen die Aufrufe von Drittanbietern blockieren, die vom Besucher-ID-Dienst getätigt werden. Siehe [Inhaltssicherheitsrichtlinien und der Besucher-ID-Service](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3).

**`VisitorAPI.js`Dateispeicher**

Es können Probleme auftreten, wenn Sie die `VisitorAPI.js` als lokale Datei in Mobile Apps hosten. Es wird empfohlen, die Datei auf einem Webserver zu hosten.

## Seitenladezeiten und Latenz {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**Wie wirkt sich die Platzierung der Besucher-ID-Service-`VisitorAPI.js` auf die Seitenladezeiten aus?**

Platzieren Sie die `VisitorAPI.js`-Bibliothek oben auf der Seite im `<head>` Code-Abschnitt. Dadurch stellen Sie sicher, dass der Aufruf an eine ID gesendet wird, bevor der Seitentext geladen wird, und die Wahrscheinlichkeit, dass eine ID erfolgreich zurückgegeben wird, erhöht sich.

Der Aufruf des Besucher-ID-Diensts ist asynchron und der einzige Aufruf an die Domain [demdex.net](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=de). Der Aufruf des Besucher-ID-Diensts blockiert nicht das Laden anderer Elemente auf der Seite.

Bei Target-Kunden kann die Platzierung des Besucher-ID-Service-Codes im `<body>` der Seite die Wahrscheinlichkeit erhöhen, dass ein Target-Aufruf blockiert wird. Wenn Sie den Besucher-ID-Service-Code im Textkörper Ihrer Seite platzieren müssen, sollte er hinter dem Tag &quot;`<body>` öffnen“ platziert werden.

**Führt der Besucher-ID-Dienst bei jedem Laden der Seite einen Server-Aufruf durch?**

Nein, dieser Aufruf erfolgt nur beim ersten Rendern der Seite und danach alle 7 Tage. In der Zwischenzeit sind keine Server-Aufrufe erforderlich. Der Besucher-ID-Dienst arbeitet im Client-seitigen Modus und muss keinen Server-Aufruf ausführen, um eine ID zurückzugeben.

Siehe [Übersicht](../introduction/overview.md).

**Was kann bei Verwendung des Besucher-ID-Service zu langsamen Seitenladezeiten führen oder das Benutzererlebnis beeinträchtigen?**

Es ist schwierig, alle möglichen Bedingungen zu katalogisieren. Milliarden von Verbraucher-Clients verbinden sich mit unseren Diensten, und die enorme Vielfalt, wo und wie sie sich verbinden, wirkt sich auf die Performance aus. Beispiel:

* Die Geschwindigkeiten in Mobilfunknetzen sind sehr unterschiedlich. Diese Netzwerke leiden auch unter Signal- und Daten- oder Sprachpaketverlusten.
* Die Konnektivität leidet bei Geräten, die unter verschiedenen Bedingungen eine Verbindung über WLAN herstellen. Beispielsweise treten Paketverluste und Geschwindigkeitsprobleme häufig an öffentlichen Orten wie Cafés oder in anderen Umgebungen wie Flugzeugen auf, wo Pakete über Satelliten geleitet werden müssen, bevor sie terrestrische Netzwerke erreichen.
* Schlecht konfigurierte lokale Netzwerke können die Konnektivität und Geschwindigkeit negativ beeinflussen.
* Client-Geräte können ihre eigenen Probleme haben, wie z. B. zu wenig Arbeitsspeicher, übermäßiger Speicheraustausch oder begrenzte CPU-Leistung im Verhältnis zur aktuellen Arbeitslast.
* Browser verwenden je nach Hersteller und Version verschiedene Regeln, um Remote-Server-Aufrufe in die Warteschlange zu stellen, auszuführen und zu verarbeiten. Dieses Verhalten wirkt sich auf Geschwindigkeit und Performance aus.

**Können Sie einige Verbesserungen nennen, die Sie vorgenommen haben, um die Seitenladezeit zu verkürzen?**

Beispiel: Thread-Yielding. Wir haben das Thread-Yielding für den Fall mehrerer ID-Synchronisationsanforderungen eingeführt. Aus Laborberichten ging hervor, dass bei Kunden, die mehrere ID-Synchronisierungen durchführen, die Benutzeroberfläche aufgrund vieler kontinuierlicher CPU-Berechnungen blockiert wird. Infolgedessen haben wir Thread-Yielding eingeführt, um die ID-Synchronisierungsanforderungen jeweils um 100 ms zu trennen.

Diese Änderung verbessert die Performance für Kunden, die Visitor 2.3.0+ und DIL 6.10+ verwenden. Die Verbesserungen bei den Seitenladezeiten sind in der folgenden Abbildung dargestellt:

![](assets/id_sync_improvements_copy.png)

**Beeinträchtigen Browser-Anforderungen mit CORS im Vergleich zu JSON-P die Seiten-Performance?**

Ressourcenanforderungen mit CORS sind im Allgemeinen besser geeignet als Anforderungen mit JSONP. Bei JSONP weisen einige Browser Anforderungen eine geringere Priorität zu als anderen synchronen und asynchronen Abrufen, wenn sie diese in die Warteschlange stellen. Mit CORS wird sichergestellt, dass diese Anforderungen im Browser-Aufrufstapel mit einer höheren Priorität behandelt werden.

Siehe [CORS-Unterstützung im Besucher-ID-Service](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## Sicherheit {#section-b176b8492fbe4acfb79ebb30ec902f98}

**Unterstützt der Besucher-ID-Service CORS?**

Ja. Siehe [CORS-Unterstützung im Besucher-ID-Service](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Was ist CORS?**

*`Cross-Origin Resource Sharing`* oder CORS ist eine Methode, mit der Browser Ressourcen anfordern. Der Besucher-ID-Dienst fordert Ressourcen immer mit CORS in Browsern an, die ihn unterstützen. Der Besucher-ID-Dienst fordert Ressourcen mit JSON-P in älteren Browsern an, die CORS nicht unterstützen. Siehe [CORS-Unterstützung im Besucher-ID-Service](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Was geschieht, wenn meine Sicherheitsanforderungen so streng sind, dass ich JSONP nie verwenden möchte?**

Wenn Sie strenge Sicherheitsanforderungen haben, legen Sie die API-`useCORSOnly: true` für den Besucher-ID-Dienst fest. Sie sollten diesen Modus nur aktivieren, wenn Sie sicher sind, dass Ihre Site-Besucher Browser verwenden, die CORS unterstützen.

Siehe [CORS-Unterstützung im Besucher-ID-](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) und [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORELIKETHIS]
>
>* [Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html)

