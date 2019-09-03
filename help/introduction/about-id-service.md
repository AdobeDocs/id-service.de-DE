---
description: Die Rolle des Experience Platform Identity-Diensts in Adobe Experience Cloud.
keywords: ID-Dienst
seo-description: Die Rolle des Experience Platform Identity-Diensts in Adobe Experience Cloud.
seo-title: Über den ID-Dienst
title: Übersicht
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: ht
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Über den ID-Dienst{#aboutidservice}

Die Rolle des Experience Cloud Identity-Diensts in Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## Der Experience Cloud Identity-Dienst: Ein Grundelement der Core Services {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Mit dem Experience Cloud Identity-Dienst wird das allgemeine Identifizierungs-Framework für die Experience Cloud-Core Services, Lösungen sowie benutzerdefinierte Attribute und Zielgruppen ermöglicht. Es funktioniert durch die Zuweisung einer eindeutigen, dauerhaften ID zu einem Sitebesucher. Wenn Ihre Organisation den ID-Dienst implementiert, können Sie mit dieser ID denselben Site-Besucher und seine Daten in unterschiedlichen Experience Cloud-Lösungen identifizieren.

![](assets/ecid.png)

Zudem kann der ID-Dienst die unterschiedlichen lösungsspezifischen IDs (z. B. Analytics AID) ersetzen. Mit der Funktionalität [Kunden-IDs und Authentifizierungsstatus](../reference/authenticated-state.md) ermöglicht es Ihnen der ID-Dienst, eigene Kunden-IDs an [!DNL Experience Cloud] zu übergeben. Beachten Sie jedoch, dass der ID-Dienst lediglich in den Lösungen verwendet werden kann, die Sie bereits abonniert haben. Er bietet keinen Zugriff auf weitere Produkte, wenn Sie diese noch nicht abonniert haben.

Künftig ist der ID-Dienst eine integrale Komponente von vielen aktuellen und künftigen [!DNL Experience Cloud]-Features, -Erweiterungen und -Services. Derzeit unterstützt der ID-Dienst [Analytics](http://www.adobe.com/de/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/de/marketing-cloud/data-management-platform.html) und [Target](http://www.adobe.com/de/marketing-cloud/testing-targeting.html). Zudem ist er erforderlich, wenn Sie sich an der [!DNL Adobe Experience Cloud]-Gerätekooperation beteiligen möchten. Wenn Sie den ID-Dienst nicht implementiert haben, ist es nun an der Zeit, eine Migrationsstrategie in Erwägung zu ziehen. Weitere Informationen über die Bedeutung und die Rolle des Identity-Dienstes finden Sie unter [Why the Experience Cloud ID Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Funktionszusammenfassung {#section-96555473455c4bf8924c2d56ff4f3255}

Kurz gesagt, ermöglicht der ID-Dienst Folgendes:

* Erstellen eines gemeinsamen Schlüssels oder einer ID, um Profile und Identitäten zu verknüpfen.
* Eindeutige Identifikation eines Geräts über mehrere Lösungen hinweg.
* Setzen eines Erstanbieter-Cookies in der Domäne eines Kunden zum Tracking in dieser Domäne. Weitere Informationen finden Sie unter [Experience Cloud](../introduction/cookies.md).
* Erhalten von Aliasen und ID-Zuordnungen von [!DNL Experience Cloud]-Kunden und -Partnern.
* Verwalten der ID-Synchronisierung innerhalb der [!DNL Experience Cloud].
* Unterstützen der ID-Synchronisierung mit unterschiedlichen Drittanbietern im Anzeigentechnologiesystem.
