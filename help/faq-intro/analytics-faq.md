---
description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich Analytics und des Experience Cloud Identity-Diensts.
keywords: Experience Cloud Identity Service
seo-description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich Analytics und des Identity-Diensts.
seo-title: Häufig gestellte Fragen zu Analytics und zum Identity-Dienst
title: Häufig gestellte Fragen zu Analytics und zum Identity-Dienst
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Häufig gestellte Fragen zu Analytics und zum Identity-Dienst{#analytics-and-id-service-faqs}

Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bezüglich Analytics und des Identity-Diensts.

## Tracking-Server {#section-9a2ad7842e364c869e1650480d17f8ef}

**Wie finde ich meine Tracking-Server-Informationen?**

Jeder richtig konfigurierte Teil des AppMeasurement-Codes enthält Ihre Informationen zum Tracking-Server.

Manchmal können Kunden jedoch ihre Analytics-AppMeasurement-Datei in separate Dateien aufteilen. Einige Kunden können beispielsweise Konfigurationsvariablen in eine Datei setzen, eine zweite Datei für Plug-Ins verwenden und dann AppMeasurement-Code in eine dritte Datei einfügen. Dies wird nicht empfohlen.

Wenn Sie Ihre Tracking-Server-Informationen nicht finden können, ist Ihre Analytics-Instanz möglicherweise nicht richtig konfiguriert. Wenden Sie sich an den [Kundendienst](https://helpx.adobe.com/de/marketing-cloud/contact-support.html) , wenn Sie Ihre Informationen zum Tracking-Server nicht finden können.

**Was geschieht, wenn ich den Identity-Dienst verwende und meinen Tracking-Server ändere?**

Es ändert sich nichts für Benutzer, die bereits durch den Identity-Dienst identifiziert wurden. Legacy-Besucher, die nicht zum Identity-Dienst migriert wurden und weiterhin mit einem Analytics-Cookie identifiziert werden, befinden sich in diesem Fall in der Schwebe. Die Anzahl der betroffenen Benutzer hängt davon ab, wie lange der Identity-Dienst aktiv war. Zum Beispiel verfügt eine Implementierung, bei der der Identity-Dienst 1 Woche lang aktiv war, möglicherweise über mehr Legacy-Benutzer als eine Implementierung, bei der der Identity-Dienst 6 Monate lang aktiv war, da Besucher, die zu dieser Site zurückkehren, bereits migriert worden wären.

## Implementierung und Konfiguration {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Muss ich einen CNAME einrichten, um Besucher domänenübergreifend zu verfolgen?**

Wenn eine Haupteinstiegssite vorhanden ist, über die Kunden vor dem Besuch weiterer Domänen identifiziert werden können, besteht die Möglichkeit, per CNAME das domänenübergreifende Tracking für Browser zu aktivieren, die keine Drittanbieter-Cookies akzeptieren (z. B. Safari).

In browsers that accept third-party cookies, a cookie is set in the [demdex.net domain](https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/reference/demdex-calls.html) during the request to retrieve a visitor ID. Mit diesem Cookie kann der Identity-Dienst für alle Domänen, die mit derselben Organisations-ID konfiguriert sind, dieselbe Experience Cloud-Besucher-ID zurückgeben. Für Browser, die keine Drittanbieter-Cookies akzeptieren, wird für jede Domäne eine neue Experience Cloud-Besucher-ID zugewiesen.

Selbst wenn ein CNAME konfiguriert ist und die Haupteinstiegssite nicht zuerst besucht wird, werden Besucher in Browsern, die keine Drittanbieter-Cookies akzeptieren, auf der sekundären Site und auf der Hauptsite unterschiedlich identifiziert.

**Warum ist der Parameter Experience Cloud ID (MID) nicht in der Analytics-Anforderung enthalten?**

Gibt der Identity-Dienst Informationen richtig zurück, ohne dass der `MID`-Parameter angezeigt wird, überprüfen Sie, ob Sie auf eine unterstützte Version von AppMeasurement aktualisiert haben.

**Können mit dem Identity-Dienst für eine Site H-Code und AppMeasurement für JavaScript verwendet werden?**

Ja. Solange beide Dateien auf dieselbe VisitorAPI.js-Datei verweisen, können Sie eine Mischung aus H-Code und AppMeasurement für JavaScript auf Ihrer Site verwenden.

H-Code wird jedoch nicht mit dem Code visitorAPI.js Version 1.6 oder höher unterstützt. Wenn Sie auf visitorAPI.js v 1.6 (oder höher) aktualisieren möchten, können Sie nicht weiterhin H-Code verwenden.

**Was ist eine Übergangsphase und wie konfiguriere ich sie?**

Siehe [Übergangsphase beim Identity-Dienst](../reference/analytics-reference/grace-period.md) und wenden Sie sich an die [Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html).

**Warum muss ich zur Echtzeit-Datenerfassung (Real-time Data Collection, RDC) migrieren, um den Identity-Dienst zu verwenden?**

RDC bietet globale Leistungsvorteile und ist erforderlich, um sicherzustellen, dass Ihre Implementierung für künftige Funktionen bereit ist, die das globale Netzwerk der Edge-Notizen von Adobe nutzen. See [Analytics Requirements: Regional Data Collection (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## Berichterstellung {#section-123cd55a32e54a45a23beb140becfa8f}

**Was sind mögliche Ursachen für Diskrepanzen bei der Verwendung von Analytics mit dem Identity-Dienst?**

Häufige Ursachen für Diskrepanzen bei der Verwendung des Identity-Diensts:

* Weitere Verwendung des veralteten s_vi-Cookies. Dies führt zu Diskrepanzen bei der Datenerfassung.
* Dublette, die Besucher zählt, wenn sie von einer Umfrage zu einem Popup navigieren.

## Cookies  {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Was geschieht in Analytics, wenn der Identity-Dienst keinen AMCV-Cookie setzen kann?**

Es gibt drei potenzielle Szenarien, in denen dies die Analytics-Daten für neue Besucher beeinflusst:

1. Ein Endbenutzer verlässt eine Seite, bevor die AMCV-Cookies erfolgreich eingestellt wurden (innerhalb des 30-Sekunden-Timeout-Fensters).

   Wenn ein Besucher eine Seite verlässt, bevor der Ladevorgang abgeschlossen ist, wird der Analytics-Treffer nicht gesendet. Analytics erhält keine Daten aus diesem Szenario und würde davon ausgehen, dass die Daten bis zum frühen Schließen der Seite verloren gingen. Basierend auf unseren Tests, die auch abgelegene Regionen einschlossen, stellten wir fest, dass dieses Szenario durchschnittlich weniger als 1 % des Traffics ausmachte. Anzumerken ist, dass dieses Szenario zuweilen auch ohne den Identity-Dienst auftritt – es entsteht durch Einschluss des Analytics-Datenerfassungscodes unten auf der Seite.

1. Einem Endbenutzer wird kein Identity-Dienst oder keine Analytics-ID innerhalb des Zeitüberschreitungsintervalls von 30 Sekunden zugewiesen, da die Verbindung zu langsam ist oder das Ladesymbol im Browser „rotiert“.

   Weder der Identity-Dienst noch die Analytics-ID werden festgelegt und dem Besucher wird eine clientseitige ID zugewiesen. Während dies die Erfassung von Analytics-Daten ermöglicht, wird das Profil des Besuchers unterbrochen, wenn auf einer nachfolgenden Seite eine Analytics-ID festgelegt wird. Die clientseitige ID stimmt auch nicht mit einem vorhandenen Besucher-Profil überein, das in Audience Manager oder Analytics gespeichert ist. Diese clientseitige ID wird in Analytics auch als zwei verschiedene Besucher angezeigt, wenn zwei separate Domänen an dieselbe Report Suite gesendet werden.

1. Einem Endbenutzer wird innerhalb des Zeitüberschreitungsintervalls von 30 Sekunden statt einer ID des Identity-Diensts eine standardmäßige Analytics-Tracking-ID zugewiesen und die Übergangsphase wird nicht aktiviert.

   Szenario 3 führt zu dem gleichen Ergebnis wie Szenario 2, da eine clientseitige ID verwendet wird.

>[!TIP]
>
>Wenn Sie die neuesten Versionen von VisitorAPI.js und AppMeasurement.js mit den Standardeinstellungen verwenden, sollten Sie alle schwerwiegenden oder spürbaren Folgen der drei oben beschriebenen Szenarios vermeiden können.

>[!MORELIKETHIS]
>
>* [Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html)

