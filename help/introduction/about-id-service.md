---
description: Die Rolle des Experience Cloud-Identitätsdienstes in der Adobe Experience Cloud.
keywords: ID-Dienst
seo-description: Die Rolle des Experience Cloud-Identitätsdienstes in der Adobe Experience Cloud.
seo-title: Über den ID-Dienst
title: Übersicht
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Über den ID-Dienst{#aboutidservice}

Die Rolle des Experience Cloud-Identitätsdienstes in der Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## The Experience Cloud Identity Service: A Foundational Element of Core Services {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Der Experience Cloud-Identitätsdienst aktiviert das allgemeine Identifizierungsframework für die Experience Cloud Core Services, Lösungen und Kundenattribute und Zielgruppen im Core-Core-Service. Es funktioniert durch die Zuweisung einer eindeutigen, dauerhaften ID zu einem Sitebesucher. Wenn Ihre Organisation den ID-Dienst implementiert, können Sie mit dieser ID denselben Site-Besucher und seine Daten in unterschiedlichen Experience Cloud-Lösungen identifizieren.

![](assets/ecid.png)

Zudem kann der ID-Dienst die unterschiedlichen lösungsspezifischen IDs (z. B. Analytics AID) ersetzen. Mit der Funktionalität [Kunden-IDs und Authentifizierungsstatus](../reference/authenticated-state.md) ermöglicht es Ihnen der ID-Dienst, eigene Kunden-IDs an [!DNL Experience Cloud] zu übergeben. Beachten Sie jedoch, dass der ID-Dienst lediglich in den Lösungen verwendet werden kann, die Sie bereits abonniert haben. Er bietet keinen Zugriff auf weitere Produkte, wenn Sie diese noch nicht abonniert haben.

Künftig ist der ID-Dienst eine integrale Komponente von vielen aktuellen und künftigen [!DNL Experience Cloud]-Features, -Erweiterungen und -Services. Der ID-Dienst unterstützt derzeit [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) und [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). Zudem ist er erforderlich, wenn Sie sich an der [!DNL Adobe Experience Cloud]-Gerätekooperation beteiligen möchten. Wenn Sie den ID-Dienst nicht implementiert haben, ist es nun an der Zeit, eine Migrationsstrategie in Erwägung zu ziehen. For more information about the importance and role of the ID service, see [Why the Experience Cloud Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Funktionszusammenfassung {#section-96555473455c4bf8924c2d56ff4f3255}

Kurz gesagt, ermöglicht der ID-Dienst Folgendes:

* Erstellen eines gemeinsamen Schlüssels oder einer ID, um Profile und Identitäten zu verknüpfen.
* Eindeutige Identifikation eines Geräts über mehrere Lösungen hinweg.
* Setzen eines Erstanbieter-Cookies in der Domäne eines Kunden zum Tracking in dieser Domäne. Weitere Informationen finden Sie unter [Experience Cloud](../introduction/cookies.md).
* Erhalten von Aliasen und ID-Zuordnungen von [!DNL Experience Cloud]-Kunden und -Partnern.
* Verwalten der ID-Synchronisierung innerhalb der [!DNL Experience Cloud].
* Unterstützen der ID-Synchronisierung mit unterschiedlichen Drittanbietern im Anzeigentechnologiesystem.
