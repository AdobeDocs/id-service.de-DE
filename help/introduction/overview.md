---
description: Die Rolle des Experience Cloud Identity-Diensts in Adobe Experience Cloud.
seo-description: Mit dem Experience Cloud-Identity-Dienst (ehemals Besucher-ID-Dienst oder Marketing Cloud ID-Dienst) wird die Nutzung des allgemeinen Identifizierungs-Frameworks für die Experience Cloud-Dienste ermöglicht, wie z. B. Kundenattribute und Zielgruppen.
seo-title: Experience Cloud ID-Dienst – Übersicht
title: Experience Cloud ID-Dienst – Übersicht
translation-type: tm+mt
source-git-commit: 98b72f87b188debd6a5f6b86822c3f714647de61
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 80%

---


# Experience Cloud ID-Dienst – Übersicht

Mit dem [!UICONTROL Experience Cloud Identity-Dienst] wird die Nutzung des allgemeinen Identifizierungs-Frameworks für den Experience Cloud Core-Dienste (z. B. Kundenattribute und Zielgruppen) im Experience Platform Identity-Dienst ermöglicht.

>[!NOTE]
>
> Referenzen auf den ID-Dienst werden möglicherweise als Akronyme oder frühere Namen wie ECID, Marketing Cloud ID-Dienst (MID) und Besucher-ID-Dienst angezeigt. Diese beziehen sich auf den [!UICONTROL Experience Cloud Identity-Dienst]. Möglicherweise sehen Sie auch den Begriff [!UICONTROL Experience Platform Identity-Dienst]. Zur Klarstellung:

* [!UICONTROL Experience Platform Identity-Dienst]: Der Dienst, der Identitäten verknüpft. Es handelt sich dabei um den Dienst zum Verknüpfen von Geräten für das personenbasierte Erlebnis-Management.
* [!UICONTROL Experience Cloud ID-Dienst] (ECID): Die eindeutige, persistente ID, die einem Site-Besucher zugewiesen wird. Dies ist eine bestimmte Entität, die vom Platform Identity-Dienst verwendet werden kann.

Wenn Ihr Unternehmen den ID-Dienst implementiert, können Sie mit dieser ID denselben Site-Besucher und dessen Daten in unterschiedlichen Experience Cloud-Lösungen identifizieren.

![](assets/ecid-new.png)

Darüber hinaus kann der ID-Dienst die verschiedenen lösungsspezifischen IDs (z. B. Analytics-AID) ersetzen. And, through the [Customer IDs and Authentication States](/help/reference/authenticated-state.md) functionality, the ID service lets you pass in your own customer IDs to the Experience Cloud. Beachten Sie jedoch, dass der ID-Dienst nur mit den Lösungen funktioniert, die Sie bereits abonniert haben. Es bietet keinen Zugriff auf andere Produkte, wenn Sie nicht für sie angemeldet sind.

Künftig ist der ID-Dienst eine integrale Komponente von vielen aktuellen und künftigen Experience Cloud-Features, -Erweiterungen und -Services. Der ID-Dienst unterstützt derzeit [Analytics](http://www.adobe.com/de/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/de/marketing-cloud/data-management-platform.html) und [Target](http://www.adobe.com/de/marketing-cloud/testing-targeting.html). Zudem ist er erforderlich, wenn Sie sich an der Adobe Experience Cloud-Gerätekooperation beteiligen möchten. Wenn Sie den ID-Dienst nicht implementiert haben, ist es nun an der Zeit, eine Migrationsstrategie in Erwägung zu ziehen. Weitere Informationen über die Bedeutung und die Rolle des Identity-Dienstes finden Sie unter [Why the Experience Cloud ID Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/) (Warum Sie den ID-Dienst im Auge behalten sollten).

## Funktionszusammenfassung

Zusammenfassend ist der ID-Dienst:

* Erstellt einen gemeinsamen Schlüssel oder eine gemeinsame ID, die zum Verknüpfen von Profilen und Identitäten verwendet werden kann.
* Identifiziert ein Gerät eindeutig in mehreren Lösungen.
* Legt ein Erstanbieter-Cookie in der Domäne des Kunden fest, um sicherzustellen, dass die Verfolgung in derselben Domäne erfolgt. See the document on [cookies and Experience Cloud Identity Service](https://docs.adobe.com/content/help/de-DE/id-service/using/intro/cookies.html) for more information.
* Erhalten von Aliasen und ID-Zuordnungen von Experience Cloud-Kunden und -Partnern.
* Verwalten der ID-Synchronisierung innerhalb der Experience Cloud.
* Unterstützen der ID-Synchronisierung mit unterschiedlichen Drittanbietern im Anzeigentechnologiesystem.

## Anforderungen für den ID-Dienst

Ihre Lösung und andere Adobe-Codebibliotheken müssen diese [Anforderungen erfüllen](/help/reference/requirements.md), bevor Sie den ID-Dienst verwenden können.

* [Cookies und der Experience Cloud Identity-Dienst](cookies.md): Der ID-Dienst verwendet Ihre Organisations-ID, das Experience Cloud-AMCV-Cookie und ein demdex-Cookie, um eindeutige und beständige IDs für die Besucher Ihrer Site zu erstellen und zu speichern. Mit diesen Cookies kann der ID-Dienst Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen unterschiedlichen Experience Cloud-Lösungen ermöglichen.
* [Anfordern und Festlegen von IDs durch den Experience Cloud Identity-Dienst](id-request.md): Eine Übersicht über den ID-Anforderungs- und Antwortprozess. Diese Beispiele decken die ID-Zuweisung auf individuellen Sites, Site-übergreifend und für durch verschiedene Experience Cloud-Kunden verwaltete Sites mit eigenen Kunden-IDs ab.
* [Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten](match-rates.md): Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Experience Cloud Identity-Dienst, einschließlich Adobe Media Optimizer und ID-Dienst.
