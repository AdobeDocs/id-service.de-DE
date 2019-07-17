---
description: Die Rolle des Experience Cloud-Identitätsdienstes in der Adobe Experience Cloud.
seo-description: Der Experience Cloud-Identitätsdienst aktiviert das allgemeine Identifizierungsframework für die Experience Cloud Core Services, Lösungen und Kundenattribute und Zielgruppen im Core-Core-Service.
seo-title: ID-Dienst – Übersicht
title: Übersicht
uuid: null
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Übersicht

Der Experience Cloud-Identitätsdienst aktiviert das allgemeine Identifizierungsframework für die Experience Cloud Core Services, Lösungen und Kundenattribute und Zielgruppen im Core-Core-Service. Es funktioniert durch die Zuweisung einer eindeutigen, dauerhaften ID zu einem Sitebesucher. Wenn Ihre Organisation den ID-Dienst implementiert, können Sie mit dieser ID denselben Site-Besucher und seine Daten in unterschiedlichen Experience Cloud-Lösungen identifizieren.

![](assets/ecid.png)

Zudem kann der ID-Dienst die unterschiedlichen lösungsspezifischen IDs (z. B. Analytics AID) ersetzen. Mit der Funktionalität [Kunden-IDs und Authentifizierungsstatus](/help/reference/authenticated-state.md) ermöglicht es Ihnen der ID-Dienst, eigene Kunden-IDs an Experience Cloud zu übergeben. Beachten Sie jedoch, dass der ID-Dienst lediglich in den Lösungen verwendet werden kann, die Sie bereits abonniert haben. Er bietet keinen Zugriff auf weitere Produkte, wenn Sie diese noch nicht abonniert haben.

Künftig ist der ID-Dienst eine integrale Komponente von vielen aktuellen und künftigen Experience Cloud-Features, -Erweiterungen und -Services. Der ID-Dienst unterstützt derzeit [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) und [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). Zudem ist er erforderlich, wenn Sie sich an der Adobe Experience Cloud-Gerätekooperation beteiligen möchten. Wenn Sie den ID-Dienst nicht implementiert haben, ist es nun an der Zeit, eine Migrationsstrategie in Erwägung zu ziehen. For more information about the importance and role of the ID service, see [Why the Experience Cloud Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Funktionszusammenfassung

Kurz gesagt, ermöglicht der ID-Dienst Folgendes:

* Erstellen eines gemeinsamen Schlüssels oder einer ID, um Profile und Identitäten zu verknüpfen.
* Eindeutige Identifikation eines Geräts über mehrere Lösungen hinweg.
* Setzen eines Erstanbieter-Cookies in der Domäne eines Kunden zum Tracking in dieser Domäne. Weitere Informationen finden Sie unter Experience Cloud.
* Erhalten von Aliasen und ID-Zuordnungen von Experience Cloud-Kunden und -Partnern.
* Verwalten der ID-Synchronisierung innerhalb der Experience Cloud.
* Unterstützen der ID-Synchronisierung mit unterschiedlichen Drittanbietern im Anzeigentechnologiesystem.

## Anforderungen für den ID-Dienst

Ihre Lösung und andere Adobe-Codebibliotheken müssen diese [Anforderungen erfüllen](/help/reference/requirements.md), bevor Sie den ID-Dienst verwenden können.

* [Cookies und der Experience Cloud-Identitätsdienst](cookies.md): Der ID-Dienst verwendet Ihre Organisations-ID, das Experience Cloud AMCV-Cookie und ein demdex-Cookie, um eindeutige, beständige ids für Ihre Site-Besucher zu erstellen und zu speichern. Mit diesen Cookies kann der ID-Dienst Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen unterschiedlichen Experience Cloud-Lösungen ermöglichen.
* [Anfordern und Festlegen von IDs durch den Experience Cloud-Identitätsdienst](id-request.md): Eine Übersicht über den ID-Anforderungs- und Antwortprozess. Diese Beispiele decken die ID-Zuweisung auf individuellen Sites, Site-übergreifend und für durch verschiedene Experience Cloud-Kunden verwaltete Sites mit eigenen Kunden-IDs ab.
* [ID-Synchronisierung und Übereinstimmungsraten](match-rates.md): Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Experience Cloud-Identitätsdienst, einschließlich Adobe Media Optimizer und des ID-Diensts.