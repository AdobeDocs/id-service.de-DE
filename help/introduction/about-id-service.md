---
description: Die Rolle des Experience Cloud Identity-Diensts in Adobe Experience Cloud.
keywords: ID Service
seo-description: Die Rolle des Experience Cloud Identity-Diensts in Adobe Experience Cloud.
seo-title: Über den ID-Dienst
title: Übersicht
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: tm+mt
source-git-commit: ec67177fc6491e4c8cea835d198574c9fdb4b01f
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 69%

---


# Über den ID-Dienst {#aboutidservice}

Die Rolle des Experience Cloud Identity-Diensts in Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## Der Experience Cloud Identity-Dienst: Ein Grundelement der Core Services {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Mit dem Experience Cloud Identity-Dienst wird das allgemeine Identifizierungs-Framework für die Experience Cloud-Core Services, Lösungen sowie benutzerdefinierte Attribute und Zielgruppen ermöglicht. Der ID-Dienst funktioniert durch die Zuweisung einer eindeutigen, dauerhaften ID zu einem Site-Besucher. Wenn Ihr Unternehmen den ID-Dienst implementiert, können Sie mit dieser ID denselben Site-Besucher und dessen Daten in unterschiedlichen Experience Cloud-Lösungen identifizieren.

![](assets/ecid-new.png)

Darüber hinaus kann der ID-Dienst die verschiedenen lösungsspezifischen IDs (z. B. Analytics-AID) ersetzen. And, through the [Customer IDs and Authentication States](../reference/authenticated-state.md) functionality, the ID service lets you pass in your own customer IDs to the [!DNL Experience Cloud]. Beachten Sie jedoch, dass der ID-Dienst nur mit den Lösungen funktioniert, die Sie bereits abonniert haben. Es bietet keinen Zugriff auf andere Produkte, wenn Sie nicht für sie angemeldet sind.

Künftig ist der ID-Dienst eine integrale Komponente von vielen aktuellen und künftigen [!DNL Experience Cloud]-Features, -Erweiterungen und -Services. Der ID-Dienst unterstützt derzeit [Analytics](http://www.adobe.com/de/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/de/marketing-cloud/data-management-platform.html) und [Target](http://www.adobe.com/de/marketing-cloud/testing-targeting.html). Zudem ist er erforderlich, wenn Sie sich an der [!DNL Adobe Experience Cloud]-Gerätekooperation beteiligen möchten. Wenn Sie den ID-Dienst nicht implementiert haben, ist es nun an der Zeit, eine Migrationsstrategie in Erwägung zu ziehen. Weitere Informationen über die Bedeutung und die Rolle des Identity-Dienstes finden Sie unter [Why the Experience Cloud ID Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/) (Warum Sie den ID-Dienst im Auge behalten sollten).

## Funktionszusammenfassung {#section-96555473455c4bf8924c2d56ff4f3255}

Zusammenfassend ist der ID-Dienst:

* Erstellt einen gemeinsamen Schlüssel oder eine gemeinsame ID, die zum Verknüpfen von Profilen und Identitäten verwendet werden kann.
* Identifiziert ein Gerät eindeutig in mehreren Lösungen.
* Legt ein Erstanbieter-Cookie in der Domäne des Kunden fest, um sicherzustellen, dass die Verfolgung in derselben Domäne erfolgt. Weitere Informationen finden Sie unter [Experience Cloud](../introduction/cookies.md).
* Erhalten von Aliasen und ID-Zuordnungen von [!DNL Experience Cloud]-Kunden und -Partnern.
* Verwalten der ID-Synchronisierung innerhalb der [!DNL Experience Cloud].
* Unterstützen der ID-Synchronisierung mit unterschiedlichen Drittanbietern im Anzeigentechnologiesystem.
