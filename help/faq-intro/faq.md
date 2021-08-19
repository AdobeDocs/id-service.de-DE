---
description: Häufig gestellte Fragen zu den Funktionen und Problemen bezüglich des ID-Diensts.
keywords: 'ID-Dienst '
title: Häufig gestellte Fragen zum ID-Dienst
exl-id: 4dd2220c-8a9d-4e27-838b-be5ad357cb3e
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '787'
ht-degree: 100%

---

# Häufig gestellte Fragen zum ID-Dienst{#id-service-faqs}

Häufig gestellte Fragen zu den Funktionen und Problemen bezüglich des ID-Diensts.

## Funktionalität {#section-659e89f8b9a74cb8afff35587dc96836}

**Welche Art von Funktionalität oder Funktionen bietet der ID-Dienst?**

Siehe  [Übersicht](../introduction/overview.md).

**Warum führt der ID-Dienst keinen Aufruf zum Abruf der Experience Cloud ID aus?**

Das kann schwer zu diagnostizieren sein. Sie können die Header der Inhaltssicherheitsrichtlinien auf Ihrer Site überprüfen. Wenn Sie über eine strenge Sicherheitsrichtlinie verfügen, können diese Einstellungen die vom ID-Dienst ausgeführten Aufrufe von Drittanbietern blockieren. Siehe [Inhaltssicherheitsrichtlinien und der Experience Cloud Identity-Dienst](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3).

**Speicherung der VisitorAPI.js-Datei**

Möglicherweise treten Probleme auf, wenn Sie die VisitorAPI.js-Datei als lokale Datei in Apps hosten. Es wird empfohlen, die Datei auf einem Webserver zu hosten.

## Seitenladezeiten und Latenz {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**Wie wirkt sich die Platzierung der ID-Dienstbibliothek VisitorAPI.js auf die Seitenladezeiten aus?**

Platzieren Sie die Bibliothek VisitorAPI.js oben auf der Seite in den `<head>` Abschnitt Ihres Codes. Dadurch stellen Sie sicher, dass der Aufruf an eine ID gesendet wird, bevor der Seitentext geladen wird, und die Wahrscheinlichkeit, dass eine ID erfolgreich zurückgegeben wird, erhöht sich.

Der ID-Dienst-Aufruf ist asynchron und der einzige Aufruf zur [Domäne „demdex.net“](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=de). Der Aufruf des ID-Diensts verhindert nicht, dass andere Elemente auf der Seite geladen werden.

Für [!DNL Target]-Kunden kann die Platzierung von ID-Dienst-Code in `<body>` der Seite die Wahrscheinlichkeit erhöhen, dass ein [!DNL Target]-Aufruf blockiert wird. Wenn Sie ID-Dienst-Code im Haupttext Ihrer Seite platzieren müssen, dann sollten Sie ihn nach dem öffnenden `<body>`-Tag einfügen.

**Führt der ID-Dienst bei jedem Laden der Seite einen Server-Aufruf durch?**

Nein, dieser Aufruf erfolgt nur beim ersten Rendern der Seite und danach alle 7 Tage. In der Zwischenzeit sind keine Server-Aufrufe erforderlich. Der ID-Dienst arbeitet im Client-seitigen Modus und muss keinen Server-Aufruf durchführen, um eine ID zurückzugeben.

Siehe [Übersicht](../introduction/overview.md).

**Was kann bei Verwendung des ID-Diensts zu langsamen Seitenladezeiten oder zu Beeinträchtigungen des Kundenerlebnisses führen?**

Es ist schwierig, alle möglichen Bedingungen zu katalogisieren. Milliarden von Verbraucher-Clients verbinden sich mit unseren Diensten, und die enorme Vielfalt, wo und wie sie sich verbinden, wirkt sich auf die Leistung aus. Beispiel:

* Die Geschwindigkeiten in Mobilfunknetzen sind sehr unterschiedlich. Diese Netzwerke leiden auch unter Signal- und Daten- oder Sprachpaketverlusten.
* Die Konnektivität leidet bei Geräten, die unter verschiedenen Bedingungen eine Verbindung über WLAN herstellen. Beispielsweise treten Paketverluste und Geschwindigkeitsprobleme häufig an öffentlichen Orten wie Cafés oder in anderen Umgebungen wie Flugzeugen auf, wo Pakete über Satelliten geleitet werden müssen, bevor sie terrestrische Netzwerke erreichen.
* Schlecht konfigurierte lokale Netzwerke können die Konnektivität und Geschwindigkeit negativ beeinflussen.
* Client-Geräte können ihre eigenen Probleme haben, wie z. B. zu wenig Arbeitsspeicher, übermäßiger Speicheraustausch oder begrenzte CPU-Leistung im Verhältnis zur aktuellen Arbeitslast.
* Browser verwenden je nach Hersteller und Version verschiedene Regeln, um Remote-Server-Aufrufe in die Warteschlange zu stellen, auszuführen und zu verarbeiten. Dieses Verhalten wirkt sich auf Geschwindigkeit und Leistung aus.

**Können Sie einige Verbesserungen nennen, die Sie vorgenommen haben, um die Seitenladezeit zu verkürzen?**

Beispiel: Thread-Yielding. Wir haben das Thread-Yielding für den Fall mehrerer ID-Synchronisationsanforderungen eingeführt. Aus Laborberichten ging hervor, dass bei Kunden, die mehrere ID-Synchronisierungen durchführen, die Benutzeroberfläche aufgrund vieler kontinuierlicher CPU-Berechnungen blockiert wird. Infolgedessen haben wir Thread-Yielding eingeführt, um die ID-Synchronisierungsanforderungen jeweils um 100 ms zu trennen.

Diese Änderung verbessert die Leistung für Kunden, die Visitor 2.3.0+ und DIL 6.10+ verwenden. Die Verbesserungen bei den Seitenladezeiten sind in der folgenden Abbildung dargestellt:

![](assets/id_sync_improvements_copy.png)

**Beeinträchtigen Browser-Anforderungen mit CORS im Vergleich zu JSON-P die Seitenleistung?**

Ressourcenanforderungen mit CORS sind im Allgemeinen besser geeignet als Anforderungen mit JSONP. Bei JSONP weisen einige Browser Anforderungen eine geringere Priorität zu als anderen synchronen und asynchronen Abrufen, wenn sie diese in die Warteschlange stellen. Mit CORS wird sichergestellt, dass diese Anforderungen im Browser-Aufrufstapel mit einer höheren Priorität behandelt werden.

Siehe [CORS-Unterstützung im Experience Cloud Identity-Dienst](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## Sicherheit {#section-b176b8492fbe4acfb79ebb30ec902f98}

**Unterstützt der ID-Dienst CORS?**

Ja. Siehe [CORS-Unterstützung im Experience Cloud Identity-Dienst](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Was ist CORS?**

*`Cross-Origin Resource Sharing`* oder CORS ist eine Methode, mit der Browser Ressourcen anfordern. In Browsern an, die CORS unterstützen, fordert der ID-Dienst die Ressourcen immer mit CORS an. In älteren Browsern an, die CORS nicht unterstützen, fordert der ID-Dienst die Ressourcen mit JSON-P an. Weitere Informationen finden Sie unter [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Was geschieht, wenn meine Sicherheitsanforderungen so streng sind, dass ich JSONP nie verwenden möchte?**

Wenn Sie strenge Sicherheitsanforderungen haben, legen Sie in der Konfiguration der ID-Dienst-API `useCORSOnly: true` fest. Sie sollten diesen Modus nur dann aktivieren, wenn Sie davon überzeugt sind, dass Ihre Site-Besucher Browser verwenden, die CORS unterstützen.

Siehe [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) und [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORELIKETHIS]
>
>* [Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html)

