---
description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich Analytics und des Experience Cloud Identity-Diensts.
keywords: Experience Cloud Identity-Dienst
seo-description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich Analytics und des Identity-Diensts.
seo-title: Häufig gestellte Fragen zu Analytics und zum Identity-Dienst
title: Häufig gestellte Fragen zu Analytics und zum Identity-Dienst
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Häufig gestellte Fragen zu Analytics und zum Identity-Dienst{#analytics-and-id-service-faqs}

Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich Analytics und des Identity-Diensts.

## Tracking-Server {#section-9a2ad7842e364c869e1650480d17f8ef}

**Wie finde ich die Informationen für meinen Tracking-Server?**

Jeder richtig konfigurierte AppMeasurement-Codeabschnitt enthält die Informationen für Ihren Tracking-Server.

In einigen Fällen teilen Kunden ihre Analytics AppMeasurement-Datei jedoch auf verschiedene Dateien auf. Beispielsweise verwenden einige Kunden eine Datei für Konfigurationsvariablen, eine zweite für Plug-ins und eine dritte für AppMeasurement-Code. Dies wird nicht empfohlen.

Wenn Sie Ihre Tracking-Server-Informationen nicht finden können, ist Ihre Analytics-Instanz möglicherweise nicht richtig konfiguriert. Wenden Sie sich an den [Kundendienst](https://helpx.adobe.com/marketing-cloud/contact-support.html), wenn Sie die Informationen für Ihren Tracking-Server nicht finden.

**Was geschieht, wenn ich den Identity-Dienst verwende und meinen Tracking-Server ändere?**

Es ändert sich nichts für Benutzer, die bereits durch den Identity-Dienst identifiziert wurden. Legacy-Besucher, die nicht zum Identity-Dienst migriert wurden und weiterhin mit einem Analytics-Cookie identifiziert werden, befinden sich in diesem Fall in der Schwebe. Die Anzahl der betroffenen Benutzer hängt davon ab, wie lange der Identity-Dienst aktiv war. Zum Beispiel verfügt eine Implementierung, bei der der Identity-Dienst 1 Woche lang aktiv war, möglicherweise über mehr Legacy-Benutzer als eine Implementierung, bei der der Identity-Dienst 6 Monate lang aktiv war, da Besucher, die zu dieser Site zurückkehren, bereits migriert worden wären.

## Implementierung und Konfiguration {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Muss ein CNAME für das domänenübergreifende Besuchertracking eingerichtet werden?**

Wenn eine Haupteinstiegssite vorhanden ist, über die Kunden vor dem Besuch weiterer Domänen identifiziert werden können, besteht die Möglichkeit, per CNAME das domänenübergreifende Tracking für Browser zu aktivieren, die keine Drittanbieter-Cookies akzeptieren (z. B. Safari).

In Browsern, die Drittanbieter-Cookies akzeptieren, wird bei der Anforderung ein Cookie in der [demdex.net-Domäne](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html) gesetzt, um eine Besucher-ID abzurufen. Mit diesem Cookie kann der Identity-Dienst für alle Domänen, die mit derselben Organisations-ID konfiguriert sind, dieselbe Experience Cloud-Besucher-ID zurückgeben. Für Browser, die keine Drittanbieter-Cookies akzeptieren, wird für jede Domäne eine neue Experience Cloud-Besucher-ID zugewiesen.

Auch wenn ein CNAME konfiguriert ist, werden Besucher bei Browsern, die keine Drittanbieter-Cookies akzeptieren, auf sekundärer Site und Hauptsite auf unterschiedliche Weise identifiziert, wenn nicht zuerst die Haupteinstiegssite besucht wird.

**Warum ist der Experience Cloud ID-Parameter (MID) nicht in der Analytics-Anforderung enthalten?**

Gibt der Identity-Dienst Informationen richtig zurück, ohne dass der `MID`-Parameter angezeigt wird, überprüfen Sie, ob Sie auf eine unterstützte Version von AppMeasurement aktualisiert haben.

**Können mit dem Identity-Dienst für eine Site H-Code und AppMeasurement für JavaScript verwendet werden?**

Ja. Vorausgesetzt, dass beide Dateien auf dieselbe VisitorAPI.js-Datei verweisen, können Sie eine Kombination aus H-Code und AppMeasurement für JavaScript für eine Site verwenden.

Auch wenn der H-Code im visitorAPI.js-Code Version 1.6 oder höher nicht unterstützt wird. Wenn Sie ein Upgrade auf visitorAPI.js Version 1.6 oder höher vornehmen möchten, kann der H-Code nicht mehr verwendet werden.

**Was ist eine Übergangsphase und wie konfiguriere ich sie?**

See [The Identity Service Grace Period](../reference/analytics-reference/grace-period.md) and contact [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**Warum muss ich zur Echtzeit-Datenerfassung (Real-time Data Collection, RDC) migrieren, um den Identity-Dienst zu verwenden?**

RDC bietet globale Leistungsverbesserungen und ist erforderlich, um sicherzustellen, dass Ihre Implementierung für künftige Funktionen bereit ist, die das globale Netzwerk der Edge-Hinweise von Adobe nutzen. Siehe [Analytics-Voraussetzungen: Regionale Datenerfassung (Regional Data Collection, RDC](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f)).

## Berichterstellung {#section-123cd55a32e54a45a23beb140becfa8f}

**Was sind mögliche Ursachen für Diskrepanzen bei der Verwendung von Analytics mit dem Identity-Dienst?**

Häufige Ursachen für Diskrepanzen bei der Verwendung des Identity-Diensts:

* Älterer Cookie s_vi wird weiterverwendet. Dies führt zu Diskrepanzen bei der Datenerfassung.
* Besucher, die von einer Umfrage zu einem Popup navigieren, werden doppelt gezählt.

## Cookies {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Was geschieht in Analytics, wenn der Identity-Dienst keinen AMCV-Cookie setzen kann?**

Es gibt drei mögliche Szenarios, in denen sich dies auf Analytics-Daten für neue Besucher auswirkt:

1. Ein Endbenutzer verlässt eine Seite, bevor die AMCV-Cookies erfolgreich gesetzt wurden (innerhalb eines Zeitüberschreitungsintervalls von 30 Sekunden).

   Wenn ein Besucher eine Seite verlässt, bevor sie geladen wurde, wird der Analytics-Treffer nicht gesendet. In diesem Szenario erhält Analytics keine Daten, die als verloren betrachtet werden, da die Seite zu früh geschlossen wurde. Im Rahmen von Tests, in denen auch entlegene Regionen berücksichtigt wurden, wurde festgestellt, dass dieses Szenario im Durchschnitt auf weniger als 1 % des Datenverkehrs zutrifft. Anzumerken ist, dass dieses Szenario zuweilen auch ohne den Identity-Dienst auftritt – es entsteht durch Einschluss des Analytics-Datenerfassungscodes unten auf der Seite.

1. Einem Endbenutzer wird kein Identity-Dienst oder keine Analytics-ID innerhalb des Zeitüberschreitungsintervalls von 30 Sekunden zugewiesen, da die Verbindung zu langsam ist oder das Ladesymbol im Browser „rotiert“.

   Weder der Identity-Dienst noch die Analytics-ID werden festgelegt und dem Besucher wird eine clientseitige ID zugewiesen. Dadurch können zwar Analytics-Daten erfasst werden, das Besucherprofil wird jedoch unterbrochen, wenn auf einer nachfolgenden Seite eine Analytics-ID festgelegt wird. Die clientseitige ID entspricht auch keinem bestehenden Besucherprofil, das in Audience Manager oder Analytics gespeichert ist. Darüber hinaus führt diese clientseitige ID in Analytics zu zwei unterschiedlichen Besuchern, wenn zwei verschiedene Domänen an dieselbe Report Suite gesendet werden.

1. Einem Endbenutzer wird innerhalb des Zeitüberschreitungsintervalls von 30 Sekunden statt einer ID des Identity-Diensts eine standardmäßige Analytics-Tracking-ID zugewiesen und die Übergangsphase wird nicht aktiviert.

   Szenario 3 führt zu dem gleichen Ergebnis wie Szenario 2, da eine clientseitige ID verwendet wird.

>[!TIP]
>
>Wenn Sie die neuesten Versionen von VisitorAPI.js und AppMeasurement.js mit den Standardeinstellungen verwenden, sollten Sie alle schwerwiegenden oder spürbaren Folgen der drei oben beschriebenen Szenarios vermeiden können.

>[!MORE_LIKE_THIS]
>
>* [Kundenunterstützung](https://helpx.adobe.com/marketing-cloud/contact-support.html)

