---
description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich Analytics und des ID-Diensts.
keywords: ID-Dienst
seo-description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich Analytics und des ID-Diensts.
seo-title: Häufig gestellte Fragen zu Analytics und zum ID-Dienst
title: Häufig gestellte Fragen zu Analytics und zum ID-Dienst
uuid: 35 ed 79 a 9-eccc -4 b 54-8451-606 f 091 c 73 b 7
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Häufig gestellte Fragen zu Analytics und zum ID-Dienst{#analytics-and-id-service-faqs}

Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich Analytics und des ID-Diensts.

## Tracking-Server {#section-9a2ad7842e364c869e1650480d17f8ef}

**Wie finde ich die Informationen für meinen Tracking-Server?**

Jeder richtig konfigurierte AppMeasurement-Codeabschnitt enthält die Informationen für Ihren Tracking-Server.

In einigen Fällen teilen Kunden ihre Analytics AppMeasurement-Datei jedoch auf verschiedene Dateien auf. Beispielsweise verwenden einige Kunden eine Datei für Konfigurationsvariablen, eine zweite für Plug-ins und eine dritte für AppMeasurement-Code. Dies wird nicht empfohlen.

Wenn Sie die Informationen für Ihren Tracking-Server nicht finden, ist Ihre Analytics-Instanz möglicherweise nicht richtig konfiguriert. Wenden Sie sich an den [Kundendienst](https://helpx.adobe.com/marketing-cloud/contact-support.html), wenn Sie die Informationen für Ihren Tracking-Server nicht finden.

**Was geschieht, wenn ich den ID-Dienst verwende und meinen Tracking-Server ändere?**

Es ändert sich nichts für Benutzer, die bereits durch den ID-Dienst identifiziert wurden. Bestehende Besucher, die nicht zum ID-Dienst migriert haben und weiterhin mit einem Analytics-Cookie identifiziert werden, befinden sich in diesem Fall in der Schwebe. Die Anzahl der betroffenen Benutzer hängt davon ab, wie lange der ID-Dienst aktiv war. Zum Beispiel verfügt eine Implementierung, bei der der ID-Dienst für 1 Woche aktiv war, möglicherweise über mehr bestehende Benutzer als bei einer Implementierung, bei der der ID-Dienst für 6 Monate aktiv war, da die zu dieser Site zurückkehrenden Benutzer migriert würden.

## Implementierung und Konfiguration {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Muss ein CNAME für das domänenübergreifende Besuchertracking eingerichtet werden?**

Wenn eine Haupteinstiegssite vorhanden ist, über die Kunden vor dem Besuch weiterer Domänen identifiziert werden können, besteht die Möglichkeit, per CNAME das domänenübergreifende Tracking für Browser zu aktivieren, die keine Drittanbieter-Cookies akzeptieren (z. B. Safari).

In Browsern, die Drittanbieter-Cookies akzeptieren, wird bei der Anforderung ein Cookie in der [demdex.net-Domäne](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html) gesetzt, um eine Besucher-ID abzurufen. Mit diesem Cookie kann der ID-Dienst für alle Domänen, die mit derselben Organisations-ID konfiguriert sind, dieselbe Experience Cloud-Besucher-ID zurückgeben. Für Browser, die keine Drittanbieter-Cookies akzeptieren, wird für jede Domäne eine neue Experience Cloud-Besucher-ID zugewiesen.

Auch wenn ein CNAME konfiguriert ist, werden Besucher bei Browsern, die keine Drittanbieter-Cookies akzeptieren, auf sekundärer Site und Hauptsite auf unterschiedliche Weise identifiziert, wenn nicht zuerst die Haupteinstiegssite besucht wird.

**Warum ist der Experience Cloud ID-Parameter (MID) nicht in der Analytics-Anforderung enthalten?**

Gibt der ID-Dienst Informationen richtig zurück, ohne dass der `MID`-Parameter angezeigt wird, überprüfen Sie, ob Sie auf eine unterstützte Version von AppMeasurement aktualisiert haben.

**Können mit dem ID-Dienst für eine Site H-Code und AppMeasurement für JavaScript verwendet werden**?

Ja. Vorausgesetzt, dass beide Dateien auf dieselbe VisitorAPI.js-Datei verweisen, können Sie eine Kombination aus H-Code und AppMeasurement für JavaScript für eine Site verwenden.

Auch wenn der H-Code im visitorAPI.js-Code Version 1.6 oder höher nicht unterstützt wird. Wenn Sie ein Upgrade auf visitorAPI.js Version 1.6 oder höher vornehmen möchten, kann der H-Code nicht mehr verwendet werden.

**Was ist eine Übergangsphase und wie konfiguriere ich sie?**

Weitere Informationen finden Sie unter [Die Übergangsphase für den ID-Dienst](../reference/analytics-reference/grace-period.md) und wenden [Sie sich an den Kundendienst](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**Warum muss ich zur Echtzeit-Datenerfassung (Real-time Data Collection, RDC) migrieren, um den ID-Dienst zu verwenden?**

RDC bietet globale Leistungsverbesserungen und ist erforderlich, um sicherzustellen, dass Ihre Implementierung für künftige Funktionen bereit ist, die das globale Netzwerk der Edge-Hinweise von Adobe nutzen. Siehe [Analytics-Voraussetzungen: Regionale Datenerfassung (Regional Data Collection, RDC](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f)).

## Berichterstellung {#section-123cd55a32e54a45a23beb140becfa8f}

**Was sind mögliche Ursachen für Diskrepanzen bei der Verwendung von Analytics mit dem ID-Dienst?**

Häufige Ursachen für Diskrepanzen bei der Verwendung des ID-Diensts:

* Älterer Cookie s_vi wird weiterverwendet. Dies führt zu Diskrepanzen bei der Datenerfassung.
* Besucher, die von einer Umfrage zu einem Popup navigieren, werden doppelt gezählt.

## Cookies {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Was geschieht in Analytics, wenn der ID-Dienst keinen AMCV-Cookie setzen kann?**

Es gibt drei mögliche Szenarios, in denen sich dies auf Analytics-Daten für neue Besucher auswirkt:

1. Ein Endbenutzer verlässt eine Seite, bevor die AMCV-Cookies erfolgreich gesetzt wurden (innerhalb eines Zeitüberschreitungsintervalls von 30 Sekunden).

   Wenn ein Besucher eine Seite verlässt, bevor sie geladen wurde, wird der Analytics-Treffer nicht gesendet. In diesem Szenario erhält Analytics keine Daten, die als verloren betrachtet werden, da die Seite zu früh geschlossen wurde. Im Rahmen von Tests, in denen auch entlegene Regionen berücksichtigt wurden, wurde festgestellt, dass dieses Szenario im Durchschnitt auf weniger als 1 % des Datenverkehrs zutrifft. Beachten Sie, dass dieses Szenario manchmal auch ohne den MCID-Dienst auftritt. Es handelt sich um ein Artefakt der Einbeziehung des Analytics-Datenerfassungscodes am unteren Rand der Seite.

1. Einem Endbenutzer wird kein ID-Dienst oder keine Analytics-ID innerhalb des Zeitüberschreitungsintervalls von 30 Sekunden zugewiesen, da die Verbindung zu langsam ist oder das Ladesymbol im Browser „rotiert“.

   Weder der ID-Dienst noch die Analytics-ID werden festgelegt und dem Besucher wird eine clientseitige ID zugewiesen. Dadurch können zwar Analytics-Daten erfasst werden, das Besucherprofil wird jedoch unterbrochen, wenn auf einer nachfolgenden Seite eine Analytics-ID festgelegt wird. Die clientseitige ID entspricht auch keinem bestehenden Besucherprofil, das in Audience Manager oder Analytics gespeichert ist. Darüber hinaus führt diese clientseitige ID in Analytics zu zwei unterschiedlichen Besuchern, wenn zwei verschiedene Domänen an dieselbe Report Suite gesendet werden.

1. Einem Endbenutzer wird innerhalb des Zeitüberschreitungsintervalls von 30 Sekunden statt einer ID des ID-Diensts eine standardmäßige Analytics-Tracking-ID zugewiesen und die Übergangsphase wird nicht aktiviert.

   Szenario 3 führt zu dem gleichen Ergebnis wie Szenario 2, da eine clientseitige ID verwendet wird.

>[!TIP]
>
>Die Verwendung der aktuellen Updates für visitorapi. js und appmeasurement. js mit den Standardeinstellungen sollte schwerwiegende oder spürbare Auswirkungen aus den drei obigen Szenarien vermeiden.

>[!MORE_ LIKE_ THIS]
>
>* [Kundenunterstützung](https://helpx.adobe.com/marketing-cloud/contact-support.html)

