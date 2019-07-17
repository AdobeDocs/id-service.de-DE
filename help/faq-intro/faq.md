---
description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich des ID-Diensts.
keywords: ID-Dienst
seo-description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich des ID-Diensts.
seo-title: ID-Dienst Häufig gestellte Fragen (FAQ)
title: Häufig gestellte Fragen zum ID-Dienst
uuid: e8d8f819-3d73-4fa2-864c-4867071c14ee
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Häufig gestellte Fragen zum ID-Dienst{#id-service-faqs}

Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich des ID-Diensts.

## Funktionalität {#section-659e89f8b9a74cb8afff35587dc96836}

**Welche Art von Funktionalität oder Funktionen bietet der ID-Dienst?**

Siehe [Übersicht](../introduction/overview.md).

**Warum führt der ID-Dienst keinen Aufruf durch, um die Experience Cloud ID abzurufen?**

Der Grund lässt sich schwer feststellen. Sie können aber beispielsweise die Header für die Inhaltssicherheitsrichtlinie auf Ihrer Site prüfen. Wenn Sie eine strenge Inhaltssicherheitsrichtlinie durchsetzen, können die vom ID-Dienst ausgeführten Drittanbieteraufrufe durch diese Einstellungen blockiert werden. Siehe [Content Security Policies und Experience Cloud-Identitätsdienst](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3).

**VisitorAPI.js-Dateispeicherung**

Möglicherweise treten Probleme auf, wenn Sie VisitorAPI.js als lokale Datei in mobilen Apps speichern. Es wird empfohlen, die Datei auf einem Webserver zu speichern.

## Seitenladezeiten und Latenz {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**Wie wirkt sich die Platzierung der ID-Dienstbibliothek VisitorAPI.js auf die Seitenladezeiten aus?**

Platzieren Sie die Bibliothek VisitorAPI.js oben auf der Seite in den `<head>` Abschnitt Ihres Codes. Dadurch stellen Sie sicher, dass der Aufruf an eine ID gesendet wird, bevor der Seitentext geladen wird, und die Wahrscheinlichkeit, dass eine ID erfolgreich zurückgegeben wird, erhöht sich.

Der Aufruf des ID-Diensts erfolgt asynchron. Es ist der einzige Aufruf an die [demdex.net-Domäne](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html). Der Aufruf des ID-Diensts verhindert nicht, dass andere Elemente auf der Seite geladen werden.

Für [!DNL Target]-Kunden kann die Platzierung von ID-Dienst-Code in `<body>` der Seite die Wahrscheinlichkeit erhöhen, dass ein [!DNL Target]-Aufruf blockiert wird. Wenn Sie ID-Dienst-Code im Haupttext Ihrer Seite platzieren müssen, dann sollten Sie ihn nach dem öffnenden `<body>`-Tag einfügen.

**Führt der ID-Dienst jedes Mal einen Server-Aufruf durch, wenn eine Seite geladen wird?**

Nein, dieser Aufruf wird nur beim ersten Rendern der Seite durchgeführt und danach alle sieben Tage. In der Zwischenzeit sind keine Serveraufrufe erforderlich. Der ID-Dienst wird im clientseitigen Modus ausgeführt und benötigt keine Server-Aufrufe, um eine ID zurückzugeben.

Siehe [Übersicht](../introduction/overview.md).

**Was kann bei der Verwendung des ID-Diensts zu langsamen Seitenladezeiten führen oder die Benutzererfahrung beeinträchtigen?**

Es ist schwierig, alle möglichen Bedingungen aufzuführen. Milliarden von Anwenderclients verbinden sich mit unseren Diensten. Standort und Art der Verbindung können sich auf vielfältige Weise auf die Leistung auswirken. Beispiel:

* Die Geschwindigkeit in Mobilfunknetzen kann erheblich schwanken. Außerdem kann es in diesen Netzen zu Signal- und Daten- oder Sprachpaketverlust kommen.
* Eine Vielzahl von Bedingungen kann sich auf die Konnektivität von Geräten auswirken, die eine Verbindung über WLAN herstellen. Beispielsweise sind Paketverlust und langsame Verbindungen ein häufiges Problem an öffentlichen Orten wie Cafés oder in Flugzeugen, wenn Pakete über Satellit geleitet werden, bevor sie das Funknetz am Boden erreichen.
* Schlecht konfigurierte lokale Netzwerke können sich negativ auf die Konnektivität und die Geschwindigkeit auswirken.
* Clientgeräte können mit eigenen Problemen behaftet sein, beispielsweise unzureichendem Arbeitsspeicher, übermäßiger Datenträgerauslagerung oder zu wenig CPU-Leistung für die aktuelle Auslastung.
* Wenn Browser Remote-Serveraufrufe in Warteschlangen stellen oder ausführen oder sogar Antworten verarbeiten, dann wenden sie eine Vielzahl unterschiedlicher Regeln an, die vom Browseranbieter und der Version abhängig sind. Dieses Verhalten wirkt sich auf die Geschwindigkeit und die Leistung aus.

**Können Sie einige Verbesserungen nennen, die Sie zur Verkürzung von Seitenladezeiten vorgenommen haben?**

Beispielsweise Thread-Yielding. Thread-Yielding wurde für Fälle eingeführt, in denen mehrere ID-Synchronisierungsanforderungen gesendet werden. In Laborberichten wurde beobachtet, dass die UI blockiert wird, wenn bei Kunden, die zahlreiche ID-Synchronisierungen ausführen, viele CPU-Berechnungen gleichzeitig ausgeführt werden. Daher wurde Thread-Yielding eingeführt, um die ID-Synchronisierungsanforderungen um je 100 Millisekunden zu trennen.

Diese Änderung erhöht die Leistung bei Kunden, die Visitor 2.3.0 oder höher und DIL 6.10 oder höher verwenden. Die Verbesserungen der Seitenladezeiten werden in der folgenden Abbildung gezeigt:

![](assets/id_sync_improvements_copy.png)

**Wirken sich Browseranforderungen, in denen CORS statt JSONP verwendet wird, auf die Seitenleistung aus?**

Ressourcenanforderungen mit CORS sind JSONP in der Regel vorzuziehen. Bei JSONP weisen einige Browser Anforderungen eine geringere Priorität zu als anderen synchronen und asynchronen Abrufen, wenn sie diese in die Warteschlange stellen. Mit CORS können Sie sicherstellen, dass die Anforderungen eine höhere Priorität in der Aufrufliste des Browsers erhalten.

Siehe [CORS-Unterstützung im Experience Cloud-Identitätsdienst](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## Sicherheit {#section-b176b8492fbe4acfb79ebb30ec902f98}

**Unterstützt der ID-Dienst CORS?**

Ja. See [CORS Support in the Experience Cloud Identity Service](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Was ist CORS?**

*`Cross-Origin Resource Sharing`* oder CORS ist eine Methode, mit der Browser Ressourcen anfordern. In Browsern, die CORS unterstützen, fordert der ID-Dienst Ressourcen immer mit CORS an. Der ID-Dienst fordert Ressourcen mit JSONP in älteren Browsern an, die CORS nicht unterstützen. Weitere Informationen finden Sie unter [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Was geschieht, wenn meine Sicherheitsanforderungen so streng sind, dass ich JSONP nie verwenden möchte?**

Wenn Sie strenge Sicherheitsanforderungen haben, legen Sie in der Konfiguration der ID-Dienst-API `useCORSOnly: true` fest. Sie sollten diesen Modus nur dann aktivieren, wenn Sie davon überzeugt sind, dass alle Site-Besucher Browser verwenden, die CORS unterstützen.

Siehe [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) und [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORE_LIKE_THIS]
>
>* [Kundenunterstützung](https://helpx.adobe.com/marketing-cloud/contact-support.html)

