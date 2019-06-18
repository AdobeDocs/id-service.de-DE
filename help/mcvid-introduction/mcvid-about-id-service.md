---
description: Die Rolle des Experience Cloud ID-Diensts in Adobe Experience Cloud.
keywords: ID-Dienst
seo-description: Die Rolle des Experience Cloud ID-Diensts in Adobe Experience Cloud.
seo-title: Informationen zum ID-Dienst
title: 'Übersicht  '
uuid: c 52 d 6155-00 a 0-4 fc 5-9 d 8 e -5 ce 00 b 8 d 01 e 6
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Informationen zum ID-Dienst{#aboutidservice}

Die Rolle des Experience Cloud ID-Diensts in Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## Der Experience Cloud ID-Dienst: Ein Grundelement der Core Services {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Mit dem Experience Cloud ID-Dienst wird das allgemeine Identifizierungs-Framework für die Experience Cloud-Core Services, Lösungen sowie benutzerdefinierte Attribute und Zielgruppen im Personen-Core Service ermöglicht. Es funktioniert durch die Zuweisung einer eindeutigen, dauerhaften ID zu einem Sitebesucher. Wenn Ihre Organisation den ID-Dienst implementiert, können Sie mit dieser ID denselben Site-Besucher und seine Daten in unterschiedlichen Experience Cloud-Lösungen identifizieren.

![](assets/ecid.png)

Zudem kann der ID-Dienst die unterschiedlichen lösungsspezifischen IDs (z. B. Analytics AID) ersetzen. Mit der Funktionalität [Kunden-IDs und Authentifizierungsstatus](../mcvid-reference/mcvid-authenticated-state.md) ermöglicht es Ihnen der ID-Dienst, eigene Kunden-IDs an [!DNL Experience Cloud] zu übergeben. Beachten Sie jedoch, dass der ID-Dienst lediglich in den Lösungen verwendet werden kann, die Sie bereits abonniert haben. Er bietet keinen Zugriff auf weitere Produkte, wenn Sie diese noch nicht abonniert haben.

Künftig ist der ID-Dienst eine integrale Komponente von vielen aktuellen und künftigen [!DNL Experience Cloud]-Features, -Erweiterungen und -Services. Der ID-Dienst unterstützt derzeit [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) und [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). Zudem ist er erforderlich, wenn Sie sich an der [!DNL Adobe Experience Cloud]-Gerätekooperation beteiligen möchten. Wenn Sie den ID-Dienst nicht implementiert haben, ist es nun an der Zeit, eine Migrationsstrategie in Erwägung zu ziehen. Weitere Informationen über die Wichtigkeit und die Rolle des ID-Diensts finden Sie unter [Why the Experience Cloud ID Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Funktionszusammenfassung {#section-96555473455c4bf8924c2d56ff4f3255}

Kurz gesagt, ermöglicht der ID-Dienst Folgendes:

* Erstellen eines gemeinsamen Schlüssels oder einer ID, um Profile und Identitäten zu verknüpfen.
* Eindeutige Identifikation eines Geräts über mehrere Lösungen hinweg.
* Setzen eines Erstanbieter-Cookies in der Domäne eines Kunden zum Tracking in dieser Domäne. Siehe [Experience Cloud](../mcvid-introduction/mcvid-cookies.md).
* Erhalten von Aliasen und ID-Zuordnungen von [!DNL Experience Cloud]-Kunden und -Partnern.
* Verwaltet die ID-Synchronisierung innerhalb des [!DNL Experience Cloud].
* Unterstützen der ID-Synchronisierung mit unterschiedlichen Drittanbietern im Anzeigentechnologiesystem.