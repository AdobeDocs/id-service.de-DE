---
description: Die Rolle des Experience Cloud ID-Diensts in Adobe Experience Cloud.
seo-description: Mit dem Experience Cloud ID-Dienst wird das allgemeine Identifizierungs-Framework für die Experience Cloud-Core Services, Lösungen sowie benutzerdefinierte Attribute und Zielgruppen im Personen-Core Service ermöglicht.
seo-title: ID-Dienst – Übersicht
title: Übersicht
uuid: null
translation-type: ht
source-git-commit: 1c6dc1871ee2e7b8d1f510576836519f7383b809

---


# Übersicht

Mit dem Experience Cloud ID-Dienst wird das allgemeine Identifizierungs-Framework für die Experience Cloud-Core Services, Lösungen sowie benutzerdefinierte Attribute und Zielgruppen im Personen-Core Service ermöglicht. Es funktioniert durch die Zuweisung einer eindeutigen, dauerhaften ID zu einem Sitebesucher. Wenn Ihre Organisation den ID-Dienst implementiert, können Sie mit dieser ID denselben Site-Besucher und seine Daten in unterschiedlichen Experience Cloud-Lösungen identifizieren.

![](assets/ecid.png)

Zudem kann der ID-Dienst die unterschiedlichen lösungsspezifischen IDs (z. B. Analytics AID) ersetzen. Mit der Funktionalität [Kunden-IDs und Authentifizierungsstatus](/help/mcvid-reference/mcvid-authenticated-state.md) ermöglicht es Ihnen der ID-Dienst, eigene Kunden-IDs an Experience Cloud zu übergeben. Beachten Sie jedoch, dass der ID-Dienst lediglich in den Lösungen verwendet werden kann, die Sie bereits abonniert haben. Er bietet keinen Zugriff auf weitere Produkte, wenn Sie diese noch nicht abonniert haben.

Künftig ist der ID-Dienst eine integrale Komponente von vielen aktuellen und künftigen Experience Cloud-Features, -Erweiterungen und -Services. Derzeit unterstützt der ID-Dienst [Analytics](http://www.adobe.com/de/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/de/marketing-cloud/data-management-platform.html) und [Target](http://www.adobe.com/de/marketing-cloud/testing-targeting.html). Zudem ist er erforderlich, wenn Sie sich an der Adobe Experience Cloud-Gerätekooperation beteiligen möchten. Wenn Sie den ID-Dienst nicht implementiert haben, ist es nun an der Zeit, eine Migrationsstrategie in Erwägung zu ziehen. Weitere Informationen über die Wichtigkeit und die Rolle des ID-Dienstes finden Sie unter [Why the Experience Cloud ID Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Funktionszusammenfassung

Kurz gesagt, ermöglicht der ID-Dienst Folgendes:

* Erstellen eines gemeinsamen Schlüssels oder einer ID, um Profile und Identitäten zu verknüpfen.
* Eindeutige Identifikation eines Geräts über mehrere Lösungen hinweg.
* Setzen eines Erstanbieter-Cookies in der Domäne eines Kunden zum Tracking in dieser Domäne. Siehe Experience Cloud.
* Erhalten von Aliasen und ID-Zuordnungen von Experience Cloud-Kunden und -Partnern.
* Verwalten der ID-Synchronisierung innerhalb der Experience Cloud.
* Unterstützen der ID-Synchronisierung mit unterschiedlichen Drittanbietern im Anzeigentechnologiesystem.

## Anforderungen für den ID-Dienst

Ihre Lösung und andere Adobe-Codebibliotheken müssen diese [Anforderungen erfüllen](/help/mcvid-reference/mcvid-requirements.md), bevor Sie den ID-Dienst verwenden können.

* [Cookies und der Experience Cloud ID-Dienst](mcvid-cookies.md): Der ID-Dienst verwendet Ihre Organisations-ID, das Experience Cloud-AMCV-Cookie und ein demdex-Cookie, um eindeutige und beständige IDs für die Besucher Ihrer Site zu erstellen und zu speichern. Mit diesen Cookies kann der ID-Dienst Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen unterschiedlichen Experience Cloud-Lösungen ermöglichen.
* [Anfordern und Festlegen von IDs durch den Experience Cloud ID-Dienst](mcvid-id-request.md): Eine Übersicht über den ID-Anforderungs- und Ausgabeprozess. Diese Beispiele decken die ID-Zuweisung auf individuellen Sites, Site-übergreifend und für durch verschiedene Experience Cloud-Kunden verwaltete Sites mit eigenen Kunden-IDs ab.
* [ID-Synchronisationen und Übereinstimmungsraten](mcvid-match-rates.md): Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Experience Cloud ID-Dienst, einschließlich Adobe Media Optimizer und des ID-Dienstes.