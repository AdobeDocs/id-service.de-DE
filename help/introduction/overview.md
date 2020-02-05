---
description: Die Rolle des Experience Cloud-Identitätsdienstes in der Adobe Experience Cloud.
seo-description: Der Experience Cloud-Identitätsdienst (ehemals Besucher-ID-Dienst oder Marketing Cloud ID-Dienst) ermöglicht das allgemeine Identifizierungsframework für die Experience Cloud-Dienste wie Kundenattribute und Zielgruppen.
seo-title: Übersicht über den Experience Cloud ID-Dienst
title: Übersicht über den Experience Cloud ID-Dienst
translation-type: tm+mt
source-git-commit: 9e020c3292a7c9f14ec77615a54ec61a37762eec

---


# Übersicht über den Experience Cloud ID-Dienst

The [!UICONTROL Experience Cloud Identity Service] enables the common identification framework for Experience Cloud Core Services (such as customer attributes and audiences) solutions in the Experience Platform Identity Service.

>[!NOTE]
>
> Möglicherweise werden Verweise auf frühere Namen oder Abkürzungen wie ECID, Marketing Cloud ID-Dienst (MID) und Besucher-ID-Dienst angezeigt. Diese beziehen sich auf den [!UICONTROL Experience Cloud-Identitätsdienst]. Möglicherweise sehen Sie auch den Identitätsdienst für [!UICONTROL Experience Platform]. Zur Klarstellung:

* [!UICONTROL Experience Platform Identity Service]: Der Dienst, der Identitäten verknüpft. Es handelt sich dabei um den Dienst zum Verknüpfen von Geräten für das personalbasierte Experience Management.
* [!UICONTROL Experience Cloud ID-Dienst] (ECID): Die eindeutige, beständige ID, die einem Site-Besucher zugewiesen ist. Es handelt sich um eine bestimmte Entität, die vom Platform Identity Service verwendet werden kann.

Wenn Ihre Organisation den ID-Dienst implementiert, können Sie mit dieser ID denselben Site-Besucher und seine Daten in unterschiedlichen Experience Cloud-Lösungen identifizieren.

![](assets/ecid.png)

Zudem kann der ID-Dienst die unterschiedlichen lösungsspezifischen IDs (z. B. Analytics AID) ersetzen. Mit der Funktionalität [Kunden-IDs und Authentifizierungsstatus](/help/reference/authenticated-state.md) ermöglicht es Ihnen der ID-Dienst, eigene Kunden-IDs an Experience Cloud zu übergeben. Beachten Sie jedoch, dass der ID-Dienst lediglich in den Lösungen verwendet werden kann, die Sie bereits abonniert haben. Er bietet keinen Zugriff auf weitere Produkte, wenn Sie diese noch nicht abonniert haben.

Künftig ist der ID-Dienst eine integrale Komponente von vielen aktuellen und künftigen Experience Cloud-Features, -Erweiterungen und -Services. Der ID-Dienst unterstützt derzeit [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) und [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). Zudem ist er erforderlich, wenn Sie sich an der Adobe Experience Cloud-Gerätekooperation beteiligen möchten. Wenn Sie den ID-Dienst nicht implementiert haben, ist es nun an der Zeit, eine Migrationsstrategie in Erwägung zu ziehen. Weitere Informationen über die Bedeutung und die Rolle des Identity-Dienstes finden Sie unter [Why the Experience Cloud ID Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

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

* [Cookies und der Experience Cloud Identity-Dienst](cookies.md): Der ID-Dienst verwendet Ihre Organisations-ID, das Experience Cloud-AMCV-Cookie und ein demdex-Cookie, um eindeutige und beständige IDs für die Besucher Ihrer Site zu erstellen und zu speichern. Mit diesen Cookies kann der ID-Dienst Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen unterschiedlichen Experience Cloud-Lösungen ermöglichen.


* [Anfordern und Festlegen von IDs durch den Experience Cloud Identity-Dienst](id-request.md): Eine Übersicht über den ID-Anforderungs- und Antwortprozess. Diese Beispiele decken die ID-Zuweisung auf individuellen Sites, Site-übergreifend und für durch verschiedene Experience Cloud-Kunden verwaltete Sites mit eigenen Kunden-IDs ab.
* [Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten](match-rates.md): Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Experience Cloud Identity-Dienst, einschließlich Adobe Media Optimizer und ID-Dienst.