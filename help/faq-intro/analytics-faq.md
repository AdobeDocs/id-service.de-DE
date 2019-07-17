---
description: Häufig gestellte Fragen zu Funktionen, Funktionen und Problemen im Zusammenhang mit der Verwendung von Analytics mit dem Experience Cloud-Identitätsdienst
keywords: Experience Cloud-Identitätsdienst
seo-description: Häufig gestellte Fragen zu Funktionen, Funktionen und Problemen im Zusammenhang mit der Verwendung von Analytics mit dem Identitätsdienst.
seo-title: Häufig gestellte Fragen zu Analytics und Identitätsdienst
title: Häufig gestellte Fragen zu Analytics und Identitätsdienst
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Analytics and Identity Service FAQs{#analytics-and-id-service-faqs}

Häufig gestellte Fragen zu Funktionen, Funktionen und Problemen im Zusammenhang mit der Verwendung von Analytics mit dem Identitätsdienst.

## Tracking-Server {#section-9a2ad7842e364c869e1650480d17f8ef}

**Wie finde ich die Informationen für meinen Tracking-Server?**

Jeder richtig konfigurierte AppMeasurement-Codeabschnitt enthält die Informationen für Ihren Tracking-Server.

In einigen Fällen teilen Kunden ihre Analytics AppMeasurement-Datei jedoch auf verschiedene Dateien auf. Beispielsweise verwenden einige Kunden eine Datei für Konfigurationsvariablen, eine zweite für Plug-ins und eine dritte für AppMeasurement-Code. Dies wird nicht empfohlen.

Wenn Sie Ihre Tracking-Server-Informationen nicht finden können, ist Ihre Analytics-Instanz möglicherweise nicht richtig konfiguriert. Wenden Sie sich an den [Kundendienst](https://helpx.adobe.com/marketing-cloud/contact-support.html), wenn Sie die Informationen für Ihren Tracking-Server nicht finden.

**Was passiert, wenn ich den Identitätsdienst verwende und meinen Tracking-Server ändere?**

Für Benutzer, die bereits durch den Identitätsdienst identifiziert wurden, ändert sich nichts. Veraltete Besucher, die nicht zum Identitätsdienst migriert wurden und weiterhin mit einem Analytics-Cookie identifiziert wurden, werden abgeschnitten. Die Anzahl der betroffenen Benutzer hängt davon ab, wie lange der Identitätsdienst aktiv war. Beispielsweise verfügt eine Implementierung, bei der der Identitätsdienst für 1 Woche aktiv war, möglicherweise über mehr alte Benutzer als eine Implementierung, bei der der Identitätsdienst für 6 Monate aktiv war, da die Benutzer, die zur Site zurückkehren, migriert worden wären.

## Implementierung und Konfiguration {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Muss ein CNAME für das domänenübergreifende Besuchertracking eingerichtet werden?**

Wenn eine Haupteinstiegssite vorhanden ist, über die Kunden vor dem Besuch weiterer Domänen identifiziert werden können, besteht die Möglichkeit, per CNAME das domänenübergreifende Tracking für Browser zu aktivieren, die keine Drittanbieter-Cookies akzeptieren (z. B. Safari).

In Browsern, die Drittanbieter-Cookies akzeptieren, wird bei der Anforderung ein Cookie in der [demdex.net-Domäne](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html) gesetzt, um eine Besucher-ID abzurufen. Mit diesem Cookie kann der Identitätsdienst dieselbe Experience Cloud-Besucher-ID für alle Domänen zurückgeben, die mit derselben Organisations-ID konfiguriert sind. Für Browser, die keine Drittanbieter-Cookies akzeptieren, wird für jede Domäne eine neue Experience Cloud-Besucher-ID zugewiesen.

Auch wenn ein CNAME konfiguriert ist, werden Besucher bei Browsern, die keine Drittanbieter-Cookies akzeptieren, auf sekundärer Site und Hauptsite auf unterschiedliche Weise identifiziert, wenn nicht zuerst die Haupteinstiegssite besucht wird.

**Warum ist der Experience Cloud ID-Parameter (MID) nicht in der Analytics-Anforderung enthalten?**

If the Identity Service is returning information correctly but you do not see the `MID` parameter, make sure that you've upgraded to a supported version of AppMeasurement.

**Kann meine Site H-Code und appmeasurement für javascript mit dem Identitätsdienst verwenden?**

Ja. Vorausgesetzt, dass beide Dateien auf dieselbe VisitorAPI.js-Datei verweisen, können Sie eine Kombination aus H-Code und AppMeasurement für JavaScript für eine Site verwenden.

Auch wenn der H-Code im visitorAPI.js-Code Version 1.6 oder höher nicht unterstützt wird. Wenn Sie ein Upgrade auf visitorAPI.js Version 1.6 oder höher vornehmen möchten, kann der H-Code nicht mehr verwendet werden.

**Was ist eine Übergangsphase und wie konfiguriere ich sie?**

See [The Identity Service Grace Period](../reference/analytics-reference/grace-period.md) and contact [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**Warum muss ich zur Echtzeit-Datenerfassung (Real-Time Data Collection, RDC) migrieren, um den Identitätsdienst zu verwenden?**

RDC bietet globale Leistungsverbesserungen und ist erforderlich, um sicherzustellen, dass Ihre Implementierung für künftige Funktionen bereit ist, die das globale Netzwerk der Edge-Hinweise von Adobe nutzen. Siehe [Analytics-Voraussetzungen: Regionale Datenerfassung (Regional Data Collection, RDC](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f)).

## Berichterstellung {#section-123cd55a32e54a45a23beb140becfa8f}

**Was sind mögliche Ursachen für Diskrepanzen bei der Verwendung von Analytics mit dem Identitätsdienst?**

Häufige Ursachen für Diskrepanzen bei der Verwendung des Identitätsdiensts:

* Älterer Cookie s_vi wird weiterverwendet. Dies führt zu Diskrepanzen bei der Datenerfassung.
* Besucher, die von einer Umfrage zu einem Popup navigieren, werden doppelt gezählt.

## Cookies {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Was geschieht in Analytics, wenn der Identitätsdienst das AMCV-Cookie nicht festlegen kann?**

Es gibt drei mögliche Szenarios, in denen sich dies auf Analytics-Daten für neue Besucher auswirkt:

1. Ein Endbenutzer verlässt eine Seite, bevor die AMCV-Cookies erfolgreich gesetzt wurden (innerhalb eines Zeitüberschreitungsintervalls von 30 Sekunden).

   Wenn ein Besucher eine Seite verlässt, bevor sie geladen wurde, wird der Analytics-Treffer nicht gesendet. In diesem Szenario erhält Analytics keine Daten, die als verloren betrachtet werden, da die Seite zu früh geschlossen wurde. Im Rahmen von Tests, in denen auch entlegene Regionen berücksichtigt wurden, wurde festgestellt, dass dieses Szenario im Durchschnitt auf weniger als 1 % des Datenverkehrs zutrifft. Beachten Sie, dass dieses Szenario manchmal auch ohne den Identitätsdienst auftritt. Es handelt sich um ein Artefakt der Einbeziehung des Analytics-Datenerfassungscodes am unteren Rand der Seite.

1. Dem Endbenutzer wird aufgrund langsamer Verbindungen oder Browser "roinning" kein Identitätsdienst oder eine Analytics-ID innerhalb des 30-Sekunden-Zeitlimits zugewiesen.

   Sowohl der Identitätsdienst als auch die Analytics-ID würden nicht festgelegt und dem Besucher würde eine clientseitige ID zugewiesen. Dadurch können zwar Analytics-Daten erfasst werden, das Besucherprofil wird jedoch unterbrochen, wenn auf einer nachfolgenden Seite eine Analytics-ID festgelegt wird. Die clientseitige ID entspricht auch keinem bestehenden Besucherprofil, das in Audience Manager oder Analytics gespeichert ist. Darüber hinaus führt diese clientseitige ID in Analytics zu zwei unterschiedlichen Besuchern, wenn zwei verschiedene Domänen an dieselbe Report Suite gesendet werden.

1. Dem Endbenutzer wird innerhalb des 30-Sekunden-Zeitfensters keine Identitätsdienst-ID zugewiesen, es wird jedoch eine Standard-Analytics-Tracking-ID zugewiesen und die Übergangsphase ist nicht aktiviert.

   Szenario 3 führt zu dem gleichen Ergebnis wie Szenario 2, da eine clientseitige ID verwendet wird.

>[!TIP]
>
>Wenn Sie die neuesten Versionen von VisitorAPI.js und AppMeasurement.js mit den Standardeinstellungen verwenden, sollten Sie alle schwerwiegenden oder spürbaren Folgen der drei oben beschriebenen Szenarios vermeiden können.

>[!MORE_LIKE_THIS]
>
>* [Kundenunterstützung](https://helpx.adobe.com/marketing-cloud/contact-support.html)

